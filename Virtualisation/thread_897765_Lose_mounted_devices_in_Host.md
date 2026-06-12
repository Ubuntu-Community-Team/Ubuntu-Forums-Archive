---
title: "Lose mounted devices in Host"
date: 2008-08-22
forum: Virtualisation
---

### Post by darco on 2008-08-22
I am running Mint as host and Ibex/KDE Mint as Guest. I am using VMWare Server.
Before I run either vm, Mint shows that I have mounted devices for example, my flash drive, external HDD,,etc.... When I mount the devices in vm, I lose everything in the Host. I have to reboot the Host in order to see the mounted devices again. I am assuming the fstab in the Host is not setup correctly and what command can I use to reload fstab w/o having to reboot?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c64a9779-e91a-4830-b3ef-290ff05a3866 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=31bc0650-b743-40b6-abf3-f42d14d52bcf /home           ext3    relatime        0       2
# /dev/sda3
UUID=62cbce2d-3d0d-40ae-854b-8d28f5a02220 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

thxs
darco

---

