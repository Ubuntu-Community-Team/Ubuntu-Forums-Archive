---
title: "Edgy Eft took one step backwards?"
date: 2006-10-27
forum: Sun Sparc Users
---

### Post by ubumatic on 2006-10-27
Hello,

I just tried to install Edgy Eft (6.10) to my Sun Blade 1000. It didn't detect the disk (FC-AL). Ubuntu 6.06.1 did detect the disk, so 6.10 seems to be a step backwards.

The 6.06.1 would be just fine but the fans are blowing at full speed all the time. I have this impression that the bbc_i2c driver, which controls the fan speed, has been fixed in newer kernels (Eft).

Has anyone got these fans under control? The bbc_i2c driver in 2.6.15-27 seems to hog CPU which kind of negates the whole purpose of the bbc_i2c.

---

### Post by calixtine on 2006-10-28
You are right the bbc_i2c driver is fixed in 2.6.17, however the way the proprietary qlogic firmware is loaded for the QLogic Fibre Channel HBA Driver also changed, it now has to be loaded with initramfs, this doesn't appear to happen with the 2.6.17 kernel shipped with edgy. The result is the kernel can't find the root disk and initialisation just stops. 

Fortunately as I did a dist-upgrade I've still got the old 2.6.15 dapper kernel which works, but of course my Blade 1000's fans are left permanently on full-blast.

Next I just have to work out how to get initramfs to load the damned qlogic firmware blob. Any help much appreciated!

More info read this post :

 [http://marc.theaimsgroup.com/?t=116107449400001&r=1&w=2](http://marc.theaimsgroup.com/?t=116107449400001&r=1&w=2)

---

### Post by ubumatic on 2006-10-28
Thanks for the link. Well, it seems that no Edgy Eft for me until this driver problem has been fixed.

Do you know if using 2.17 bbc_i2c works with 2.16 and fixes the problem? The difference between them is small:
[http://www.gelato.unsw.edu.au/lxr/diff/drivers/sbus/char/bbc_i2c.c?v=2.6.16;diffval=2.6.17;diffvar=v](http://www.gelato.unsw.edu.au/lxr/diff/drivers/sbus/char/bbc_i2c.c?v=2.6.16;diffval=2.6.17;diffvar=v)

This box works so sweetly with 2.16. Probably the cheapest and fastest option to backporting would be using earplugs :D

---

