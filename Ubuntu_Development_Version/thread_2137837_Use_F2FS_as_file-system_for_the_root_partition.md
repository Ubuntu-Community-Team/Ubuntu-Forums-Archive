---
title: "Use F2FS as file-system for the root partition"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by ekerazha on 2013-04-22
Hi,

I have an Acer Aspire One with a low-end SSD drive which is extremely slow. I'd want to try the new F2FS file-system which is specifically designed for this kind of flash memory drives. The 3.8 kernel should support the F2FS file-system, although I don't know if the Ubuntu kernel has been compiled with F2FS support... however...

I downloaded GParted Live 0.16.0 Beta 2 which includes some F2FS support, I created an EXT2 boot partition (I don't think F2FS is bootable yet) and a F2FS root partition.

Then I tried to install Ubuntu 13.04 Beta 2 but it looks like the Desktop installer doesn't support F2FS. So I tried the Alternative installer (text based) of Lubuntu 13.04 Beta 2 (Lubuntu is the only Ubuntu flavor which still releases the Alternative image) but even the text-mode installer supports F2FS.

Any suggestions? I'd want to install Ubuntu on a F2FS root partition.

Thanks.

--

[SIZE=7]Update[/SIZE]
Sustain the ticket to add F2FS support to the Ubuntu installer: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1261175](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1261175)

---

### Post by dino99 on 2013-04-22
F2FS has been merged into 3.8 kernels  ([http://www.phoronix.com/scan.php?page=news_item&px=MTI1OTU](http://www.phoronix.com/scan.php?page=news_item&px=MTI1OTU))

but using that new 0.16 gparted (still beta, and 0.15 was so buggy) is at your own risk; so be sure to backup your data/settings elsewhere first (on an other device)

[http://askubuntu.com/questions/258329/can-and-how-do-you-install-ubuntu-in-f2fs-filesystem](http://askubuntu.com/questions/258329/can-and-how-do-you-install-ubuntu-in-f2fs-filesystem)

Also watch the f2fs-tools package details.

---

### Post by ekerazha on 2013-04-22
Yes but there are no Ubuntu installers with F2FS support. Also, it looks like there isn't an utility to resize the F2FS file-system (I can't see it in f2fs-tools), so I can't even try to install Ubuntu on an EXT2 partition, shrink it, create a F2FS partition, copy the EXT2 partition content into the F2FS partition, delete the EXT2 partition and extend the F2FS one... because F2FS lacks the resizing tool. Maybe I could try to use a third temporary partition and then use it as /home.

---

### Post by dino99 on 2013-04-22
browse down and watch the latest posts (maybe btrfs is a better choice)
[http://lwn.net/Articles/518988/](http://lwn.net/Articles/518988/)

---

### Post by ekerazha on 2013-04-22
Btrfs is probably better on high-end SSD, while F2FS is specifically designed with the flash memory of mobile devices (smartphones, tablets etc.) in mind, which is similar to the low-end drive I have in my netbook.

---

### Post by ekerazha on 2013-04-22
Some brainstorming (I didn't test it)...

*[Edit: removed... useless...]*

---

### Post by dino99 on 2013-04-22
posting oops

---

### Post by dino99 on 2013-04-22
Hopes you succeed; good luck  :P

... and post your feedback please. (might help some others)

---

### Post by Cheesemill on 2013-04-22
I should think that using debootstrap to install would probably work.

---

### Post by ekerazha on 2013-04-25
So... I tried to install Ubuntu on a EXT4 partition (with a different EXT4 /boot partition), then I booted from the Live CD and I copied the root partition content to an external USB drive (EXT4 formatted), then I formatted the original partition as F2FS and I copied everything back from the USB drive to the F2FS partition. I adjusted the fstab file and I also ran update-grub (chrooting the installed system). It didn't work. I also tried update-initramfs. Maybe I missed something.

---

### Post by anca-emanuel on 2013-05-01
sudo apt-get install f2fs-tools
manually compiled gparted 0.16.1
created partition on /sdb1

Docs: [https://github.com/torvalds/linux/blob/master/Documentation/filesystems/f2fs.txt](https://github.com/torvalds/linux/blob/master/Documentation/filesystems/f2fs.txt)

From [https://bugzilla.redhat.com/show_bug.cgi?id=922966](https://bugzilla.redhat.com/show_bug.cgi?id=922966) :
cat /proc/filesystems
```
nodev    sysfs
nodev    rootfs
nodev    bdev
nodev    proc
nodev    cgroup
nodev    cpuset
nodev    tmpfs
nodev    devtmpfs
nodev    debugfs
nodev    securityfs
nodev    sockfs
nodev    pipefs
nodev    anon_inodefs
nodev    devpts
    ext3
    ext4
nodev    ramfs
nodev    hugetlbfs
    vfat
nodev    ecryptfs
    fuseblk
nodev    fuse
nodev    fusectl
nodev    pstore
nodev    mqueue
    f2fs
```
f2fs module is loaded !


libblkid version is 2.20.1 : [https://launchpad.net/ubuntu/saucy/+package/libblkid1](https://launchpad.net/ubuntu/saucy/+package/libblkid1)
the version needed is 2.23

---

### Post by maestrobwh1 on 2013-06-18
EXT4 still seems to outperform BTRFS from what I can see as far as speed is concerned.  F2FS; my major concern just right now would be a difficulty to repair and/or extract data from a F2FS disk/partition in case recovery was needed; however, it does seem to win over EXT4 right now.   

I have Ubuntu installed an Asus EEEPC 701, 901 & 1201T (don't know what my fascination is with these machines?) and I use EXT4 on all of of them.  The 901 has a REALLY slow SSD but EXT4 works well with no "hiccups."  

I followed this post to increase my ssd performance times by adding options to my /etc/fstab.  Some of the options are only recommended for laptops or machines with a UPC.

[http://blog.loxal.net/2009/04/tuning-ext4-for-performance-with.html](http://blog.loxal.net/2009/04/tuning-ext4-for-performance-with.html)  BE SURE to do a 

```
tune2fs -o journal_data_writeback /dev/sdXY
```

before rebooting or you will get thrown to a busybox promt on the next boot.

Your performance issues should go away as best as possible, but I also understand and identify with your need to experiment with this.  The F2FS looks especially promising with the need to have Ubuntu on an SD card.

---

### Post by ekerazha on 2013-12-27
Sustain the ticket to add F2FS support to the Ubuntu installer: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1261175](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1261175)

---

### Post by vinibali on 2014-08-26
speed up guys :)
[http://ubuntuforums.org/showthread.php?t=2241328](http://ubuntuforums.org/showthread.php?t=2241328)

---

### Post by Elfy on 2014-08-26
closing trusty thread

---

