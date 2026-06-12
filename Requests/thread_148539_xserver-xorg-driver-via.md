---
title: "xserver-xorg-driver-via"
date: 2006-03-22
forum: Requests
---

### Post by surak on 2006-03-22
xserver-xorg-driver-via has no breezy version for amd64. Besides, the 6.8.2 version has a problem on via_mode.c which prevents some hardware from displaying  more than 640x480 on 24bits and 800x600 on 16bits. This error was corrected on july 24, 2005 on x cvs.

Look at
[http://webcvs.freedesktop.org/xorg/xc/programs/Xserver/hw/xfree86/drivers/via/via_mode.c?r1=1.7&r2=1.8](http://webcvs.freedesktop.org/xorg/xc/programs/Xserver/hw/xfree86/drivers/via/via_mode.c?r1=1.7&r2=1.8)

Xserver-xorg-driver-via has no version compiled in breezy for amd64 and powerpc also, only in dapper. This could lead more people to use it while dapper (and its derivatives) don't come to public.

---

