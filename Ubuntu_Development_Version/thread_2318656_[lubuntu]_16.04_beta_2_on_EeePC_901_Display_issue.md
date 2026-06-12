---
title: "[lubuntu] 16.04 beta 2 on EeePC 901: Display issue"
date: 2016-03-28
forum: Ubuntu Development Version
---

### Post by GoetzKluge on 2016-03-28
Perhaps useful for developers: I installed Lubuntu 16.04 beta 2 on an old EeePC 901.

Graphics won't start with standard boot.
However, it works with 800x600 display in recovery mode.

Logfiles: [ATTACH]268029[/ATTACH]

Happy Easter,
Goetz

PS: As for entering graphics mode, Ubuntu 16.04 beta 2 with Mate desktop as well as Xubuntu 16.04 beta 2 so far work fine on my stoneage EeePC 901.

---

### Post by howefield on 2016-03-28
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by macmpi on 2016-04-22
> **GoetzKluge said:**
> Perhaps useful for developers: I installed Lubuntu 16.04 beta 2 on an old EeePC 901.

Graphics won't start with standard boot.
However, it works with 800x600 display in recovery mode.
Hi, same problem here with Lubuntu 16.04 release on EeePC 1005HA.
Tried BootRepair under recovery but it did not fix the problem.
BootRepair info here: [http://paste2.org/mWUnmv05](http://paste2.org/mWUnmv05)

Thanks for any help!


PS: Lubuntu 16.04 image on USB allowed to install properly, but Lubuntu Trial (no install) would not boot either...

---

### Post by GoetzKluge on 2016-04-23
> **macmpi said:**
> Hi, same problem here with Lubuntu 16.04 release on EeePC 1005HA.
Tried BootRepair under recovery but it did not fix the problem.
BootRepair info here: [http://paste2.org/mWUnmv05](http://paste2.org/mWUnmv05)

Thanks for any help!


PS: Lubuntu 16.04 image on USB allowed to install properly, but Lubuntu Trial (no install) would not boot either...

My EeePC 901 now runs with Xubuntu.

By the way, here are the graphics data  for the EeePC 901:
- Card: Intel Mobile 945GSE Express Integrated Graphics Controller
- Display Server: X.Org 1.18.3
- drivers: intel (unloaded: fbdev,vesa)
- Resolution: 1024x600@60.00hz
- GLX Renderer: Mesa DRI Intel 945GME x86/MMX/SSE2
- GLX Version: 1.4 Mesa 11.2.0

Best regards
Goetz

---

### Post by macmpi on 2016-04-23
Thanks Goetz,

After more digging, I think I found a solution.
It seems i915 intel driver has some issues from 14.04 and on.
According to the following article, there are updated & optimized driver from a ppa
[http://sourcedigit.com/17038-install-updated-optimized-graphics-drivers-on-ubuntu-15-04-ubuntu-14-04/](http://sourcedigit.com/17038-install-updated-optimized-graphics-drivers-on-ubuntu-15-04-ubuntu-14-04/)

[This PPA]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers") now supports 16.04
Following this and installing as suggested:

 ```
$ sudo add-apt-repository ppa:oibaf/graphics-drivers
$ sudo apt-get update
$ sudo apt-get install xserver-xorg-video-intel
```Reboot, and done!
My EeePC now boots fine, and runs 1024x600@60Hz !
(now I still have to solve unreliable wifi AR9285 with my WPA1 router, but it's another story...)

---

