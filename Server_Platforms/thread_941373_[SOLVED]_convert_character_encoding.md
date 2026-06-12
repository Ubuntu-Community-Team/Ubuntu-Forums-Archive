---
title: "[SOLVED] convert character encoding"
date: 2008-10-08
forum: Server Platforms
---

### Post by dmizer on 2008-10-08
I have a bunch of php files which contain some Japanese characters. They render correctly on my website, but in the text files they look like this: &# 31119;&# 23713; (no spaces)

I need the files to contain the actual Japaense kanji characters so I can export into a mysql database.

I tried iconv like so:
```
iconv -f iso-8859-1 -t utf-8 <album.dat> album.conv
```

But this did nothing.

How do it get this: &# 31119;&# 23713; (no spaces) to look like this: &#31119;&#23713; without going through thousands of lines and manually replacing it?

```
$locale -a
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ja_JP.utf8
```

---

### Post by dmizer on 2008-10-09
Bump for help.

I've found that the encoding for the .dat files is ascii:
```
$ file -bi album.dat
text/plain; charset=us-ascii
```

But attempting to encode to UTF-8 fails with both iconv and recode:
```
iconv -f ascii -t utf-8 <album.dat> album.conv&&file -bi album.dat
text/plain; charset=us-ascii
```
```
$ recode UTF-8 album.dat&&file -bi album.dat
text/plain; charset=us-ascii
```

I've followed the directions here: [http://dev.mysql.com/doc/refman/5.0/en/charset-conversion.html](http://dev.mysql.com/doc/refman/5.0/en/charset-conversion.html) in an attempt to convert the text after I've imported it into the database, but still zero luck.

I'm dyin' over here ... someone throw me a bone :)

---

### Post by tacutu on 2008-10-09
this seems to do the trick:
```
ascii2uni -a D  <oldfile> newfile
```
ascii2uni is provided by the uni2ascii package (in the repos).

---

### Post by dmizer on 2008-10-09
Humm, that didn't seem to work quite right:
```
$ ascii2uni -a D <album.dat> album-uni.dat
2 tokens converted
$ file -bi album-uni.dat
text/plain; charset=utf-8
```

But the kanji turns into [mojibake](http://en.wikipedia.org/wiki/Mojibake).

Specifically this: &#36950;&#19998;&#65394;&#65377;&#12288;(which is gibberish)
instead of this: &#31119;&#23713; (which is how it should look)

---

### Post by tacutu on 2008-10-09
This is weird. I tested it and it works here. No mojibake.

---

### Post by tacutu on 2008-10-09
I tried opening a simple file containing "&#31119;&#23713;" in firefox and set the encoding to Shift-jis. Guess what I got? &#36950;&#19998;&#65394;&#65377;

So it is not the conversion that didn't work, but the encoding with which you tried to open the file. Try setting the encoding to UTF-8 and it should display fine.

Hope this helps.

---

### Post by dmizer on 2008-10-10
You were quite right. Where I work, it's no wonder there's an entire department devoted to these problems.

Unfortunately, I still have a problem. Even though the file has been converted to utf-8, the mysql database shows the file as utf-8, and the metadata on my page is causing my browser to display the page in utf-8, I still am not seeing these characters.

Something is getting dropped in the upload to the mysql database. I'm moving this to the servers forum because this seems to be related to a db server issue.

Thanks for your help tacutu.

---

### Post by tacutu on 2008-10-10
Glad to be of assistance.

> **dmizer said:**
> You were quite right. Where I work, it's no wonder there's an entire department devoted to these problems.


That's why I always said Japan shoud drop EUC, JIS and Shift-JIS and move to Unicode. Things would become so simple!

---

### Post by jure1873 on 2008-10-11
> **dmizer said:**
> 
I tried iconv like so:
```
iconv -f iso-8859-1 -t utf-8 <album.dat> album.conv
```

How do it get this: &# 31119;&# 23713; (no spaces) to look like this: &#31119;&#23713; without going through thousands of lines and manually replacing it?



&# 31119; is the html notation so iconv won't convert it. 
You'd first need to pass the files trough some kind of function to decode the html entities into normal characters and then use iconv on that file.

in php the function is [html-entity-decode]("http://php.net/manual/en/function.html-entity-decode.php") but I don't know if there is a program that would do that.

---

### Post by dmizer on 2008-10-13
You seem to have hit the mark jure1873.

If I look at the field in mysql, the &# 31119; is correct but when I look at the page source, the ampersand is changed to xhtml &amp, so something in the gallery2 source is altering the mysql output by calling on the html_entity_decode.

It really looks like the only way around this is for me to manually edit some 700 entries :(

Unless someone has a better idea?

Edit:
I finally broke down and simply hand edited everything :(

---

### Post by radosiu on 2009-10-24
well I hope you used find and replace method...

best regards...
chopin

---

