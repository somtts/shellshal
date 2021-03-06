# shellshal
Shell Script for Arabic Language processing
سكريبتات سطر الأوامر للتعامل مع النصوص العربية

#Description
This project is a collection of small shell scripts used to process arabic texts, like:

- Tokeninze a file text into tokens
- Strip Tashkeel from text
- Strip only the last mark from every word in text.


#التسمية
شَلْشَلَ
    [ ش ل ش ل ]. ( فعل : رباعي لازم متعد ). :- شَلْشَلْتُ ، أُشَلْشِلُ ، شَلْشِلْ ، مصدر شَلْشَلَةٌ .
    1 . :- شَلْشَلَ الْمَاءَ :- : صَبَّهُ مُتَتَابِعاً .
    2 . :- شَلْشَلَ الْمَاءُ :- : قَطَرَ وَسَالَ مُتَتَابِعاً .
    3 . :- شَلْشَلَ السَّيْفُ الدَّمَ :- : صَبَّهُ .
    
الاسم مأخوذ من شبهه بكلمة shell التي تعني سطر الأوامر، 

والمعنى في الشلشلة هي التتابع

##SCRIPTS

### Tokenize
1- You can tokenize a text file by the following script.
```
tokenize.sh filename
```
#### source
```shell
tr -s '[*!"#\$%&\(\)\+,\\\.\/:;،؛<=>\?@\[\\\\]^_`\{|\}~][:space:]]' '\n' < $1 
```

2- Tokenize, sort, removre duplicates and count frequencies for words in file. The result file is filename.unq.
```
tokenize_uniq.sh filename
```
#### source
```shell
tr -s '[*!"#\$%&\(\)\+,\\\.\/:;،؛<=>\?@\[\\\\]^_`\{|\}~][:space:]]' '\n' < $1 | sort | uniq -c | sort -nr >$1.unq
```

### Tashkeel
1- Remove Harakat (diacritics) and Tatweel from text
```
strip_tashkeel.sh filename
```
#### source
```shell
CHARS=$(python -c 'print u"\u064b\u064c\u064d\u064e\u064f\u0651\u0652".encode("utf8")')
sed 's/['"$CHARS"']//g' < $1
```

2- Remove last Haraka (diacritic) from the end of words from text
```
Strip_lastmark.sh filename
```
#### source
```shell
CHARS=$(python -c 'print u"\u064b\u064c\u064d\u064e\u064f\u0651\u0652".encode("utf8")')
sed 's/['"$CHARS"']$//g' < $1
```
