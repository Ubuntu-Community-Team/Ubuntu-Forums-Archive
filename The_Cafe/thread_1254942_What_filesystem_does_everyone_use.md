---
title: "What filesystem does everyone use?"
date: 2009-08-31
forum: The Cafe
---

### Post by Grifulkin on 2009-08-31
So, everyone I'm just wondering what filesystems everyone uses?

---

### Post by jrusso2 on 2009-08-31
/ use JFS

/ home I use XFS

---

### Post by kk0sse54 on 2009-08-31
I primarily use UFS2, ZFS, JFS, NTFS

---

### Post by magmon on 2009-08-31
Whatever linux auto formats to lol.

---

### Post by RedSingularity on 2009-08-31
ext3 here.  I love the stability of it.

---

### Post by bl33d on 2009-08-31
> **jrusso2 said:**
> / use jfs

/ home i use xfs

+1

---

### Post by JillSwift on 2009-08-31
This really should have been a multi-choice poll :)

ext3 (/home on everyone, and / on my main machine)
ext4 (/ I use jaunty on my laptop, and ext4 makes for speedy booting)
ntfs (for portability, one external hard drive)
fat32 (for portability, thumb drives)

---

### Post by ad_267 on 2009-08-31
The poll should allow more than one choice. I'm using ext4 for / and ext3 for /home at the moment.

---

### Post by sideaway on 2009-08-31
ext3 for linux partitions, ntfs for windows partitions. I'm boring when it comes to filesystem formats :P

---

### Post by samjh on 2009-08-31
ext4 for most things, except /boot, which is ext3.

I'm a former JFS user though.  I'm guinea-pigging myself with ext4 for the sake of development.

---

### Post by juancarlospaco on 2009-08-31
Theres 2 reiser items on that poll...
:)

---

### Post by oboedad55 on 2009-08-31
Reiserfs on my desktop, ext3 on my laptop.

---

### Post by kk0sse54 on 2009-08-31
> **juancarlospaco said:**
> Theres 2 reiser items on that poll...
:)

Those are two different reiser filesystems ;)

---

### Post by Grifulkin on 2009-08-31
There are also three ext but they are different filesystems.

---

### Post by oboedad55 on 2009-09-01
> **C!oud said:**
> Those are two different reiser filesystems ;)

Reiser 3. It is included with most Linux distributions. I haven't seen reiser 4 as an option anywhere. Anyway, the guy is in jail accused of murdering his wife. If I was to reinstall I'd go with ext3. I've got ext4 on one stock Ubuntu Jaunty installation but I really can't see any speed increase, so I'd go with stability.

---

### Post by gletob on 2009-09-01
/ and /home: EXT4
/boot: EXT2 (I want to be absolutely sure I can modify menu.lst from windows.)

---

### Post by running_rabbit07 on 2009-09-01
> **ad_267 said:**
> the poll should allow more than one choice. I'm using ext4 for / and ext3 for /home at the moment.

+1

---

### Post by Crunchy the Headcrab on 2009-09-01
I'm using ext3 for my boot and ext4 for everything else.

---

### Post by Perfect Storm on 2009-09-01
I use ext4 on them all.
/boot
/
/home

---

### Post by itreius on 2009-09-01
ext4, ntfs and hfs+

---

### Post by The Real Dave on 2009-09-01
I'm really not sure about my choice, I used Ext4 for / and /home, fat32 for XP and my 200Gb Data partition. I'm thinking of changing /home back to ext3 for stability, seeing as I just had a filesystem failure with ext4 on /, complete re-install needed. I'm gonna get / as Ext4 though, because, for my system at least, its quite a speed increase. 

But where I'm stuck is the Data partition. I shouldn't have used FAT, because of its lack of 4+Gb file support. But I've nowhere to put the Data to re format. :(:(

---

### Post by K.L. on 2009-09-01
I use ext4 for / and /home partitions, tested it long enough to switch from ext3. Didn't have any problems with it.

---

### Post by ssri on 2009-09-01
ext3 for work critical stuff on my laptop..

---

### Post by kk0sse54 on 2009-09-01
> **oboedad55 said:**
> Reiser 3. It is included with most Linux distributions. I haven't seen reiser 4 as an option anywhere. 

Reiser 4 is an option in Arch and Gentoo. I don't about anything else though.

---

### Post by Dark Aspect on 2009-09-01
ext3 for now, I'll probably use ext4 with the release of Ubuntu 9.10.

---

### Post by insane_alien on 2009-09-01
ext4, xfs, zfs, ntfs, FAT32, and ext2.

ext4 for / and /home

xfs for a portable 320GB harddrive used on linux only

zfs on my fileserver

ntfs on my windows partition and a 250GB external harddrive that is used on both windows and linux FAT32 on a USB flash drive and ext2 on the usb flash drive running the OS for my fileserver.

---

### Post by Baneblade on 2009-09-01
EXT4 for OS drives
EXT2 for Storage Drives
UFS and EXT2 for servers

---

### Post by Grifulkin on 2009-09-01
Well a lot of people have responded so I might as well say what I have, on my laptop I have reiserfs, I had ext4 but I unplugged the battery one time while it was plugged in and the computer shut off and when I restarted I got an error, I don't really use this for anything so it wasn't a big deal to just reinstall and I wanted to try something different.

Oh also, NTFS on my external hard drive, Ext4 on my dual boot on my desktop.  I didn't set up its own /home partition in retrospect I should have because theoretically any distrohopping I do I could save all my personal stuff, right?

---

### Post by papangul on 2009-09-01
ext2 for /boot
ext3 for /usr
reiserfs for / and /home
xfs for 3 storage partitions

---

### Post by chriskin on 2009-09-01
After reading many contradictory benchmarks etc , is XFS faster or slower than ext4? if it is faster, are there any reasons not to choose it as my karmic filesystem?

---

