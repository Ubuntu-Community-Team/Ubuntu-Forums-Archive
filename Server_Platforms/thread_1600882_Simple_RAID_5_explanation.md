---
title: "Simple RAID 5 explanation"
date: 2010-10-19
forum: Server Platforms
---

### Post by kevinfishburne on 2010-10-19
I've spent the last few days reading countless how-to's about setting up various software RAID configurations, and while normally I can figure things out on my own or with some online help this time I'm having a real problem.

I have a server with six empty terabyte hard drives that I'd like to configure as RAID 5. The "Disk Utility" is really old and buggy so I'm using the Ubuntu 10.04.1 Server LiveCD instead.

What I'm missing is a general description (not step-by-step instructions) of the process of creating multiple partitions on a RAID 5 array. Ideally I'd like md0p1 to be swap, md0p2 to be root and md0p3 to be data/home.

So far the descriptions I've read go something like:

1) Create partitions on all drives to be in the array.
2) Set the RAID flag on each drive.
3) Create the array.
4) Create partitions on the array itself.

Is this possible via the Server LiveCD GUI?

Is step 1 necessary, and why?

Is it possible to create multiple partitions on the array and do I need to do that before or after it's created?

Will I be forced to resize the data/home partition after the array's creation to fill the rest of the array?

As you can see I'm a little lost on the logic of how RAID 5 is constructed and how it can be partitioned for use. Any basic explanation would be greatly appreciated.

---

### Post by arrrghhh on 2010-10-19
Never used RAID before, but I understand some concepts.

[SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) - that's the official Ubuntu community doc, hopefully that will help.

In respect to your question about the LiveCD... the server edition doesn't have a 'live' environment, you must be using the desktop version ;)

I don't know how well it would work, but I imagine you could do it - just may need to install a few things like mdadm.

---

### Post by Vegan on 2010-10-19
Using a OS based RAID is useless.

[http://www.windows-it.tk/papers/raid.php]("http://www.windows-it.tk/papers/raid.php")

---

### Post by arrrghhh on 2010-10-19
> **Vegan said:**
> Using a OS based RAID is useless.

[http://www.windows-it.tk/papers/raid.php]("http://www.windows-it.tk/papers/raid.php")

Dude... if you only run one OS and don't have the cash for hardware RAID, software RAID is perfectly fine as an inexpensive solution to get redundancy...

You should make a separate disk for system tho, I would agree with that article in that sense.

---

### Post by SeijiSensei on 2010-10-19
> **kevinfishburne said:**
> 
1) Create partitions on all drives to be in the array.
2) Set the RAID flag on each drive.
3) Create the array.
4) Create partitions on the array itself.

Is step 1 necessary, and why?

Yes and no.  I've usually decided on the partition sizes in advance, then used fdisk to create them on the hard drives and mark them with the "Linux Autodetect RAID" partition type, "fd".  Alternatively, you could create a single partition on each drive, RAID them together, then divide them up using [LVM]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem").  You'd have more flexibility that way, but I don't think it really matters much in your case.

You'll need to put /boot someplace outside the array to insure that the kernel can load before the array is started.  I'm not sure it matters if swap is on an array; you can just allocate 1 GB on each of the six drives to swap and concatenate them all together by listing them in /etc/fstab.  As for root (/) and /home, something like 20GB maximum for the former and the remainder for the latter would be fine.  With RAID5 you'd have an effective 100GB for / which is more than you'll ever use.

> Is it possible to create multiple partitions on the array and do I need to do that before or after it's created?

No, software RAID combines physical partitions.  If you want a logical partitioner than runs above the RAID device, you'll need to use LVM.

> Will I be forced to resize the data/home partition after the array's creation to fill the rest of the array?

If you create the partitions in advance, you can control how they are layed out.  You could leave a block of free space on the end of each drive for later applications.  Just make sure that the starting and ending cylinders are the same for each partition on every device.

If the LiveCD includes the "gparted" utility, I'd suggest using that to configure the hard drives.

---

### Post by doogy2004 on 2010-10-19
See my signature for instructions on RAID 5.

> **kevinfishburne said:**
> I have a server with six empty terabyte hard drives that I'd like to configure as RAID 5.

With disks that large you may want to look into ZFS.

check out these articles:
[http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162](http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162)
[http://www.zdnet.com/blog/storage/why-raid-6-stops-working-in-2019/805](http://www.zdnet.com/blog/storage/why-raid-6-stops-working-in-2019/805)

---

### Post by psusi on 2010-10-19
> **Vegan said:**
> Using a OS based RAID is useless.

[http://www.windows-it.tk/papers/raid.php]("http://www.windows-it.tk/papers/raid.php")

That statement is useless.  Also the article you linked is wrong.  WINDOWS does not have the ability to boot from a software raid, but Linux does so just fine.

---

### Post by WinstonChurchill on 2010-10-19
> **Vegan said:**
> Using a OS based RAID is useless.

[http://www.windows-it.tk/papers/raid.php](http://www.windows-it.tk/papers/raid.php)
Anything Windows-based is useless....

Linux mdraid is fantastic - I have 3 500GB's in a RAID5 on my desktop; I get the same random-write speeds as a single drive (~100 MB/s), and more than twice the read rate (~250MB/s). I definitely recommend it.

To the OP: I have no experience with ZFS; however, if you use ext4, be sure you use the RAID-specific options (stride, stripe-width and resize (although obviously you'd have to set that one yourself)) that mke2fs has - the installation CD, as of 10.04 anyway, did not set these options correctly, and they make a very noticeable difference in performance. I had to create md0 "manually" with a live CD and then run the installer.

Also, this might seem obvious, but since the array must be bootable, you have to have MBR's on the hard disks and RAID the partitions, even if it's just one big partition on each disk - you can't just RAID them at the device level. I didn't realize that the first time...

---

### Post by kevinfishburne on 2010-10-20
Thanks for the excellent replies, and I must say that "Anything Windows-based is useless...." is one of the funniest quotes I've seen in the forums. Like the Metallica song, sad but true.

It looks like there's only one thing left that I'm not clear on, so to summarize what I am clear on so far:

There are two ways to create a software RAID. One (mdadm only) assembles the array from preexisting partitions on a set of disks, preserving their data, and the other method (mdadm+lvm) creates logical volumes/partitions on top of an array created from (in my case) whole disk partitions.

The mdadm+lvm method I successfully implemented last night using the 10.04.1 Server textual GUI, including booting the OS to the array, but what I'm not clear on is how the first method works.

It's my understanding that RAID takes 2+ physical disks and presents them to the OS as a single logical disk, which may be partitioned without regard to the underlying physical disk size boundaries. That preconception makes the idea of creating the partitions -before- creating the array confusing, as I don't see how they'd be combined/extended after the array is created to take advantage of the additional space.

For example is it possible without using lvm to create a six-disk RAID 5 with the "data" or third partition spanning all space not occupied by the swap and root partitions? Prior to creating the array, which one of these partition schemes would be appropriate, if any:

Disk 1 - swap(12 GB), root(24 GB), data(964 GB)
Disk 2 - data(1000 GB)
Disk 3 - data(1000 GB)
Disk 4 - data(1000 GB)
Disk 5 - data(1000 GB)
Disk 6 - data(1000 GB)

or

Disk 1 - swap(12 GB), root(24 GB), data(964 GB)
Disk 2 - swap(12 GB), root(24 GB), data(964 GB)
Disk 3 - swap(12 GB), root(24 GB), data(964 GB)
Disk 4 - swap(12 GB), root(24 GB), data(964 GB)
Disk 5 - swap(12 GB), root(24 GB), data(964 GB)
Disk 6 - swap(12 GB), root(24 GB), data(964 GB)

or

Disk 1 - swap(2 GB), root(4 GB), data(994 GB)
Disk 2 - swap(2 GB), root(4 GB), data(994 GB)
Disk 3 - swap(2 GB), root(4 GB), data(994 GB)
Disk 4 - swap(2 GB), root(4 GB), data(994 GB)
Disk 5 - swap(2 GB), root(4 GB), data(994 GB)
Disk 6 - swap(2 GB), root(4 GB), data(994 GB)

In any scenario I don't see how the resulting array would logically treat the original partitions, or how it would know to combine the six "data" partitions into a single logical partition.

I thank the Ubuntu gods that it seems to be working now, but this may be one of my moments where I'm just too thick headed to grasp the concept.

---

### Post by psusi on 2010-10-20
You use partitions on the disk as the raid elements rather than the raw disk so that you still have a partition table that shows that the disk is in use as part of a raid array, rather than appearing to be an unformatted disk full of random data.  It also must have a partition table to be bootable.

The array itself can then be split up either using lvm or a traditional partition table INSIDE the array.

---

