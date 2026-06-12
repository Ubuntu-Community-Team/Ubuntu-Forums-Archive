---
title: "VirtualBox Module Modprobe Problem"
date: 2008-03-26
forum: Virtualisation
---

### Post by strikenowhere on 2008-03-26
Hello everyone,

I am currently in the process of attempting to get VirtualBox up and running on a Linux machine running 2.6.15-26-server kernel.  After installing the linux-source-2.6.15, linux-headers-2.6.15-26-server, and linux-image-2.6.15-26-server packages, I retrieved the latest version of the VirtualBox .deb package (v1.5.6) from VirtualBox's download site (added the location into my /etc/apt/sources.list).  When I run "/etc/init.d/vboxdrv setup", I am able to compile the module, but I receive an error message stating that "Modprobe of vboxdrv failed.  Please use 'dmesg' to find out why." and upon checking out the log I find these two error lines:

> [46014039.470000] vboxdrv: disagrees about version of symbol boot_cpu_data
[46014039.470000] vboxdrv: Unknown symbol boot_cpu_data

I have racking my brains trying to figure out what the heck is going on!  In another of my posts, I had asked what exactly that error message meant, and the response was that boot_cpu_data is a kernel symbol and that

> "The kernel module you're using is incompatible with your kernel. To be assured of compatibility, you need to recompile it from source against your own kernel, and do so again, whenever you install a new kernel in the future."

Now, I am at a loss for what exactly is going on...I had actually run into this problem about 6 months ago when I was installing VirtualBox (v1.5.0 I believe) onto a different machine, and the fix turned out to be that I just needed to install the correct linux-image package.  I did that for this machine as well, but I still receive this error!  Does anyone at all have any suggestions?

Thank you for your time,
Greg

---

