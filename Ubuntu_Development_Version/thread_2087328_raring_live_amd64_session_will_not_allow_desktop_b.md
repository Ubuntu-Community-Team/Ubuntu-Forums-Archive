---
title: "raring live amd64 session will not allow desktop background to be changed"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-23
Upon clicking 'change desktop background' it bring up the whole 'system settings' dash.

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
ubuntu@ubuntu:~$ 

```

---

### Post by ventrical on 2012-11-23
Solved after install and update.

---

### Post by cecilpierce on 2012-11-28
> **ventrical said:**
> Solved after install and update.

Is this still working for you ?
I can't change mine, get the whole system settings :confused:

---

### Post by ventrical on 2012-11-28
> **cecilpierce said:**
> Is this still working for you ?
I can't change mine, get the whole system settings :confused:

 Ok .. I did this about (5)? days ago. I was referring to the Live USB of that day (Friday, Nov. 23/2012) on Acer Extensa 4420 AMD Athlon 2X Dual Core. Once I *installed* it to hdd and updated, the ability to change the desktop background was restored.

Btw.. I haven't yet zsynced any of the ISOs since Friday so I am not sure what the staus of the live amd64bit iso is at the moment.

 I will then make a copy  of Fridays (phenom-unity) daily and zsync today and get back at this.

Note: (phenom-unity) is referring to an anomoly with Fridays daily with he Unity desktop where the speed and responsiveness of unity was much faster that normal.

---

### Post by nuttzo31 on 2012-11-28
I found i had to manually install the gnome-control-center-unity package.

---

### Post by cecilpierce on 2012-11-28
> **nuttzo31 said:**
> I found i had to manually install the gnome-control-center-unity package.

That worked! How did you find that out...:confused:
I was going crazy trying to get rid of that ugly wallpaper I had... Thanks

---

### Post by nuttzo31 on 2012-11-28
Often there are packages missing from the daily builds that aren't picked up with an update.

---

### Post by grahammechanical on 2012-11-28
>  I am not sure what the status of the live amd64bit iso is at the moment.

I can tell you the state of the daily amd64 images for 26th and 27th on my machine.

The live session breaks down during the second purple screen when Casper brings up Busybox with the message:

> Panic Unable to find a medium containing a live file system

I have not found an existing bug report for this. I have learnt how to add 'debug' to the boot parameters and I am now learning how to save log files from a broken live session to my hard disk to include in a bug report. And I am failing.

"Learning all to time!"

Oh. In messing around with this issue I have noticed that Nautilus 3.6.3 in Raring does not detect CD/DVDs.

Regards.

---

### Post by serdotlinecho on 2012-11-28
> That worked! How did you find that out...:confused:
I was going crazy trying to get rid of that ugly wallpaper I had... ThanksYou mean the default Ubuntu wallpaper?  =D>

---

### Post by cecilpierce on 2012-11-28
> **serdotlinecho said:**
> You mean the default Ubuntu wallpaper?  =D>

Yep, have three RR's installed and get tired of looking at the same thing.

---

### Post by ventrical on 2012-11-28
Ok.. todays daily Nov.28th(27) the problem is solved - ubiquity also solved. Booted up great here.

So I will mark this thread as solved.

---

### Post by ventrical on 2012-11-28
> **grahammechanical said:**
> I can tell you the state of the daily amd64 images for 26th and 27th on my machine.

The live session breaks down during the second purple screen when Casper brings up Busybox with the message:



I have not found an existing bug report for this. I have learnt how to add 'debug' to the boot parameters and I am now learning how to save log files from a broken live session to my hard disk to include in a bug report. And I am failing.

"Learning all to time!"

Oh. In messing around with this issue I have noticed that Nautilus 3.6.3 in Raring does not detect CD/DVDs.

Regards.

I don't use 'perisistve' casper very much
anymore.  Try 'discard on exit' option and see how that works. There have been problems with casper since natty I think.

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.7.0-4-generic #12-Ubuntu SMP Tue Nov 27 23:13:21 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$

---

