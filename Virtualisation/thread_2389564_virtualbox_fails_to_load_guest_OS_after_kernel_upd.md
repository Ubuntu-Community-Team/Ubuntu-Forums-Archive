---
title: "virtualbox fails to load guest OS after kernel update to 3.13.0-143"
date: 2018-04-18
forum: Virtualisation
---

### Post by knight69 on 2018-04-18
I am running VirtualBox 5.2.8r121009 (latest version) on Ubuntu 14.04.5.  VirtualBox was reliably hosting Windows XP and Windows 7 guest OS's until I updated the the linux kernel version to 3.13.0-143 which happened to be the version that integrated retpoline into the system.  Since then, VirtualBox fails to load either guest OS.  If I fall back to kernel version 3.13.0-139, VirtualBox loads both guest OS's reliably.  This not being a satisfactory solution, I am hoping someone can help me solve the problem.

Running /sbin/vboxconfig in accordance with instructions from VirtualBox's error message yields the following error message.

[I]vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.

[/I]Running dmesg gives the following error message after running '/sbin/vboxconfig'

*[  137.823326] vboxdrv: version magic '3.13.0-144-generic SMP mod_unload modversions ' should be '3.13.0-144-generic SMP mod_unload modversions retpoline '*


Given that retpoline is mentioned in the error message and that the problem was first encountered when ubuntu added retpoline to the OS, I believe the problem is related to the retpoline addition, but I have no idea how to resolve it.

---

### Post by deadflowr on 2018-04-18
*Thread moved to **Virtualization** *

---

### Post by cruzer001 on 2018-04-18
> vboxdrv: version magic '3.13.0-144-generic SMP mod_unload modversions ' should be '3.13.0-144-generic SMP mod_unload modversions retpoline '

I run VirtualBox 5.2.8 and kernel 4.15.0.15-generic in both guest and host without this issue.  Sounds like "modversions retpoline" needs to be ported to your kernel.  I would suggest filing a bug against your kernel.
```

ubuntu-bug linux
```

Its a automated process.  You do need a LaunchPad account.

[https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)

---

### Post by knight69 on 2018-04-18
I am also running VirtualBox 5.1.28r117968 on a different computer with kernel 4.4.0-116 (also incorporatates retpoline) and it's working fine. Initially when I updated the kernel, I got the same problem, but running vboxconfig recompiled VirtualBox and it now runs perfectly.

---

### Post by knight69 on 2018-04-18
Just installed VirtualBox 5.1.10r122088 (latest version according to Oracle) and no change.  Getting exactly the same error message from dmesg.

---

### Post by knight69 on 2018-04-18
updated kernel version to 4.4.0-119.  Same results.

*vboxdrv: version magic '4.4.0-119-generic SMP mod_unload modversions  ' should be '4.4.0-119-generic SMP mod_unload modversions retpoline '*

---

### Post by ajgreeny on 2018-04-18
Do you have the kernel headers packages for your kernel version installed; they are normally installed with the kernel by default but without them you may find that the *vboxdrv* module is not created for your kernel.

I'm currently using kernel 4.4.0-119 in my Xubuntu 16.04 system and running VBox version 5.2.10 without any problems. However I believe that as you are still using *ubuntu 14.04 with the original kernel version, you may need to upgrade to either a newer hardware stack with more recent kernel and xorg packages to get VBox version 5.1 to work properly or upgrade your OS to at least 16.04.

I will try to find the references to this and report back if I have time. Alternatively you could try moving back to VBox version 5.0, just to test my theory, though that version is no longer supported, so is not recommended.

---

### Post by jeremy31 on 2018-04-19
I think gcc needs to be patched to fix the retpoline issue.  Best idea is to file a bug report

---

