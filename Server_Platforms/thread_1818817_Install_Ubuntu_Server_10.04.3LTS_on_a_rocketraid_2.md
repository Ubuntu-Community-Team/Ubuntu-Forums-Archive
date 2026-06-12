---
title: "Install Ubuntu Server 10.04.3LTS on a rocketraid 26xx"
date: 2011-08-05
forum: Server Platforms
---

### Post by Brain_Damage on 2011-08-05
Hi all,

I'm struggling to install Ubuntu Server 10.04.3 on my brand new Shuttle.  The main problem is my storage controller card (RAID) a Highpoint rocketraid 2640x4.  I cannot install directly to the RAID volume I created: install does not see it.

From there, I read this manual on their website: [COLOR=RoyalBlue][Manual]("http://www.highpoint-tech.cn/BIOS_Driver/rr26xx/2640X1-2640X4-2642/Linux/Install_Ubuntu_RR2640_2642.pdf")[/COLOR]

At step 4.3, when I run preinst.sh, I have an error:
> cp: cannot stat /../rr26xxdriver file.ko
Error loading driverAt this point, the driver that is on the USB diskette (!!!) is for kernel 2.6.32-21-generic but the kernel loaded for the installation (uname -r) is 2.6.32-28-genericpae.
Other thing I tried is the tutorial here: [COLOR=RoyalBlue][Tutorial]("http://www.3dinfluence.com/blog/installing-ubuntu-server-unsupported-raid-controller")[/COLOR]

Following this tuto, I'm able to build a .ko file (freshly installed the same version on a SATA disk) to insert the storage controller driver into the installation kernel. When I try to insmod or modprobe the rr26xx.ko file in the installation it tells me:
> insmod error -1 incorrect module formatWHich I suspect comes from a difference of kernel version from installed version vs. kernel loaded during installation (.28 during install, .33 after install)
Seeing this, I tried to install Ubuntu Server 10.04.3 without network (so it doesn't install a downloaded kernel more recent than the one loaded during installation), but installation wouldn't let me install if no network is present.

At first I installed the server onto an USB key, then loaded drivers then I was able to use the RAID array. It's not my first choice because performances are quite low.

Anyone have any insight? I'd like to install directly on the RAID array... 

Thanks!

Jerome

P.S. I tried 11.04 as well with no avail.

edit: I also tried to boot on a live CD, build driver there, then insert into installation, but same problem arise, kernel is .33 instead of .28...

---

