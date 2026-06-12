---
title: "Installing Ubuntu server 13.10 and setting up RAID 1 (mirroring)"
date: 2013-12-22
forum: Server Platforms
---

### Post by spmealin on 2013-12-22
Hi all,

For the last couple of days, I've been trying to set up a server with RAID 1.  The hardware is a Dell PowerEdge T20, with three 1TB hard disks.  The boot type is EFI.  I have been following "Advanced Instillation" in the Ubuntu Server Guide ([https://help.ubuntu.com/13.10/serverguide/advanced-installation.html](https://help.ubuntu.com/13.10/serverguide/advanced-installation.html)).

When I get to the partitioning step, my hardware options consist of four devices: /dev/sda (the USB key that I am installing Ubuntu from), /dev/sdb, /dev/sdc, and /dev/sdd, (which are the three hard drives).

Following the guide, I set up identical partitions on the three hard drives (/dev/sdb, /dev/sdc, and /dev/sdd):
Partition 1: Use as = physical volume for RAID, size = 16GB (twice the amount of memory)
Partition 2: Use as = physical volume for RAID, size = remainder of the disk

According to the guide, I should be able to set the "bootable flag" to "on" for the second partition (the root of the file system), however the installer will not let me.

I then configure two software RAID devices.  For my setup, I am using two active devices, and one device is spare:
RAID1 device #0: active devices = /dev/sdb1 and /dev/sdc1, spare devices = /dev/sdd1, use as = swap area
RAID1 device #1: active devices = /dev/sdb2 and /dev/sdc2, spare devices = /dev/sdd2, use as = Ext4 journaling file system, mount point = / - the root file system.

After I go through the rest of the installer, when I restart my machine, I get the error that no boot device was found.  Looking around, I found suggestions that I create a smaller partition on each drive first (about 100 or 200MB) and RAID it together and use it for EFI boot area, however it did not help.

How can I get this to work?

---

### Post by csknight on 2014-01-16
Hi,

I'm looking at getting the Dell PowerEdge T20 to run Ubuntu Server too.
Did you manage to complete the setup?

Thanks!

---

### Post by SeijiSensei on 2014-01-17
In situations like these, I usually create a 512MB ext2 partition on the first drive and mount it as boot.  I usually create similarly-sized partitions on the other drives and use them as backups to /boot.  Then you can RAID the remainder of the drive and not have problems with the BIOS locating the boot sector.

I avoid using RAID during boot and prefer bare-metal partitions for the /boot area.

---

