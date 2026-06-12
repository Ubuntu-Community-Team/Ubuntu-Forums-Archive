---
title: "LTS of Ubuntu is the most popular version?"
date: 2019-06-19
forum: Ubuntu, Linux and OS Chat
---

### Post by j2ee on 2019-06-19
More popular than the 9 months support version?

---

### Post by kpatz on 2019-06-19
LTS is recommended for live/production use where you want a stable system that doesn't require an OS upgrade/reinstall every 6 months.

I think of LTS as the production/stable version, and the non-LTS as development versions.  The latest non-LTS has newer packages that aren't tested as thoroughly, but contain the latest features.

Personally, I run LTS versions on my hardware, and I only experiment with non-LTS versions in VMs.

---

### Post by coffeecat on 2019-06-19
*Thread moved to **Ubuntu, Linux & OS Chat**.*

---

### Post by TheFu on 2019-06-19
> **j2ee said:**
> More popular than the 9 months support version?

I don't touch non-LTS releases unless absolutely required for new hardware needs.  Recently, Canonical has been pushing alpha capable software into their non-LTS releases and causing some pain for the community.

If you want to be bleeding edge, it is there.
If you want a system that works and is basically boring because it is so stable, use the LTS.
I did my bleeding edge Linux time in the 1990s.

---

### Post by lammert-nijhof on 2019-06-19
In general use LTS. I have Vega graphics, that is why I use Ubuntu 19.04 for the newest video drivers of Linux 5.0. I use a minimal install of Ubuntu 19.04 as Vbox Hosts and do my normal work in a virtual machine with Xubuntu 18.04.2 LTS. So you can have both, support for the newest hardware and the reliability of a LTS release.

---

### Post by j2ee on 2019-06-19
> **lammert-nijhof said:**
> In general use LTS. I have Vega graphics, that is why I use Ubuntu 19.04 for the newest video drivers of Linux 5.0. I use a minimal install of Ubuntu 19.04 as Vbox Hosts and do my normal work in a virtual machine with Xubuntu 18.04.2 LTS. So you can have both, support for the newest hardware and the reliability of a LTS release.

Do you fee not as smooth as native or missing something in virtual machine?

---

### Post by TheFu on 2019-06-19
> **j2ee said:**
> Do you fee not as smooth as native or missing something in virtual machine?

Life is about trade-offs.  

Processing is unaffected.  The GUI is a impacted, but only if you use a GUI that prefers direct GPU access like Gnome3 or KDE. If you use any lighter desktop, then it isn't noticed, most of the time.

There is 1 area where easy-to-setup VMs lack compared to native, high-end graphics, but there are 20 other areas where VMs far surpass loading directly on physical hardware.  For properly setup servers, over 95% of native performance is possible and has been since 2010.  Just need to share the hardware in a way that works for all the running VMs. Obviously, you can't get 1 GigE interface to push 1 Gbps for 20 VMs concurrently, but you can share the available bandwidth efficiently or have different VMs use different physical NICs or do bonded NICs on the host that get shared by all the VMs. Lots-o-solutions to get the performance needed, without giving up the flexibility of decoupled from hardware OSes.

But if you really want native graphics performance, then you can dedicate a GPU to a VM and pass through the PCIe device.

---

### Post by lammert-nijhof on 2019-07-17
Virtual Machines are not slow at all. I would say my response time in the VMs are the best. My Host file system is ZFS and everything is LZ4 compressed, which more or less halves the number of disk IOs needed to load a program. I use 4 GB of memory cache and around 50 GB of SSD cache on top of 3 striped HDDs. So if I use one, two or three Virtual machine, they will run almost completely from memory cache, after a short while. Response times in my VMs are instantaneous. 
Two months ago I used a 2008 HP dc5850 with 8 GB DDR2 and a Phenom II X4 B97 (3.2 GHz) in exactly the same way with the same disk configuration, only with 2 GB of memory cache. I admit, the response times were closer to half a second than zero. For this setup you need at least 8 GB. 

If you do a lot of serious gaming with real GPUs, it is not a solution, you need the raw GPU. But I play a number of standard Linux games like Extreme Tux Racer and Super Tux Cart easily in a Virtual Machine with 3D acceleration enabled. 

Another huge advantage is safety, I have a separate VM for banking and PayPal, It is "powered-on" not more than two hours per week and its firewall blocks all inbound traffic. That VM is only used for that purpose, so the chance to catch virus or malware is minimal. 
I have another VM to try out new stuff, if it fails I rollback the VM and I'm clean and ready for the next test. I don't pollute my main system with these experiments. 
I like Windows Media Player, so I still use it to play my music (old wma copies of CDs and LPs) in Windows XP with WOW and TrueBass effects.

---

