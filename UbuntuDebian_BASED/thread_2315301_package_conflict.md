---
title: "package conflict"
date: 2016-02-27
forum: Ubuntu/Debian BASED
---

### Post by Ron_H on 2016-02-27
Hello people
Hope you help
I was installing gpsdrive and his dependecie libmapnik0.7 which asked me to install libjpeg62 but when i tried
apt-get install libjpeg62

it says
libjpeg62-turbo : Conflicts: libjpeg62

and my dpkg --list | grep libjpeg says
ii  libjpeg-dev                            1:1.3.1-12                           all          Development files for the JPEG library [dummy package]
ii  libjpeg-turbo-progs                    1:1.3.1-12                           i386         Programs for manipulating JPEG files
ii  libjpeg62-turbo:i386                   1:1.3.1-12                           i386         libjpeg-turbo JPEG runtime library
ii  libjpeg62-turbo-dev:i386               1:1.3.1-12                           i386         Development files for the libjpeg-turbo JPEG library

feel really confused now

---

### Post by Bashing-om on 2016-02-27
Ron_H; Hello ...

Pops to mind ... where did you get " libjpeg62-turbo " from ..

please post the output - Between code tags ! - of terminal command:
```

apt-cache show libjpeg62-turbo

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

and we see where this leads us to.

[INDENT][INDENT]3rd party PPA is not a 'buntu specific problem.
[/INDENT][/INDENT]

---

### Post by Ron_H on 2016-02-27
Hi Bashing-om
Thanks for attention

this is the oputput
of the command

```
Package: libjpeg62-turbo
Source: libjpeg-turbo
Version: 1:1.3.1-12
Installed-Size: 368
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Replaces: libjpeg62
Provides: libjpeg62
Depends: libc6 (>= 2.7)
Conflicts: libjpeg62
Size: 122868
SHA256: 5d7d8aa7c44316065667f0ca96ef11ffa1f7528ac1d8e6ed2a8a66a6a8089334
SHA1: 7a72fd2a2c7c68a7da4022db69559ff0d60bb086
MD5sum: 14d5ec9b01c04345110f937fa283b30d
Description: libjpeg-turbo JPEG runtime library
 The libjpeg-turbo JPEG library is a library for handling JPEG files.
 .
 libjpeg-turbo is a JPEG image codec that uses SIMD instructions (MMX,
 SSE2, NEON) to accelerate baseline JPEG compression and decompression
 on x86, x86-64, and ARM systems.  The libjpeg-turbo JPEG library is
 an API/ABI compatible with the IJG JPEG library.
 .
 This package contains the shared runtime library.
Description-md5: 08e0ce6ce076575f3375631f6f960ebe
Multi-Arch: same
Homepage: http://www.libjpeg-turbo.org/
Section: libs
Priority: optional
Filename: pool/main/libj/libjpeg-turbo/libjpeg62-turbo_1.3.1-12_i386.deb


```

hope you can help
i need to install libjpeg62 or somehow fix the dependecies for the packages that require it as installed

---

### Post by sandyd on 2016-02-27
> **Ron_H said:**
> Hello people
Hope you help
I was installing gpsdrive and his dependecie libmapnik0.7 which asked me to install libjpeg62 but when i tried
apt-get install libjpeg62

it says
libjpeg62-turbo : Conflicts: libjpeg62

and my dpkg --list | grep libjpeg says
ii  libjpeg-dev                            1:1.3.1-12                           all          Development files for the JPEG library [dummy package]
ii  libjpeg-turbo-progs                    1:1.3.1-12                           i386         Programs for manipulating JPEG files
ii  libjpeg62-turbo:i386                   1:1.3.1-12                           i386         libjpeg-turbo JPEG runtime library
ii  libjpeg62-turbo-dev:i386               1:1.3.1-12                           i386         Development files for the libjpeg-turbo JPEG library

feel really confused now

Hi, how are you installing GPSDrive?

Are you installing it from their site, from Ubuntu's repository, or somewhere else?

Thanks,

---

### Post by Bashing-om on 2016-02-28
Ron_H; Morning ...

See sandyd's last .. in addition to that good to know information
Show us also:
```

apt-cache policy libjpeg62-turbo

```
as we know :
> 
Package: libjpeg62-turbo >> Conflicts: libjpeg62


and something somewhere has got to give.

3rd party ?
[INDENT][INDENT][INDENT]not 'buntu's fault
[/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2016-02-28
Ubuntu switched naming  to libjpeg-turbo8 a long time ago, reasons not remembered. 
(Debian still uses the libjpeg-turbo62 name

---

### Post by Ron_H on 2016-02-29
I forgot to mention im using kali sana os. It is based on debian wheezy and probably this situation can be recreated in ubuntu because i read many people had this sort of problem. Im posting on this forum because of the great community wich is surely able to solve solve this. Hope you can understand.

I tried installing gpsdrive from official site which gives problems so i added deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) squeeze main

To my file sources.list and it is probably not the problem since everything looks weel except the package conflict. My dependecies are fixes and system updated. Maybe it was not the best source but still fine.

From there i was able to install gpsdrive but it asked me some other packets so now i am installing libmapnik which says the following packages have unmep dependecies:

libgdal1-6.0 : Depends: libjpeg62 (>=6b1)
libmapnik0.7 : Depends: libjpeg62 (>=6b1)
libticf : Depends: libjpeg62 (>=6b1)

Try apt-get -f install

When i type apt-cache policy libjpeg62-turbo i got this message

Libjpeg62-turbo
Installed: 1:1.3.1-12
Candidate: 1:1.3.1-12
Version table:
*** 1:1.3-12 0
500 [http://http.kali.org/kali/](http://http.kali.org/kali/) sana/main i386 Packages
100 /var/lib/dpkg/status

And thanks

---

### Post by howefield on 2016-02-29
Thread moved accordingly.

---

### Post by Bashing-om on 2016-03-01
Ron_H; Welp ....

There is not a lot we can do :
> 
sysop@1404mini:~$ apt-cache show Libjpeg62-turbo
N: Unable to locate package Libjpeg62-turbo
E: No packages found
sysop@1404mini:~$

If you must have that 3rd party software installed... all I can suggest at this point is to open a dialog with the author(s) of Libjpeg62-turbo . Have them fix their packaging for the release you are running.
It is my concern that if we fix this, with the later version packaging installed, will break other things.

[INDENT][INDENT]cure worse than the bite
[/INDENT][/INDENT]

---

### Post by Ron_H on 2016-03-01
Did you try to do apt-get install libjpeg62-turbo and then libjpeg62 to try to see if you got same error? Its not hard to try hope you teel me what you get. Thanks for the support.

---

