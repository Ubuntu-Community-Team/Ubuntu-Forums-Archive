---
title: "Filesystem compatible with Ubuntu AND Solaris?"
date: 2009-11-21
forum: Server Platforms
---

### Post by fosheezy on 2009-11-21
I've got a box I built last year with opensolaris. I am ready to wipe it and move to Ubuntu, and I'm buying 3 1Tb hard drives to copy the data onto. Currently the data is in a 4Tb ZFS pool, which I don't want to worry about trying to get Ubuntu to read.

Is there a Filesystem (JFS, UFS, ext3/4, etc) that I can format those drives with to copy the data over to (from solaris), wipe solaris, install ubuntu and setup the 4Tb raid drive (with the old drives), and copy the data back over (to ubuntu)? I need these 3 drives to be read/write by both OS's.

Just to clarify the picture:
-currently: 4 x 1.5Tb HDDs RAIDz1 (running solaris)
-about to have: 3 x 1 Tb HDDs, the 2Tb of data on the ZFS pool will be copied onto these to be moved back to ubuntu.

I am going to put the new 3 HDDs on the same MB (it has 10 SATA ports) to make copying as fast as possible. I'd like to have them in a RAID5 but I have a feeling this would not work out between OS's. I can just copy stuff over to each individual drive.

---

### Post by scorp123 on 2009-11-21
> **fosheezy said:**
>  which I don't want to worry about trying to get Ubuntu to read.  Linux can read and write ZFS via "zfs-fuse".

My **/etc/apt/sources.list.d/zfs-fuse.list** file looks like this:
```
#
# http://tech.xerces.com/zfs-part-3-linux-edition.geek
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 17F547C39C5C4071E254D0A7313D312748A22A95
#
deb http://ppa.launchpad.net/brcha/ubuntu jaunty main
deb-src http://ppa.launchpad.net/brcha/ubuntu jaunty main

```

If you have Ubuntu 9.10 simply replace the keyword "*jaunty*" with "*karmic*" in above lines. Once you have the "**zfs-fuse**" package installed all the "**zfs***" commands are available, e.g. "**zfs import**" should work.

> **fosheezy said:**
>  Is there a Filesystem (JFS, UFS, ext3/4, etc) that I can format those drives with to copy the data over to (from solaris), wipe solaris, install ubuntu and setup the 4Tb raid drive (with the old drives), and copy the data back over (to ubuntu)? I need these 3 drives to be read/write by both OS's.  The problem here is Solaris. It only supports UFS, ZFS and Microsoft FAT. At least officially.

This extremely old thread from 2005 suggests that Linux back then could read UFS:
[http://forums.sun.com/thread.jspa?forumID=864&threadID=5088640](http://forums.sun.com/thread.jspa?forumID=864&threadID=5088640)

So I'd assume that this is still the case. So UFS is another option you could consider.

And Google gave me this link:

"(9.24) Can I access Linux (ext2/ext3) partitions from Solaris?"
[http://www.sun.drydog.com/faq/9.html#s9.24](http://www.sun.drydog.com/faq/9.html#s9.24)

The answer is: "Yes." You will need a software package for that. Instructions are on that link above. So depending on the level of support you could probably try and mount Ext2/Ext3 partitions from Solaris and have it copy the data away ... ?

---

### Post by fosheezy on 2009-11-21
wow thanks for that, I hadnt realized the it was that easy to get Ubuntu to see the ZFS pool.

Considering that, How does this sound:
(i have a dedicated boot hard drive)

1) install Ubuntu on the boot drive
2) install the package to use ZFS
3) setup (mdadm) the new 3 disc RAID5 set
4) copy data over to this RAID set from the ZFS pool
5) be sure data is there
6) wipe the ZFS pool, create RAID5 array, copy data back over

I don't want to use ZFS long-term. I'd rather just have a RAID array in Ubuntu.

Thanks again

---

### Post by karlson on 2009-11-21
> **fosheezy said:**
> I've got a box I built last year with opensolaris. I am ready to wipe it and move to Ubuntu, and I'm buying 3 1Tb hard drives to copy the data onto. Currently the data is in a 4Tb ZFS pool, which I don't want to worry about trying to get Ubuntu to read.

Is there a Filesystem (JFS, UFS, ext3/4, etc) that I can format those drives with to copy the data over to (from solaris), wipe solaris, install ubuntu and setup the 4Tb raid drive (with the old drives), and copy the data back over (to ubuntu)? I need these 3 drives to be read/write by both OS's.

Just to clarify the picture:
-currently: 4 x 1.5Tb HDDs RAIDz1 (running solaris)
-about to have: 3 x 1 Tb HDDs, the 2Tb of data on the ZFS pool will be copied onto these to be moved back to ubuntu.

I am going to put the new 3 HDDs on the same MB (it has 10 SATA ports) to make copying as fast as possible. I'd like to have them in a RAID5 but I have a feeling this would not work out between OS's. I can just copy stuff over to each individual drive.

As far as I know that Solaris' UFS is supported for read under linux the other one is FAT

---

### Post by fosheezy on 2009-12-05
does anyone have any good how-tos on formatting a disk as UFS in Solaris? or BSD? I'd prefer a livecd so i don't have to install it onto anything for now.

---

### Post by Lars Noodén on 2009-12-07
> **fosheezy said:**
> does anyone have any good how-tos on formatting a disk as UFS in Solaris? or BSD? I'd prefer a livecd so i don't have to install it onto anything for now.

Well the package ufsutils should in theory allow the creation of UFS filesystems.  However, it seems that Ubuntu can't really do anything with UFS yet:

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/268665](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/268665)

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/181452](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/181452)

I don't have any Solaris or OpenSolaris systems handy at the moment to test anything.  However, it does look like you can use EXT2 if you install the FSWpart and FSWfsmisc packages on Solaris:

[http://unixsadm.blogspot.com/2007/11/ext2-filesystem-for-linux-and-solaris.html](http://unixsadm.blogspot.com/2007/11/ext2-filesystem-for-linux-and-solaris.html)

EXT2 is usable by a fairly wide range of systems, but not always as default.

---

