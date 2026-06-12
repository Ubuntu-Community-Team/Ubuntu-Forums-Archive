---
title: "Swedish Charset on LAMP"
date: 2006-04-04
forum: Server Platforms
---

### Post by iluminate on 2006-04-04
Hello everyone,

I have a problem getting the swedish letters to display correctly on my website.
In php I have defined setlocale (LC_ALL, array ('sv_SE', 'swedish'));
And the swedish letter show up correctly! (static text)
BUT when data is displayed from MysqlDB (latin1_swedish) on the website  the swedish letters are scrambled. (they look good if you check em in phpmyadmin eg.)

So my question is, how the #"¤%#"# can I display the swedish letters correctly from the DB ?

I tried to play around with apache2.conf and unmarked the line:
#AddDefaultCharset	ISO-8859-1
After this the letter in the DB show up correctly, but everything else (that worked before) is scrambled.

My apache2.conf looks like this:
```
AddLanguage da .dk
AddLanguage nl .nl
AddLanguage en .en
AddLanguage et .et
AddLanguage fr .fr
AddLanguage de .de
AddLanguage el .el
AddLanguage it .it
AddLanguage ja .ja
AddLanguage pl .po
AddLanguage ko .ko
AddLanguage pt .pt
AddLanguage no .no
AddLanguage pt-br .pt-br
AddLanguage ltz .ltz
AddLanguage ca .ca
AddLanguage es .es
AddLanguage sv .se
AddLanguage cz .cz
AddLanguage ru .ru
AddLanguage tw .tw
AddLanguage zh-tw .tw

LanguagePriority sv en da nl et fr de el it ja ko no pl pt pt-br ltz ca es tw


#AddDefaultCharset	ISO-8859-1

AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
AddCharset ISO-8859-5  .iso8859-5  .latin5 .cyr .iso-ru
AddCharset ISO-8859-6  .iso8859-6  .latin6 .arb
AddCharset ISO-8859-7  .iso8859-7  .latin7 .grk
AddCharset ISO-8859-8  .iso8859-8  .latin8 .heb	
AddCharset ISO-8859-9  .iso8859-9  .latin9 .trk
AddCharset ISO-2022-JP .iso2022-jp .jis
AddCharset ISO-2022-KR .iso2022-kr .kis
AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5
# For russian, more than one charset is used (depends on client, mostly):
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
AddCharset KOI8-r      .koi8-r .koi8-ru
AddCharset KOI8-ru     .koi8-uk .ua
AddCharset ISO-10646-UCS-2 .ucs2
AddCharset ISO-10646-UCS-4 .ucs4
#AddCharset UTF-8       .utf8

AddCharset GB2312      .gb2312 .gb 
AddCharset utf-7       .utf7
AddCharset utf-8       .utf8
AddCharset big5	       .big5 .b5
AddCharset EUC-TW      .euc-tw	
AddCharset EUC-JP      .euc-jp
AddCharset EUC-KR      .euc-kr
AddCharset shift_jis   .sjis

```

So is something missing here?

Did also locale -a and the output is :
```
C
de_CH
de_CH.iso88591
de_DE
de_DE.iso88591
deutsch
en_CA.utf8
en_DK
en_DK.iso88591
en_GB
en_GB.iso88591
fi_FI@euro
fi_FI.iso885915@euro
german
POSIX
swedish
sv_SE
sv_SE.iso88591

```

Any help would be very much appreicated.
There must be alot of Swedish, Finish and German users with the same problem?
Or is it just me?:-?

---

### Post by LordHunter317 on 2006-04-04
None of that is the issue nor should you have played with any of it.  Likely you need to do two things:
Make sure you transmit the correct character set to the client, either by sender the appropriate header or using meta http-equiv tags.
Explictly set the enconding you're using to talk to MySQL.

---

### Post by coolvik on 2006-04-06
Hej,

if you visit a web page with a browser and check the info from Show -> Encoding (Firefox)

Thats mostly a hint on what the http header from the webserver is sent like.

Another way is to install the web developer plug-in to  Firefox and check the header from Information -> View response headers

---

### Post by iluminate on 2006-04-06
Tjena CoolVik,

I get Content-Type: text/html; charset=UTF-8 which is obviously wrong.
Hmmm....it should be iso8859-1 right?

Peace!

---

### Post by coolvik on 2006-04-06
Tja,

it depends on how the content is saved. In this case you seems to save the data in ISO-8859-1 format. So somewhere in the process when the data is being presented thrue the webserver the output stream gets the wrong header.

I would try to look more into the Apache2 settings, or maybe PHP if you run that.

---

