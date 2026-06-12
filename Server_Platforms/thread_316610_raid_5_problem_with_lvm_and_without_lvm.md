---
title: "raid 5 problem with lvm and without lvm"
date: 2006-12-11
forum: Server Platforms
---

### Post by jimx on 2006-12-11
Hello,
I'm trying to install Ubuntu Server 6.10 Edgy Eft on a raid 5 array on LVM with 4 disks 4x250GB.I have done a boot partition on md0 out of the lvm and the rest space on md1 with mount points for root,swap,home,opt in the lvm,so the output is like that:

/boot 200MB on md0
/root 10GB on md1
/home 20GB on md1
/swap 4GB on md1
/opt on md1 the rest space of the disks.

Everything goes well but when it comes to install the boot loader
it chooses lilo but stops before it installs it with an exit error:
Running "/sbin/lilo" failed with error code "1".
I tried again and put grub as the boot loader but grub freezes at 50% of the installation and i have to reset the PC.
I also tried to set the raid 5 array without including LVM but the result was the same,except that grub doesn't freeze but it stops with a FATAL ERROR.

I posted this thread and to "Installation & Upgrades" forum but i didn't get any help.

My hardware is:
MSI P965 Platinum,Core 2 Duo 2.13Ghz,2GB Ram,4X250GB WD sata2

---

### Post by abadr on 2007-01-26
Is md0 RAID 1 or RAID 5? /boot can only be on a RAID 1.

---

### Post by uiteoi on 2007-03-06
I had the same problem, fixed it by switching /boot to RAID1, don't use LVM either for /boot.

The reason is that GRUB and LILO do not have RAID or LVM drivers. A RAID1 partition looks like   non-RAID as long as one only reads. So RAID1 works with boot loaders unless they attempt to write on /boot.

---

