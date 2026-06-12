---
title: "Jockey suggests blacklisted driver - nonsense"
date: 2011-10-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-17
During PP install on Dell Vostro 13** Laptops, Jockey pops-up suggesting restricted drivers for WLAN. If you accept, there will an unspecified error and message to see log. Basically the driver is blacklisted at /etc/modprobe.d/blacklist-bcm43.conf. Users must install bcmwl-kernel-source to get these cards working.

But, if it is blacklisted, why suggest it? 

So, I'm in doubt if this should be a bug report or a feature request:

Bug report: The situation I described. Users won't know what to do and will have no wlan.
Feature request: Jockey should only suggest drivers that are not blacklisted.

Regards,
Effenberg

---

### Post by ventrical on 2011-10-17
Wow.

  I'll load up my PP usb on my Dell Inspiron B130 (has that broadcom b43) and see if i can replicate the problem.

---

### Post by cariboo on 2011-10-17
When I did a fresh install of Oneiric on my netbook, I was offered both the b43 driver and the Broadcom STA driver, although the STA driver was marked recommended. During the Natty testing session we found that for the Broadcom 4312 chipset, some systems used the b43 driver, and others used the bcmwl driver. During last testing session some systems installed the Broadcom open source driver. 

Although for me the Broadcom drivers work well on 3 systems that use Broadcom devices, there still is a huge mess where drivers are concerned. Being closed source, it's pretty hard to track down problems, but personally I think it's more a firmware problem, that gets installed when the driver is installed than anything else.

---

