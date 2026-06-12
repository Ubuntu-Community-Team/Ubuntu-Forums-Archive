---
title: "Ubuntu GNOME boots to tty1 w/i945 graphics"
date: 2015-06-04
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-06-04
Seems to be just hardware related, but Ubuntu GNOME just boots to tty1 on this set of hardware:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

It affects both the live session and Ubuntu GNOME Wily installed.

Both Ubuntu and Ubuntu Mate work OK on the same hardware so I even tried swapping to 'lightdm w/gtk-greeter' but no joy :(

But Ubuntu GNOME Wily works OK on this hardware:

> Intel Motherboard: DB43LD
Intel Pentium Dual-Core CPU E5300 @ 2.60GHz
Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
3GB DDR2 RAM

Seems odd that Ubuntu GNOME would differ from Ubuntu and Ubuntu Mate on the same hardware, but something ain't happy ;)

---

### Post by kerry_s on 2015-06-04
intel drivers broke yesterday. took me awhile to get up & running had to create a 20-intel.conf file to get it to boot to gui, but it's running in vesa mode.
from log:
```
[     8.019] (EE) Failed to load /usr/lib/xorg/modules/drivers/intel_drv.so: /usr/lib/xorg/modules/drivers/intel_drv.so: undefined symbol: xorgMir
[     8.019] (II) UnloadModule: "intel"
[     8.019] (II) Unloading intel
[     8.020] (EE) Failed to load module "intel" (loader failed, 7)
```

apparently it's a mir issue.

also on boot my mouse is invisible, have to log out & back in to get back. luckly i can do that with just keyboard.

---

