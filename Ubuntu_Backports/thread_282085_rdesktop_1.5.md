---
title: "rdesktop 1.5"
date: 2006-10-22
forum: Ubuntu Backports
---

### Post by ashrack on 2006-10-22
Since it wont be in EDGY will it make it to backports at least?

Here-s the changelog:
> Version 1.5.0 is a major step forward and includes many bug fixes as
 well as several new features. This includes:
 
   * SeamlessRDP - seamless windows support
   * Keymap fixes
   * Fix connection issues with Windows XP RTM
   * Keyboard handling improvements and fixes
   * SGI/Irix sound-driver fixes
   * Support for clipboard INCR protocol
   * Session Directory support (patch from Brian Chapeau <lheria@us...>)
   * Support for long filenames on redirected drives
   * XOR ellipse drawing fix
   * Clipboard unicode support (Ilya Konstantinov)
   * Fix display issues with exotic color depths (30bpp, 32bpp, etc) (Ilya Konstantinov)
   * Large file support
   * The default color depth is now the depth of the root window
   * Basic support for Windows Vista Beta 2
   * Fix high cpu-usage in OSS-driver

---

### Post by kosmic on 2006-10-22
Go to [www.getdeb.net](www.getdeb.net) i've made one package (.deb) of Rdesktop 1.5

---

### Post by ashrack on 2006-10-22
tanx but your DEB, it doesnt work. Here's the error:
```
Selecting previously deselected package rdesktop.
(Reading database ... 47009 files and directories currently installed.)
Unpacking rdesktop (from rdesktop_1.5.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of rdesktop:
 rdesktop depends on imake (>= 1); however:
  Package imake is not installed.
 rdesktop depends on linux-kernel-headers (>= 2.6.11.2-0ubuntu18); however:
  Package linux-kernel-headers is not installed.
dpkg: error processing rdesktop (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rdesktop

```

---

### Post by ashrack on 2006-10-23
just compiled my own RDESKTOP 1.5 and this one did install. Perhaps U should replace your DEB with mine.

[ATTACH]18030[/ATTACH]

---

### Post by Avian00 on 2006-11-14
> **ashrack said:**
> just compiled my own RDESKTOP 1.5 and this one did install. Perhaps U should replace your DEB with mine.

[ATTACH]18030[/ATTACH]

Thanks!  That .deb worked great and solved my problem!

---

### Post by patpicos on 2006-11-20
that 1.5 deb worked perfect for me. Thanks

I was going nuts with the lame refresh rate in 1.4!!

---

### Post by christianskov on 2006-11-21
I first meet the problem when updating to 6.10 Edgy. rdesktop 1.5 solved the problem with refresh. Thx a lot.

---

### Post by kosmic on 2006-11-21
Ups, sorry i've made a mistake in my deb, I will submit your deb to getdeb.net, if you give me permission of course.

---

