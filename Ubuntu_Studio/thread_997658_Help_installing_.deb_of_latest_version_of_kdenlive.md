---
title: "Help installing .deb of latest version of kdenlive"
date: 2008-11-30
forum: Ubuntu Studio
---

### Post by ExquisiteDeadGuy on 2008-11-30
Hey everyone,

I'd like to install the newest version of kdenlive on Ubuntu 8.10. I downloaded the .deb from the kdenlive site, but when I run dpkg -i on it, I get these errors:

```
Selecting previously deselected package kdenlive.
(Reading database ... 165428 files and directories currently installed.)
Unpacking kdenlive (from kdenlive_0.7-0.0_amd64.deb) ...
dpkg: dependency problems prevent configuration of kdenlive:
 kdenlive depends on libavcodec51 (>= 3:20080706); however:
  Version of libavcodec51 on system is 3:0.svn20080206-12ubuntu3.
 kdenlive depends on libavformat52 (>= 3:20080706); however:
  Version of libavformat52 on system is 3:0.svn20080206-12ubuntu3.
 kdenlive depends on libmlt++1 (>= 1:0.3.2); however:
  Package libmlt++1 is not installed.
 kdenlive depends on libmlt1 (>= 1:0.3.2); however:
  Package libmlt1 is not installed.
 kdenlive depends on mlt; however:
  Package mlt is not installed.
dpkg: error processing kdenlive (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdenlive

```

Except the mlt which I can't find (libmlt is installed) all those packages are installed, I'm assuming they're just the wrong versions. Is there any way to make this install without totally messing up my apt?

Thanks!

---

### Post by cotcot on 2008-11-30
You need MLT 3.0. I think the best is to try to compile ffmpeg (for the libavcodec issue), mlt, mlt++ and kdenlive according to the instructions of the kdenlive wiki. Read carefully the reporting from the ./configure instruction. I could install the 0.7 beta version on my amd64 box, but failed to install the latest 0.7 release on my i386 box with a compilation error on libavcodec.

---

### Post by cignale on 2008-12-14
i've made some deb packages for Intrepid:

look at my blog post:

[http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/](http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/)

---

