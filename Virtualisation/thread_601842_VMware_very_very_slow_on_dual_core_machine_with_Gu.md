---
title: "VMware very very slow on dual core machine with Gutsy"
date: 2007-11-03
forum: Virtualisation
---

### Post by jhoderd on 2007-11-03
Hi,

I used to run VMware fine under a Edgy host in an old Athlon machine.  I recently upgrade to a Pentium Dual core machine (AMD64 arch) and I've installed Gutsy.

The problem is that VMware is now horribly slow.  I have tried booting with the "nohz=off" kernel option to see if the problem was in the new tickless kernel, but there's no change.

So, I have two questions:

1) Does anyone know why this could be happening?
2) Is someone out there running Gutsy AMD64 on a dual core machine, and having no speed problems when booting a guest OS inside VMware?

Thanks in advance,
Jean

---

### Post by Delvien on 2007-11-04
I'm having problems when running Vmware on a intel dual core 32 bit processor, so its not only AMD. Mine is very slow, I switched to VirtualBox anyway, Vbox is so fast.

---

### Post by HDave on 2008-01-03
I am running VMware on Gutsy on 2.5Ghz dual-core Intel.   It too is running very very slow.  CPU is constantly at 70%-80% even though I have almost nothing running in it.

Any ideas?

---

### Post by Kzin on 2008-01-03
I noticed that VMWare runs slower on my AMD64 machine under Ubuntu than it did under Slackware... I guess thats Gnome VS KDE too or something.  Something to note is that they mention on the VMWare forums that their 64 bit architecture is flaky at best.  You may want to just install the 32 bit kernel.  Oh, and if you have less than 4 G of ram there isn't much benefit to the 64bit arch. or so I've heard.  Something to do with PAE?

---

### Post by dpj23 on 2008-01-03
I have notice a problem when a virtual machine is trying to use multiple processors it has to wait for both to be free to process the calls...  

I don't remember you posting whether or not you configured your machine to use 2 processors or 1...  However, if you configured your machine to use 2, then you can try this solution:  Simply re-configure the vm to run on 1 processor... this will allow the calls to go through the process as soon as 1 is available...

This has been noted on the vm boards as well...  

This recommendation is a quick fix...  Which has proven to work in some cases when it was a resource scheduling problem with multiple processors...

---

### Post by fjgaude on 2008-01-03
> **HDave said:**
> I am running VMware on Gutsy on 2.5Ghz dual-core Intel.   It too is running very very slow.  CPU is constantly at 70%-80% even though I have almost nothing running in it.

Any ideas?

Well, off and on I've seen this in both my AMD box and my Dell Intel laptop. What seems to always cure the situation for awhile, like until I reboot, is to get out of VMware and using Open System Monitor kill the vmware processes. The CPU activity stops. Then go and restart VMware and its vm guest. The CPU should stay quiet.

I've also noticed that just getting out of the vm and restarting it, WinXP in my case, the CPUs quiet.

I've never used VMware with less than two CPUs active.

---

### Post by tbranham on 2008-01-03
> **Delvien said:**
> I'm having problems when running Vmware on a intel dual core 32 bit processor, so its not only AMD. Mine is very slow, I switched to VirtualBox anyway, Vbox is so fast.
Too true. VirtualBox is nice!

jhoderd@ I can't give you a specific reason, but I can confirm that I had a whole lot of problems getting VMware to work smoothly on my 64-Bit machine.

Good luck.

---

### Post by dpj23 on 2008-01-03
O.K., I don't want to confuse anyone here...

I was referring to the quest operating system only...  If the VM machine is configured to run with 2 processors try it with only 1...  

Do not play around with the host operating system what-so-ever...  We have experienced this problem when we migrated servers from physical to virtual...  We noticed that the virtual servers had major slow down when trying to run with 2 virtual processors...  When we adjusted them to run with 1 there performance returned to our expectations...

---

### Post by fjgaude on 2008-01-03
> **dpj23 said:**
> O.K., I don't want to confuse anyone here...

I was referring to the quest operating system only...  If the VM machine is configured to run with 2 processors try it with only 1...  

Do not play around with the host operating system what-so-ever...  We have experienced this problem when we migrated servers from physical to virtual...  We noticed that the virtual servers had major slow down when trying to run with 2 virtual processors...  When we adjusted them to run with 1 there performance returned to our expectations...

Okay, it seems at first blink you are right... my dual-core machine seems to be faster using just one core. I wouldn't have thought of the reason you give but it makes since. I've sure that vmware will fix this soon.

---

### Post by HDave on 2008-01-03
I have the same problem.  Tried going with one core...and VMware simply pegs that one core.

It leaves the host OS (Gutsy) usable, but renders the guest OS (WinXP) unusable.

---

### Post by Tuxi on 2008-01-03
I just stumbled across this thread looking for another issue (USB removable devices not working).  I had the VM using two cores, and switching to one seemed to work wonders -- low CPU loads.

---

### Post by fjgaude on 2008-01-03
USB devices not working, eh? Here the fix by having these lines uncommented:

[HTML]gksudo gedit /etc/init.d/mountdevsubfs.sh

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb[/HTML]

 Uncomment no. 42-45 lines starting with #mkdir -p /dev/bus/usb/.usbfs and then reboot.

That should do it, if not get back here with us.

---

### Post by HDave on 2008-01-04
After reading more threads, I have switched back to 1 CPU and also bumped down the memory to 500MB.

Seems to work like magic.

---

### Post by dpj23 on 2008-01-04
Currently I configure my workstations as follows:

XP Pro (minimum RAM 512 MB, Preferred RAM 640MB +)

Vista Enterprise (minimum RAM 640MB, Preferred RAM 756MB +)

Linux OS (minimum RAM 512, Preferred RAM 640MB +)

I always want more, but settle for what is available....

---

### Post by noogen on 2008-01-12
You guys are right on the money!  Using 1 core is much faster.  I'm on Gutsy 64bit with dual core with 8 gig ram.  In generall, my VMWare experience has been great.  Coming from MS VPC2007, the dual core  vmware xp is much faster, but I was still unable to play movie smoothly on it.  I was browsing the forum and stumple on this thread and now my VM is faster.  Thanks.

---

### Post by fjgaude on 2008-01-12
From what I've read on the fourms vmware is working on making their product work with more than one CPU core, in the next release of the free version.

---

### Post by SJrX on 2009-01-18
_**ONE CORE**_ 
Guest OS works great.

I was so frustrated with VMWares preformance, but my Windows 2003 client was WAY to slow, it took hours to sync my iPhone to backup. I tried throwing the nice value to -20, and still it tanked. One core fixed it in a jiffy!

Thanks Genius.

(I registered to just put this post)

---

### Post by dcstar on 2009-01-25
> **fjgaude said:**
> From what I've read on the fourms vmware is working on making their product work with more than one CPU core, in the next release of the free version.

Which was supposed to be VMWare Server 2.0 (this is an **old** thread), so can anyone confirm if the multi-CPU issue is fixed in 2.0?

---

