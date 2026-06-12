---
title: "Issue with Freenas running in Virtualbox"
date: 2009-04-21
forum: Virtualisation
---

### Post by thevoicesdoneit on 2009-04-21
Hi,

I have a persistent (repeatable) issue running Freenas in Virtualbox on Ubuntu.

I have two, spare 160GB IDE drives (let's call them IDE1 and IDE2). I have partitioned/formatted these in Windows to be entirely NTFS.

I've then booted into Ubuntu, done a blkid etc, then mounted them via fstab via something like:
"UUID=123 	/media/NTFS153	ntfs	defaults,locale-en_GB.UTF-8 0 1"

OK, so I then set up a Vbox virtual machine that has 3 virtual HDDs. 

The first virtual HDD (128MB) resides on IDE1 and pretends to be for the Freenas installation.

The second virtual HDD (90GB) resides on IDE1.

The third virtual HDD (90GB) resides on IDE2.

I then install Freenas onto my virtual machine and set up the interfaces etc. I can connect to it/configure it etc without problems.

I then followed the Freenas documentation on setting up software RAID. I assigned both 90GB "drives" to a software RAID1 array and formatted it etc for UFS as per the instructions. I then mount this "virtual raid1 array" and can access it via the SAMBA CIFS setup I have made in Freenas.

OK, so far so good. Here is where the problems start.

The Freenas virtual server will run fine for a while then the RAID array will get reported as degraded and I will get a lot of disk thrashing in Ubuntu. If I check my mounts, I see things like:

ls -la
drwxrwxrwx  1 root root 4096 2009-04-21 19:36 NTFS150
d?????????  ? ?    ?       ?                ? NTFS153

If I then fdisk -l, fdisk complains that it cannot read the drives that are connected:

Also, sudo fdisk /dev/sda returns:
"Unable to read /dev/sda"

So, the two IDE drives that were being used have suddenly disappeared for no good reason.

Also, if I use gparted, the two IDE drives have actually disappeared(!) and if I try to remount (after unmounting), I get:

sudo mount -a
ntfs-3g: Failed to access volume '/dev/disk/by-uuid/071FF0121FCA1045': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
ntfs-3g: Failed to access volume '/dev/disk/by-uuid/0A9887815215C5A8': No such file or directory

Very worrying(!)

This is repeatable now although I did have slightly different behaviour before where fdisk would report that my IDE drive partitions were GPT (Id 0xee) when gparted reported them as being NTFS. Freenas just happens to use GPT/UFS for it's file system (as far as I know) so it's as though something sees the RAID array residing inside a virtual disk as the actual disk format and gets very confused.

I'm not suggesting that this is a problem particular to Ubuntu but it does consistently get confused with this setup and I don't see why it should be the case.

I've noticed a few other posts reporting oddities with partitions so is this an actual bug ?

Rgds
V

---

### Post by thevoicesdoneit on 2009-04-21
Why was this moved? 

It's not a virtualisation problem - it's a problem with Ubuntu (Linux, fdisk, whatever) getting confused with partitions that happen to have virtual drives on them. 

Having RAID1 on virtual drives on NTFS partitions causes a problem that Ubuntu cannot deal with.

---

