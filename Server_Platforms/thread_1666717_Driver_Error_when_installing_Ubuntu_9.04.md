---
title: "Driver Error when installing Ubuntu 9.04"
date: 2011-01-14
forum: Server Platforms
---

### Post by idny on 2011-01-14
Hi,

Been searching for a while now and still need help (sorry for new thread)

Im installing Ubuntu Server 9.04 from a CD, the installer works fine  until i need to get the drivers for my RAID card. (this is asked when  detecting disk on installation)

I put the drivers onto a USB (MSDOS boot diskette)
mounted it by pressing ALT+F2 to get a terminal during the installation.
then copied the files from the USB to /tmp

When I try and run the driver from /tmp i get.

 
> # sh preinst.sh

sh: 2.4: unknown operand
sh: 2.6 unknown operand
The disk you insert is for linux kernel 2.4/2.6
Error! Please change your floppy disk, the installation is under 2.6 Linux Kernel. 

I've tried this on both 10.10, 10.04 installation disks and now 9.04.
The Driver is for 9.04 X86 & X64.

Any ideas?
Thanks

---

### Post by idny on 2011-01-14
bumping for help

---

