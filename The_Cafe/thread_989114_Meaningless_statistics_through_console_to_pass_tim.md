---
title: "Meaningless statistics through console to pass time"
date: 2008-11-21
forum: The Cafe
---

### Post by Trail on 2008-11-21
Well I was bored. I'll just leave those here. Of course, no harm done to your system. I can analyse how they work if you wish.

```


#measure disk usage of subdirectories
ls -A -U -Q -1 | xargs du -s -x | sort -g | tail -n 15

#measure most common file extension of subdirectories
find . | rev | cut -d / -s -f1 | cut -d . -s -f1 | rev |  sort |uniq -c | sort -g -r | head -n 15

#measure most common file type (as returned from `file') of subdirectories
#warning: will most likely be very slow
find . -exec file {} \; | rev | cut -d : -f1 | rev | sort | uniq -c | sort -g -r | head -n 15


```

---

### Post by Trail on 2008-11-21
Ah, and some examples:

```

340     .fontconfig
404     .cache
408     .vlc
468     .gimp-2.4
672     .gstreamer-0.10
1164    .xsession-errors
2892    Wallpapers
3880    .wine
3940    Desktop
5108    tomcat5.5
8712    .ooo-2.0
31236   .svnqt
46136   oots
53604   jakarta-jmeter-2.3.2
74248   .kde
96656   random mp3
146700  .mozilla
235808  .local
328080  .kde4
555796  .eclipse

```


```

   4009 mood (amarok's moodbar)
   1969 html
   1855 gif
   1106 jar
    833 png
    791 xml
    762 class
    522 properties
    388 jsp
    348 zip

```

```

   4782  data
   3231  directory
   2210  HTML document text
   1071  XML
   1070  GIF image data, version 89a, 16 x 16
    774  ASCII text
    765  Zip archive data, at least v1.0 to extract
    676  Zip archive data, at least v2.0 to extract
    652  ASCII Pascal program text
    466  smtp mail text
    345  ASCII text, with CRLF line terminators
    318  ASCII English text
    294  XML  document text
    201  JPEG image data, JFIF standard 1.01
    177  JPEG image data, JFIF standard 1.02

```

---

### Post by chucky chuckaluck on 2008-11-21
_my gold medalists_

princess
png
Audio file with ID3 version 2.3, MP3 encoding

---

### Post by Vadi on 2008-11-21
```
vadi@ubuntu:~$ ls -A -U -Q -1 | xargs du -s -x | sort -g | tail -n 15
40492	.dropbox-dist
57116	.savage2
59744	.purple
79144	Pictures
105456	.mozilla
231848	Documents
300832	.secondlife
550160	.phoronix-test-suite
578404	Dropbox
1239196	Music
1465032	Desktop
3255688	Programs
3853404	Systems
6432056	Games
16587092	.VirtualBox

vadi@ubuntu:~$ find . | rev | cut -d / -s -f1 | cut -d . -s -f1 | rev |  sort |uniq -c | sort -g -r | head -n 15

   9473 html
   8300 svn-base
   7143 h
   4088 png
   4064 c
   2216 cpp
   1982 jpg
   1875 o
   1697 gif
   1292 as
   1104 js
    947 mesh
    890 php
    775 txt
    660 xml

vadi@ubuntu:~$ find . -exec file {} \; | rev | cut -d : -f1 | rev | sort | uniq -c | sort -g -r | head -n 15
  10076  directory
   9115  data
   9068  ASCII C program text
   9051  HTML document text
   8541  ASCII text
   3141  ASCII C++ program text
   3065  ASCII English text
   1670  ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped
   1538  XML
   1518  ASCII C program text, with CRLF line terminators
   1069  ISO-8859 C program text
    967  JPEG image data, JFIF standard 1.01
    919  ASCII Java program text, with CRLF line terminators
    916  JPEG image data, JFIF standard 1.02
    839  PHP script text


```

---

### Post by Bruce M. on 2008-11-21
And the winners are:

```
bruloo@bruloo:~$ ls -A -U -Q -1 | xargs du -s -x | sort -g | tail -n 15
13404	Desktop
22440	Conky-Old
28600	Liloo Saved
31628	.icons
35976	WRSSCC
50196	T|E2
50232	SD-Cards
73808	Images
75036	.mozilla
77464	Documents
80784	.wine
90388	Atlas
116540	Wallpapers
148656	Websites
301048	.mozilla-thunderbird
bruloo@bruloo:~$ find . | rev | cut -d / -s -f1 | cut -d . -s -f1 | rev |  sort |uniq -c | sort -g -r | head -n 15
   2575 jpg
   1466 png
   1214 gif
   1065 html
    608 txt
    370 js
    236 htm
    128 xpt
    123 dll
    114 thb
    114 swf
    110 xml
    105 msf
     92 css
     86 dat
bruloo@bruloo:~$ find . -exec file {} \; | rev | cut -d : -f1 | rev | sort | uniq -c | sort -g -r | head -n 15
   2118  JPEG image data, JFIF standard 1.01
   1328  HTML document text
   1234  directory
    594  ASCII text
    588  X11 cursor
    460  JPEG image data, JFIF standard 1.02
    306  data
    286  ASCII English text
    192  PNG image data, 93 x 93, 8-bit/color RGBA, non-interlaced
    156  ASCII C++ program text
    149  PNG image data, 128 x 128, 8-bit/color RGBA, non-interlaced
    147  PNG image data, 61 x 61, 8-bit/color RGBA, non-interlaced
    144  PNG image data, 31 x 31, 8-bit/color RGBA, non-interlaced
    140  XML
    131  ASCII English text, with very long lines, with CRLF line terminators
bruloo@bruloo:~$ 

```
NOTE: I have no idea what all that stuff it.  :)
Have a nice day.
Bruce

---

