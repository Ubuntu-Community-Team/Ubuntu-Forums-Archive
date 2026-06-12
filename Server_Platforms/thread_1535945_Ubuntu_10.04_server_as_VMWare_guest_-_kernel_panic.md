---
title: "Ubuntu 10.04 server as VMWare guest - kernel panic not syncing vfs unable to mount"
date: 2010-07-21
forum: Server Platforms
---

### Post by lavacaballero on 2010-07-21
I've been dealing with this issue for days and can't figure out how to fix it.


Situation: I've built a customized 2.6.32 kernel over Ubuntu 10.04  server (physically) -note: it is the same version that comes with the  livecd-. Then I added my stuff, cloned the disk, applied it to 3  different hardware boxes and it works perfectly. But when I put that  image on a VMWare Workstation 7.1 or VirtualBox machine it doesn't load... I get a "kernel panic: not syncing vfs unable to mount root fs on unknown-block 0,0".


 So, I've created a new vm, I've installed ubuntu and it booted without a  problem. I ran my kernel patching as I did on the physical machine, but  when I rebooted with the new kernel, I got the same error.


 So, the problem seems to be something in the customized kernel, but specifically going over virualized copies.


 By the way - In a previous version, specifically Debian 5 with kernel  2.6.18,  I did the same stuff about a year ago and the machine loads  perfectly in any virtualized environment. Then, the only thing left to  think about my problem is that some grub parameter or kernel driver or  something is messing up with booting.


 The customization of the kernel is only the patching for IMQ stuff.


 If you have any idea about my issue, I beg you to let me know how did you deal with it.

---

### Post by lavacaballero on 2010-07-23
Update: I've tried with VirtualBox and it has the same problem, so, definetly, is some misconfiguration in the kernel... or a driver needing to be loaded?

Any hints? Please!

---

### Post by sylvester_0 on 2010-07-23
It sounds like you're missing a mass storage (hard drive controller) driver. You'll need to find out which controller your VM is emulating then compile the driver into your kernel.

---

### Post by lavacaballero on 2010-07-23
Ok, for those with the same problem:

Manage your virtual disk as IDE, not SATA. That brings up the virtual machine!!!!

Tested on VMWare and VirtualBox.

---

### Post by lavacaballero on 2010-07-23
> **sylvester_0 said:**
> It sounds like you're missing a mass storage (hard drive controller) driver. You'll need to find out which controller your VM is emulating then compile the driver into your kernel.

Indeed, it is the SATA/SCSI controller in the kernel. When specifying the disk as IDE, it boots smoothly :D

What I'm not sure is what to load or configure in the kernel for virualized disk controllers...

---

### Post by sylvester_0 on 2010-07-23
Well, if you're able to now boot up a copy of linux you could do the following:

1. Run "lspci" and save the output
2. Add an additional disk controller (the one that didn't work before) to the VM
3. Boot up your VM and run "lspci" again to find the new controller
4. Google the additional controller to see what module it requires
...

---

