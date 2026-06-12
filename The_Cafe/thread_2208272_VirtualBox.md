---
title: "VirtualBox"
date: 2014-02-27
forum: The Cafe
---

### Post by moses65 on 2014-02-27
I have recently installed **VirtualBox** as I need some of the more advanced features of Excel.  It seems to be working really well and to be an excellent solution to the problem of what to do with XP when it is no longer maintained by Microsoft - i.e. install it inside VirtualBox and retain the use of your old software.

btw do let me know when GRUB definitely can do the full Dual boot on a Windows 7 Machine so I can put Ubuntu on that too.

---

### Post by Bucky Ball on 2014-02-27
> **moses65 said:**
> 

btw do let me know when GRUB definitely can do the full Dual boot on a Windows 7 Machine so I can put Ubuntu on that too.

It can do it now, but if you want support with that, please post a thread in the appropriate forum area. ***The Cafe*** is a non-support forum. Good luck.

---

### Post by mattlach on 2014-02-27
> **moses65 said:**
> I have recently installed **VirtualBox** as I need some of the more advanced features of Excel.  It seems to be working really well and to be an excellent solution to the problem of what to do with XP when it is no longer maintained by Microsoft - i.e. install it inside VirtualBox and retain the use of your old software.

If you don't want to boot an entire windows install in a VM, and you find that it is difficult to get Wine to work properly, there is always Crossover Linux (Originally Crossover-Office). It is a commercial development on top of Wine in which Windows Office products work seamlessly, without needing to launch a full VM.   It costs about $60 though if I recall.  May or may not be worth it to you.

Personally I started with VMWare Player, but in recent versions I have had a hard lock problem with VMWare pPlayer, so I recently switched to VirtualBox as well.   Apart from the comparatively poor DirectX implementation compared to VmWare, it has been pretty good to me.

> **moses65 said:**
> 
btw do let me know when GRUB definitely can do the full Dual boot on a Windows 7 Machine so I can put Ubuntu on that too.

Not sure what you are talking about here.  I've been using Grub to dual boot Windows 7 since it's launch in 2010...     These days it is super easy, it just auto detects it during launch, if Windows 7 is installed and you drop Linux on a different partition.

It gets a little trickier if you install Ubuntu before Windows, as Windows 7 will overwrite the MBR, and Linux will no longer boot.  However, if you google there are plenty of guides on how you can restore Grub (and autodetect Windows presence) using a live cd.

---

