---
title: "partition type for mdadm arrays"
date: 2009-01-09
forum: Server Platforms
---

### Post by ljwobker on 2009-01-09
I've read in a few places where you're supposed to set the partition type to "fd" -- linux raid -- for mdadm arrays.

However, my ubuntu 8.10 version of parted doesn't seem to want to allow this option, nor can I easily find it mentioned in any of the parted docs.

Questions:

1) is it still necessary to set this to build arrays using mdadm/parted? I've managed to get it up and running without it, so trying to understand if this is historical or if I'm doing something wrong that will bite me later.

2) if this IS necessary, how do I go about changing the filesystem type?

3) purely from curiosity, does "fd" stand for anything, or is this just the assigned hex value for that specific partition type?

thanks...

---

### Post by albinootje on 2009-01-09
> **ljwobker said:**
>  1) is it still necessary to set this to build arrays using mdadm/parted? I've managed to get it up and running without it, so trying to understand if this is historical or if I'm doing something wrong that will bite me later.

2) if this IS necessary, how do I go about changing the filesystem type?


What do you mean with "I've managed to get it up and running" ?
Are you using software RAID already ? 
Or are you using hardware RAID ?

I think this howto is pretty good for answering question 1 and 2 :
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
This is about software RAID.

---

### Post by ljwobker on 2009-01-09
Thanks -- I'll take a read over that.  By "I got it up and running" I guess I mean that I was able to get the raid up and running without ever explicitly defining the partition types -- so either something is setting them correctly, or it doesn't *really* prevent you from running.  

Part of the question was whether having the fs-type set to something other than "fd" would cause problems in the future... everything I read still says you should set the partition type to "fd", but none of the docs say why.

and for anyone who finds this in search, "fd" doesn't stand for anything, it is just the hex code for that particular fs-type.

---

### Post by albinootje on 2009-01-09
> **ljwobker said:**
>  Part of the question was whether having the fs-type set to something other than "fd" would cause problems in the future... everything I read still says you should set the partition type to "fd", but none of the docs say why.

and for anyone who finds this in search, "fd" doesn't stand for anything, it is just the hex code for that particular fs-type.

83 is for a normal Linux partition. 82 for Linux swap. Just like with fd.
It's only meant for programs to easily work with I think.
And it makes sense to e.g. label a Linux swap partition as 82, no ?

---

### Post by fjgaude on 2009-01-09
From my knowledge and user experience I'd say it is not important, now that UUIDs and the like are being used.

The "FD" is hex and has no meaing other than a legion: Auto raid - Linux.

There are several ways the kernel can auto detect and assemble a created array at bootup. I believe the FD was used to be sure that a collection of drives were part of an array. I'm not sure if this is needed anymore.

BTW, such labels have nothig to do with the filesystem type, just the device/partition type.

---

### Post by ljwobker on 2009-01-09
OK.  This is what I had suspected, but wasn't sure.  Given that parted (which seems to be the current partition manager of choice) doesn't even allow type FD to be set, it seems unlikely that it's really all that necessary.

---

### Post by fjgaude on 2009-01-09
I have used **cfdisk** to set partition types beyond what **parted** can do... it's in the repository.

---

### Post by Cracauer on 2009-01-09
I think you mix up the partition type as set in the partition table and the actual type of the filesystem.

As for partition types, you only want to set it to "Linux raid" if you want kernel autodetection of the raid partitions. If you manage them on your own on boot then you set something else, e.g. plain "Linux".

---

### Post by ecosprog on 2009-02-21
Gparted does indeed have an option for setting the partition type. It can be found under the heading of ´flags´. The ´fd´ option is the hex option that is used with the CLI utility fdisk.

Although I haven´t tested it, I suspect that setting the partiton type to ´raid autodetect´ (which is what fd does) enables programs like mdadm to assemble RAID arrays automatically without the need to specify particular partitions.

[This]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID") guide provides a good starting point for software raid.

---

