---
title: "Can not install Grub on sda"
date: 2018-11-18
forum: Server Platforms
---

### Post by bambamm on 2018-11-18
I am trying to install Ubuntu onto a server with RAID1.
I get through the install and come to the point to where I need to install grub but it gives the following error.

```
[FONT=Arial]root@ubuntu:/# grub-install /dev/sda[/FONT]
[FONT=Arial]Installing for i386-pc platform.[/FONT]
[FONT=Arial]grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.[/FONT]
[FONT=Arial]grub-install: error: embedding is not possible, but this is required for RAID and LVM install.[/FONT]
[FONT=Arial]root@ubuntu:/# [/FONT]
```

I am using the following steps to install RAID1 by using Terminal mode via Test Ubuntu.

```
sudo –s
apt install mdadm
ls  –l /dev/sd*
fdisk /dev/sda
m
n
w
fdisk /dev/sdb
n
w
ls  –l /dev/sd*
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
ubiquity –b

Choose "Language"
Choose “Keyboard Layout”
Choose “Download Updates” if you want
Choose “Something Else”
Right click on /dev/md0
Create “New Partition Table”
Right click the “Free Space”
Choose “Add”
Choose the size of the drive you want, I maxed it out
Type for the new partition: “Primary”
Location for the new partition: “Beginning of this space”
Use as: “Ext4 journaling file system”
Mount point /
Choose “Ok”
Choose “Install Now”
Click Continue if you get a pop-up
Choose your country
Enter your personal info
Click “Continue Testing” after everything is installed

Go back to “Terminal”

df –h
mount --bind  /dev /target/dev
mount --bind  /sys  /target/sys
mount --bind  /proc /target/proc
cp /etc/resolv.conf /target/etc/resolv.conf
chroot /target/
apt install mdadm

grub-install  /dev/sda
grub-install  /dev/sdb

exit
reboot

Go back to the “Terminal”

sudo -s
apt install gnome-disk-utility
Chose “Yes” if asked

```

---

### Post by oldfred on 2018-11-18
I do not really know server installer.

But with gpt partitioning grub need a 1 or 2MB unformatted partition with the bios_grub flag for BIOS boot and install of grub to gpt's protective MBR.
If using gdisk then the partition code is ef02. 
Usually first partition, but must be within first 2TB  if large drive.

---

### Post by darkod on 2018-11-19
Very weird proces to partitio nand create mdadm array. it got me confused honestly.

Please port the output of:
```
sudo parted -l (that's small L)
```

PS. The messages mention GPT disks but you are using fdisk to partition. fdisk is not for GPT, only for MSDOS disks...

---

### Post by oldfred on 2018-11-19
@darko
The new version of fdisk now does support gpt partitioning. So it now depends, if 16.04 fdisk does not support gpt, but if 18.04 it now does.

from 
man fdisk
>        fdisk  is a dialog-driven program for creation and manipulation of par&#8208;
       tition tables.  It understands GPT, MBR, Sun,  SGI  and  BSD  partition
       tables.


---

### Post by darkod on 2018-11-19
Ahh, thanks for that. But I still consider fdisk very limited for partitioning compared to parted. In parted you can change the units of display, it clearly shows if the disk is msdos or gpt, etc...

Anyway, the OP problem seems to be the missing bios_grub partition. he can create it with any tool he prefers, as long as it is created.

---

### Post by bambamm on 2018-11-19
> **darkod said:**
> Anyway, the OP problem seems to be the missing bios_grub partition. he can create it with any tool he prefers, as long as it is created.

So how should I create it? I just found this tutorial on YouTube. I have two 2Tb HDDs I want in a RAID1 array.

---

### Post by dbergst on 2018-11-19
It sounds like you allocated the entire RAID1 array to the / partition.  Therefore it would make sense that you would install grub to /dev/md0, i.e.:

[FONT=Arial]# grub-install /dev/md0[/FONT]

---

### Post by bambamm on 2018-11-20
I tried to install @md0 but got an error.
```

root@ubuntu:/# grub-install /dev/md0
Installing for i386-pc platform.
grub-install: error: diskfilter writes are not supported.
root@ubuntu:/#
```

---

