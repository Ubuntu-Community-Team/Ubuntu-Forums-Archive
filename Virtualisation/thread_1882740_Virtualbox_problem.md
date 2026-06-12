---
title: "Virtualbox problem"
date: 2011-11-17
forum: Virtualisation
---

### Post by chenr1 on 2011-11-17
Hey guys im trying to start a VM on my optiplex 745 and i first get the following message VT-x/AMD-V hardware acceleration is not available on your system. Certain guests (e.g. OS/2 and QNX) require this feature and will fail to boot without it. I click continue it goes a little further and then this happens VT-x/AMD-V hardware acceleration is not available on your system. Certain guests (e.g. OS/2 and QNX) require this feature and will fail to boot without it.   I've heard people virtualize on this same machine. (optiplex 745) So i dont think its my hardware,  Please help.

---

### Post by collisionystm on 2011-11-17
Reboot your computer
Hit F2 for bios
enable virtualization

if its not there
change virtualbox settings to disable VT-x/AMD-V and do not attempt to run x64 bit guest os

---

### Post by chenr1 on 2011-11-17
Its not in bios. So how do i disable it in VB? and not attempt to be in 64

---

### Post by chenr1 on 2011-11-18
bump

---

### Post by coldraven on 2011-11-18
> So how do i disable it in VB?
See the screenshot.
If you see an OS that has X86 at the end of it's filename it is 32bit.
If it has AMD64 it is 64bit

---

### Post by Perryg on 2011-11-18
If the system (host) does not support VT-x/AMD-v that section will be grayed out for the user.  The solution is don't try to install 64-bit OSes or 32-bit OSes that need the VT-x/AMD-v feature since they will not work.

---

