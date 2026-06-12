---
title: "update Nvidia"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by MikeCyber on 2012-09-22
How to most easily update the upcoming 12.10 to the latest Nvidia drivers? Could I do something alike ./Nvi* --update?
Thanks

---

### Post by dino99 on 2012-09-22
no, only install the xorg-edgers ppa from launchpad and you will get the latest driver.

---

### Post by pogopuschel on 2012-09-22
If you do not know what you are doing, it is no good idea to *add* Xorgedgers PPA, since you would get a bunch of other Updates, eg mesa, Intel driver aso. Just pick the nvidia-current package from their PPA by selecting "package details".
Or, as described on the Xorgedgers page:
[I]For less fresh, more stable updates, see [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
[/I]Nvidia-current is the same version as Xorgedgers offers.

---

### Post by funicorn on 2012-09-22
I dont suggest you install version 304.48, it's unstable and system suffers from regression in some aspects. 304.43 is good.

---

### Post by MikeCyber on 2012-09-22
I remember some headache in 10.04 with ppa hence in 12.04 i only removed and installed a nvidia download. I wonder, if I could do it even more easily and what could be the cause for no AA with fxaa:
[http://flightgear.org/forums/viewtopic.php?f=19&t=16943&start=15](http://flightgear.org/forums/viewtopic.php?f=19&t=16943&start=15)

---

