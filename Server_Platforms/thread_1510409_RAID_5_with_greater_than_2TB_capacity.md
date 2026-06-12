---
title: "RAID 5 with greater than 2TB capacity"
date: 2010-06-15
forum: Server Platforms
---

### Post by Jeffa on 2010-06-15
Hello Community. 

I'm wondering if you might be able to help me out with this. 

I've recently completed a fresh install of 10.04 on a home file server and upgraded the hard drives in my storage array. My PREVIOUS hardware was: 

Old version of Ubuntu (I forget which one exactly, but I know I had missed a few upgrade cycles)
3X 500 GB Seagate Baracuda's (for the array)
Areca 1220 Hardware RAID controller
Intel Core 2 Duo 6600
320 GB Seagate for the boot drive

I was running that hardware for about five years or so and it was rock solid. After the upgrade the hardware specs are:

Ubuntu 10.04
Areca 1220 hardware RAID controller
4x 1000GB Samsung
Intel Core 2 Duo 6600
320 GB Seagate for the boot drive. 

The fresh install of Ubuntu 10.04 went remarkably well. The drivers for that raid controller are in the kernel, which is great. I was able to access the old array after upgrading Ubuntu. Now I am trying to create a new array with the four 1000 GB drives in a RAID 5. Obviously that gives a maximum storage capacity of 3 TB, greater than the 2 TB threshold that seems to be so important. I've been doing some digging and here is where my questions start:

it appears as though gparted doesn't support file partitions greater than 2 TB, correct?

it also doesn't seem as though parted supports ext3 or ext4, is that correct? 

If this is the case, how do I create a partition with ext4 that is greater than 2 TB? 

I can see the array volume in gparted (which is a relief) but it lists the size as 2.73 TiB, which I find curious because that is over 2 TB, but not the full capacity of the volume. I can also get to the volume in parted. But I see in the [parted documentation]("http://www.gnu.org/software/parted/manual/parted.html#mkpartfs") that using the makepartfs command is discouraged and instead, one should use the command mkpart to create an empty partition, and then use external tools like mke2fs (8) to create the filesystem. 

Sooooo, that is a little long and rambling, but I'm not exactly sure how to proceed from here. What does the community think is the best course of action to create a partition of 3TB in ext4? Then I need to change fdisk to automatically mount the array at every log in, right? 

Many thanks, 

-Jeff

---

### Post by psusi on 2010-06-15
The 2TB limit is the maximum size an an msdos partition table can handle.  Typically you partition the physical disks, then combine those partitions into the raid device.  Since the individual disks are less than 2tb, you don't have anything to worry about.  Unless you wanted to partition up the raid device.  If you want to do that, then you either have to use a gpt partition label, or LVM.

And 2.73 TB is the correct size.  Hard drive manufacturers always overstate the size of their disks by using powers of 1000 instead of 1024, so the disk is 1,000,000,000,000 bytes, which is only 931 GB, x3 since you have a 4 disk raid 5 = 2.79 TB.

---

### Post by CharlesA on 2010-06-15
What I did was just greate the array using the software that came with the RAID controller, then formatted the single "device" with gparted using a GUID partition.

Maybe I did it differently, but I only had to create 1 volume, since the OS saw it as one huge drive, no messing around with partitioning the individual drives.

But anyway, 2.73TB is the correct size for a 3TB array.. rounded bits and all that.

---

### Post by Jeffa on 2010-06-15
@CharlesA, is your volume larger than 2tb? When I try and use gparted I get the following error:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160597&stc=1&d=1276652325http://ubuntuforums.org/attachment.php?attachmentid=160597&stc=1&d=1276652325[/IMG]

Many Thanks.

---

### Post by CharlesA on 2010-06-15
Yeah. I used a gparted livecd to create the partition.

This is what fdisk says about it:

```
Disk /dev/sdb: 4000.6 GB, 4000627818496 bytes
255 heads, 63 sectors/track, 486381 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483647+  ee  GPT

```

Are you using gparted that comes with Ubuntu?

You have to create a GUID Partition table, not a MSDOS partition table.

If you go to Device > Create Partition Table > Advanced > Select new partition table type > gpt

It should work.

---

### Post by Jeffa on 2010-06-18
Thanks CharlesA, that appears to have done the trick. Although it also appears as though I have a bad drive in the array, so I can't finish this until I replace that drive. Will post the results when I get the new drive.

---

### Post by CharlesA on 2010-06-18
Ouch. Bad drives suck big time.

Best of luck. :)

---

### Post by ian dobson on 2010-06-19
Hi,

You don't need to partition a drive/block device to be able to format it:-

```

fdisk -l
Disk /dev/md1: 5941.2 GB, 5941150875648 bytes
2 heads, 4 sectors/track, 1450476288 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 1048576 bytes / 3145728 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

mount:
/dev/md1 on /data type ext4 (rw,noatime,nodiratime,data=writeback,nobh,barrier=0,commit=15)
```

Regards
Ian Dobson

---

### Post by Jeffa on 2010-07-11
OK, got the new drive installed and all seems to be working. I had a few problems with mounting and sharing [as described here]("http://ubuntuforums.org/showthread.php?t=1528486"), but that has also been resolved and now everything appears to be in working order! woohoo!

Thanks community!

---

