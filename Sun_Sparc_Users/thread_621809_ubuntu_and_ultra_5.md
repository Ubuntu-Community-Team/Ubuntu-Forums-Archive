---
title: "ubuntu and ultra 5"
date: 2007-11-24
forum: Sun Sparc Users
---

### Post by psankovic on 2007-11-24
Hi,

I have Ubuntu installed on my Sun Ultra 5 ad it was working fine. Now I have got new motherboard (better) with new (stronger) processor. When I start Ubuntu it logs in perfectly but I receive pop up window with " Can not initiate HAL". How do I upgrade ubuntu without performing totaly new installation. Previously I had problem with X and I would like to avoid same problem with new installation. 
Also can someone tell me is there desktop sparc version of 7.10 ubuntu, I found only server version for sparc.

/regards,

---

### Post by zanderred on 2007-11-24
Hi, have a look here [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) desktop for sparc [http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)  [http://cdimage.ubuntu.com/kubuntu/ports/daily/current/](http://cdimage.ubuntu.com/kubuntu/ports/daily/current/)  [http://cdimage.ubuntu.com/xubuntu/ports/daily/current/](http://cdimage.ubuntu.com/xubuntu/ports/daily/current/) have a look at xubuntu "it's light". Upgrade unbuntu you should have a look here [http://screencasts.ubuntu.com/MoS2007/11_Updating_and_Upgrading](http://screencasts.ubuntu.com/MoS2007/11_Updating_and_Upgrading). how you upgrade from server to desktop ???. Clean install would be better.

---

### Post by psankovic on 2007-11-25
Hi,

I have downloaded SPARC alternate install CD and burn it on cd, but when I want to boot sparc from it it says that there is no kernel or something like that. I have tried to use cd from previous release from which I succeeded to install linux ( at that time I had old motherboard) and I get same error. 
What to do? Please help me.

/cheers,

---

### Post by zanderred on 2007-11-27
Hi, have you tested the hard ware. have alook at sun doc's  OpenBood 3.x Command Reference Manual.

---

### Post by oddhair on 2007-11-29
You didn't say which version you had installed previously, but the [7.10 release notes](http://www.ubuntu.com/getubuntu/releasenotes/710) indicate that upgrades from previous versions need to run Fdisk on SunSparc hardware, to apply a new disk label format.  If you are coming from a previous version, this might help you.

---

### Post by psankovic on 2007-12-03
Hi,

I know now why I can not boot CD install. My firmware was locked. When I fix this problem,
I will try to install Ubuntu once again. Thanks for help.

/cheers,

---

