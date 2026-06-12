---
title: "Virtualize existing Ubuntu and still boot into it"
date: 2014-05-08
forum: Virtualisation
---

### Post by Matthew_Lowther on 2014-05-08
Hello all!  So I want to take my existing Ubuntu 14.04 installation that I have and virtualize it.  However, I also want to be able restart my pc and boot into that same installation.  Is that a thing?  I'm using VMware Workation 10 in Windows 8.1.  The option to use a physical disk still wants to make it into a VMDK, which is what I don't want to do.

---

### Post by LastDino on 2014-05-08
Is making a fresh install on that VM not an option? 

While making image of existing 14.04 is possible but making it run on VM successfully is not that simple, it may work or may not. Stability will be always in question. Fresh install including software you need may need you less than hour and compared to doing what you want, it is far more safe and sure fire way of doing things.

However, if you still want to try, you can give it shot by using Clonezilla.

---

### Post by TheFu on 2014-05-09
> **Matthew_Lowther said:**
> Hello all!  So I want to take my existing Ubuntu 14.04 installation that I have and virtualize it.  However, I also want to be able restart my pc and boot into that same installation.  Is that a thing?  I'm using VMware Workation 10 in Windows 8.1.  The option to use a physical disk still wants to make it into a VMDK, which is what I don't want to do.

Step back and think about what a VM hypervisor does.
It emulates hardware - the motherboard, southbridge, northbridge, NICs, GPU, RAM, CPU, .... everything.
So, if you want to boot from physical AND virtual hardware using the same image, then those things need to match as closely as possible.  Linux can handle more differences between reboots that other options, so there is hope - provided the VM image is installed onto real hardware.

So ... it is non-trivial.

Here's the only person that I know who got something working: [https://systemoverlord.com/blog/2013/04/04/booting-raw-partitions-in-virtualbox-with-grub2/](https://systemoverlord.com/blog/2013/04/04/booting-raw-partitions-in-virtualbox-with-grub2/)

i haven't any clue about VMware Workstation capabilities.

---

### Post by pixelfairy2 on 2014-05-21
its a thing. its a relatively common thing. heres the instructions.

[http://pubs.vmware.com/workstation-10/index.jsp#com.vmware.ws.using.doc/GUID-BA557736-482C-42C1-BC52-C76673948D2F.html](http://pubs.vmware.com/workstation-10/index.jsp#com.vmware.ws.using.doc/GUID-BA557736-482C-42C1-BC52-C76673948D2F.html)

linux is fine with new hardware. so doing this should not be a problem. remember to enable all the things in cpu options, or at least hyperviser and code profiling so you dont have to reboot the vm later.

---

