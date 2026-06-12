---
title: "What OS to Virtualise"
date: 2010-09-22
forum: Virtualisation
---

### Post by jagoodjee on 2010-09-22
I need some advice on whether to install Windows 7 and then use VMware to virtualise Ubuntu or install Ubuntu and then virtualise windows 7. I will be using Windows 7 for microsoft office and itunes, and use Ubuntu for web browsing and executing commands for my electronic engineering course at Uni.

Also wondered if you could install an upgrade version of Windows 7 on VMware which I highly doubt or if you had to use the full version. 

Thanks in advance of responses.

---

### Post by perspectoff on 2010-09-22
Don't you need a license for each virtual instance of Windows 7?

I would think this makes Windows 7 a poor choice for virtual machines.

Ubuntu (or other Linux) OSs don't need a license for each instance, so you can make many virtual machines. 

That is why Linux is far more suitable for virtualization than Windows (and probably why supercomputers use Linux, as well).

There is a third option: have a bare metal hypervisor and virtualize both. That's probably the best if you are really going to virtualization. It's probably what a lot of datacenters do.

But I'll let those more expert than I comment on how to do that.

To be honest, I have moved completely away from Microsoft Office and am now completely OpenOffice. I don't use iTunes anymore, either (since the imboglio over DRM a few versions ago where iTunes tried to lock the files to use on a single computer. I know that's been rectified, but that's always the danger of proprietary software).

To answer your question directly, use Windows 7 as the host and run virtual machines in it.

But you can also run Ubuntu from within Windows using Wubi without using virtual machines. You can also install Ubuntu on a separate partition and choose which one to run. these options don't allow you to run Windows and Ubuntu simultaneously, though, if that is your intent.

---

### Post by TheFu on 2010-09-22
I love Linux and use it 95% of the time.

If you have only 1 machine to work with and don't want to be stuck, then you'll want to have MS-Windows-whatever as the host machine and run Linux inside a VM or 2 or 5.  There are still some hardware that only has Windows drivers.  You may need that flexibility in the future. 

OTOH, you may not need the flexibility and running Linux as the hostOS could work too.  I've done both, but I have multiple machines.  On my laptop, Win7 x64 is the host OS and Linux, BSD, WinXP, OpenSolaris, Netbook-Remix are client OSes. I spend 95% of the day using a Linux install under this config.

Another option is to buy another HDD and try it both ways.  For $40, you can get a 200GB+ laptop HDD and swap them as needed. Once you decide the config that works best for you, then you have a 2nd disk for good backups.

In an ideal world, the hostOS wouldn't matter. I live in the real world and sometimes MS-Windows is required.

---

### Post by srhart on 2010-09-23
At work I have an Ubuntu 10.04 workstation host machine running virtual instances of Windows 7 and XP. With this setup, I can have both the XP and the Windows 7 guest machines running simultaneously, not full speed but certainly usable for a work environment. I use Win7 for Outlook and Office and XP (unfortunately) for QuickBooks.

On the same machine, I've tried using Windows 7 as the host with Ubuntu as the guest and my perception is that it's OK for testing but it's not fast enough to use in a working environment.

I have 4G RAM as lots of memory helps. The virtualisation engine is VirtualBox (excellent).

So my recommendation, FWIW, is Ubuntu host and Windows guests. I have also had other Linux distros as guests at the same time, no problem. My impression is that it's also more stable.

---

### Post by TheFu on 2010-09-24
That is encouraging.  

Do you have any strange hardware that needs specific drivers?  That has been my fear - Windows-only drivers that can't be USB-passed-thru.

I can concur on the Windows host OS stability issue. Win7 x64  and Vista x64 before that never stayed up more than 7 days for me when running VirtualBox.  Back in the 1990s, NT4.0 would stay up for 3+ weeks at a time while I was doing C/C++ software development.  

Unfortunately, I had similar stability issues with VirtualBox on Ubuntu 10.04 x64 running WindowsXP - actually, it would trash the X/Windows GUI after about 3 days and a complete system reboot (ssh in from a remote machine) was required. These were different physical machines, an E6600 and 2 Core i5s.  OTOH, an E8400 running Xen and 10 paravirtual Linux machines stays up for multiple months, no problem, but there's no Microsoft anything on that machine. ;)  The ESXi machine, E9450, with a mix of Windows7 and Linux and OpenSolaris machines stays up months and months at a time without any issues. It is rock solid and performs well.

Most machines here have 8GB of RAM, but all have at least 4GB, so running VMs isn't an issue.

---

### Post by jetgraphics on 2010-09-25
> **srhart said:**
> At work I have an Ubuntu 10.04 workstation host machine running virtual instances of Windows 7 and XP....
I have 4G RAM as lots of memory helps. The virtualisation engine is VirtualBox (excellent).


I, too, have a 4G Ram machine, that I wanted to run with Ubuntu as a host for WinXP. My concern was in finding a virtual tool that gave me reasonable performance on the virtual OS.

I confess to noobie disease and have fouled my nest with various failed attempts. 
I run BeyondTV on the WinXP machine, but I'd rather run it under a Linux host. I wish I could get MythTV working with my tuner card (Hauppauge), but the analog tuner is still not supported by MTV.

---

### Post by davrosuk on 2010-09-26
My recommended approach is Linux as host and windows virtualised unless there is a specific need or requirement to have it the other way round. Bare metal virtualization was mentioned earlier (eg VMWare ESX), which although is the gold standard, would not meet the OP's needs.

---

