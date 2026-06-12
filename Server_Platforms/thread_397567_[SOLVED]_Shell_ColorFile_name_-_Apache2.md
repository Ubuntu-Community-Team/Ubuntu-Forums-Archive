---
title: "[SOLVED] Shell Color/File name - Apache2"
date: 2007-03-30
forum: Server Platforms
---

### Post by victorbrca on 2007-03-30
Hi all,


  I just spent the last day migrating my web-ftp Windows server to Ubuntu. It was rather fun...

  I faced a problem wich took me while to resolve (ddn't however figure it out). One of my files would not open on any browser, however it was still listed on my www folder.

  I noticed that the color of the file name was normal (white), while the other files had a pink color on my terminal. Them I also noticed that the extension was capital "JPG". Once I changed it to lower case it became pink and it started working.

  Now I have other files with capital extension which have no problem being displayed on a web browser. 

  Can any one gimme the light? I bet is prob something really simple...


[IMG]http://wazem.dyndns.org/temp/pink.png[/IMG]


Thanks,


Vic

---

### Post by Mr. C. on 2007-03-31
The colors presented by ls are defined by default in a database, which can be seen by running:

dircolors --print-database

This will show you a series of ANSI color codes.  The colors are coded as numbers:

```
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white
```

There are also attribute codes (blink, normal, underline):
```
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
```

```
and below that, you can see jpg files are:

.jpg 01;35
.jpeg 01;35
```

This means, jpg and jpeg files are bold (01), magenta (35), and what do you know... that's the color of your jpg's.  So your question is, why were the .JPG files white?  Because white is the default color for unrecognized files, and .jpg is different than .JPG in Unix/Linux file systems (case sensitive).

Which other files have no trouble with case sensitivity ?

MrC

---

### Post by victorbrca on 2007-03-31
Thanks for the reply MrC...

  I totally forgot the case sensitivity in UNX. Did not put 2 and 2 together that it would also b aplicable to the extension....  :redface:

  The 2 files that work are the ones on the screenshot on my first post. You can see that there's a 1.JPG and 2.JPG. These two files still open with no problem...

  So I guess this could be somewhat of a pain for some web developers using digital cameras as they would have to be extra careful... I would think the manufactures would avoid using upper case for the default file extension...


Vic.

---

