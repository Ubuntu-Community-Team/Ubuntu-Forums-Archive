---
title: "[SOLVED] VirtualBox kernel driver suddenly doesn't load at startup"
date: 2008-10-09
forum: Virtualisation
---

### Post by jespdj on 2008-10-09
I am running VirtualBox 2.0.2 on 64-bit Ubuntu 8.04:
```
$ uname -a
Linux jesper-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```
Suddenly, the VirtualBox kernel driver (vboxdrv) doesn't seem to load at boot. When I start VirtualBox from a terminal, I get this message:
> WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.24-19-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.

Ok, so I execute the command that the message mentions. Then I get:
```
$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                                                                                                   *  done.
 * Removing old VirtualBox kernel module                                                                                                               *  done.
 * Recompiling VirtualBox kernel module                                                                                                                *  done.
 * Starting VirtualBox kernel module                                                                                                                  
 * Cannot change owner vboxusers for device /dev/vboxdrv
```
With lsmod I see that vboxdrv is still not loaded.

The strange thing is that I can load it manually:
```
sudo modprobe vboxdrv
```
and then it works normally.

What could be the reason that the module doesn't load automatically anymore? I didn't change anything to the configuration of my computer. How do I get it to load automatically again?

---

### Post by jespdj on 2008-10-09
I reinstalled VirtualBox and now it works again. Still don't know why this was happening.

---

