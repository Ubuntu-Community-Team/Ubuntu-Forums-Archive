---
title: "32 or 64 bits Kernel?"
date: 2013-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by cnplane on 2013-05-16
Four commands on my pc:

$ dpkg -l |grep linux-image
Linux kernel image for version 3.4.0 on [COLOR=#ff0000]**32 bit x86 **[/COLOR]SMP

[COLOR=#0000cd]It means my Ubuntu kernel is 32 bits?[/COLOR]


$ uname -a
Linux ny 3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 [COLOR=#ff0000]**x86_64 x86_64 x86_64**[/COLOR] GNU/Linux

$ file /bin/ls
/bin/ls: ELF 64-bit LSB executable, [COLOR=#ff0000]**x86-64**[/COLOR], version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x37cdd635587f519989044055623abff939002027, stripped

$ file /sbin/init
/sbin/init: ELF 64-bit LSB shared object, **[COLOR=#ff0000]x86-64[/COLOR]**, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x7aa29ded613e503fb09fb75d94026f3256f01e7a, stripped

[COLOR=#0000cd]up 3 commands mean my kernel is 64 bits?

My question:  What is my kernel, 32 bits or 64 bits? Thanks.
   [/COLOR]

---

