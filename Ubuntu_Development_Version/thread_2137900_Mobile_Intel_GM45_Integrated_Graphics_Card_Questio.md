---
title: "Mobile Intel GM45 Integrated Graphics Card Question"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-04-22
My Toshiba Satellite C660-15R has got a Mobile Intel GM45 Integrated Graphics Card
and About Computer reports the Experience as Standard

[ATTACH=CONFIG]241646[/ATTACH]

Is their any way to improve the Experience?

Roland

---

### Post by dino99 on 2013-04-22
that display is quite useless; the kernel find then set the gm45 quite well

---

### Post by roly33 on 2013-04-22
> **dino99 said:**
> that display is quite useless; the kernel find then set the gm45 quite well

Ok thank's.  I'm pretty much used to the Windows experience Index and thought that it was similar.

Is there any point to Installing [these]("https://01.org/linuxgraphics/") when they get a 13.04 version?

Roland

---

### Post by dino99 on 2013-04-22
Intel is actively contributing to open-source, so the kernel's builtin drivers already deal with the actual chipsets (and those not yet out also have their kernel driver). On the xserver side, xserver-xorg-video-intel is doing the interface for displaying.
So there is no need to manually download/upgrade as you are used with MSos

---

### Post by roly33 on 2013-04-22
> **dino99 said:**
> Intel is actively contributing to open-source, so the kernel's builtin drivers already deal with the actual chipsets (and those not yet out also have their kernel driver). On the xserver side, xserver-xorg-video-intel is doing the interface for displaying.
So there is no need to manually download/upgrade as you are used with MSos

Ok thank's Ubuntu certainly makes life a lot more simple compared to windows.

Roland

---

