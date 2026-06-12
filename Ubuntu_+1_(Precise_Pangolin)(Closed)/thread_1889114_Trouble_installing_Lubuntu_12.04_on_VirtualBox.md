---
title: "Trouble installing Lubuntu 12.04 on VirtualBox"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shiva.n on 2011-11-30
Didnt want to hijack any of the other 12.04 Lubuntu threads.

I downloaded the latest ISO of Lubuntu 12.04, and am trying to install it on a VM in VirtualBox to help with alpha testing. The Live CD loads up great on the VM. I install Lubuntu 12.04 on the VM with no issues. When I boot after install, the machine hangs while booting at one of the following steps 

1. Checking battery state
2. Trying to start CUPS 
3. saned error

I booted in recovery mode and installed Guest Additions. Now the boot still hangs, but with a wierd blue flicker!

I dont think this is a problem with 12.04 Lubuntu. Just something wrong with what i am doing with Virtualbox. Most likely a display issue I think. 

Any help would be much appreciated. Let me know if you need any more debug info or logs.

Thanks much.

---

### Post by shiva.n on 2011-11-30
This issue is Solved.  I tried to enable 3D Acceleration, and did a fresh install, and Lubuntu 12.04 booted fine!

---

### Post by shiva.n on 2011-12-01
I take that back. I tried a fresh install but still ran into my original hang on boot problem. I have one good VM running Lubuntu 12.04, but cant seem to install another one!

---

