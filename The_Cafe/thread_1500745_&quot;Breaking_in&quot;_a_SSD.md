---
title: "&quot;Breaking in&quot; a SSD?"
date: 2010-06-03
forum: The Cafe
---

### Post by 98cwitr on 2010-06-03
So I was afraid I had gotten a bad one. For the first few days my SSD got slower and slower, about 3MB avg per day and then leveled out. Is it possible for an MLC device to get slower and then stop slowing down?

---

### Post by sydbat on 2010-06-03
> **98cwitr said:**
> So I was afraid I had gotten a bad one. For the first few days my SSD got slower and slower, about 3MB avg per day and then leveled out. Is it possible for an MLC device to get slower and then be stop slowing down?Maybe it's a file system issue. How have you formatted it?

---

### Post by 98cwitr on 2010-06-03
ext4

---

### Post by cascade9 on 2010-06-03
It could be an alignment issue- 

[http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)

---

### Post by 98cwitr on 2010-06-03
ill check this with parted when I get home

---

### Post by 98cwitr on 2010-06-03
um...(512*2) != 1049k so does that mean my drive is not aligned


brett@brett-desktop:~$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Model: ATA Mushkin MKNSSDCL (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  57.5GB  57.5GB  primary   ext4            boot
 2      57.5GB  60.0GB  2497MB  extended
 5      57.5GB  60.0GB  2497MB  logical   linux-swap(v1)



when I look at the partition with gparted, the first sector starts at 2048 and through 112351231

---

### Post by andrewabc on 2010-06-03
You have Mushkin 60GB SSD?
So it's sandforce controller.

When you say 3mb/s is that read or write?
Are you constantly benchmarking it (specifically write benchmarks)? Don't do that as it slows it down.

Your alignment looks ok. Read: [Partition alignment for OCZ Vertex in Linux](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)

Go to verify result section to see if similar to what they have.

> Number Start End Size Type File system Flags
1 1049kB 57.5GB 57.5GB primary ext4 boot
The start of 1049 looks wrong. Shouldn't it be 1024? I think that is your problem. Although odd that gparted says 2048 is start position. Still no confirmation from anyone whether 10.04 aligns SSD properly by default.

---

### Post by Shining Arcanine on 2010-06-03
> **andrewabc said:**
> You have Mushkin 60GB SSD?
So it's sandforce controller.

When you say 3mb/s is that read or write?
Are you constantly benchmarking it (specifically write benchmarks)? Don't do that as it slows it down.

Your alignment looks ok. Read: [Partition alignment for OCZ Vertex in Linux](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)

Go to verify result section to see if similar to what they have.


The start of 1049 looks wrong. Shouldn't it be 1024? I think that is your problem. Although odd that gparted says 2048 is start position. Still no confirmation from anyone whether 10.04 aligns SSD properly by default.

Gparted does that because it is mimicking the Windows 7 behavior, which is to start at sector 2048. You can use any multiple of 1024 as a starting sector, although using sector 1024 minimizes wasted space.

---

### Post by 98cwitr on 2010-06-03
I have only done read benchmarks. I started at 264MBps avg. I was @ 249.6 yesterday and just pulled 250.7. It has been around this number for a week or so without much fluctuation. 

See post #53
[http://ubuntuforums.org/showthread.php?t=1468995](http://ubuntuforums.org/showthread.php?t=1468995)

---

### Post by andrewabc on 2010-06-03
> **98cwitr said:**
> I have only done read benchmarks. I started at 264MBps avg. I was @ 249.6 yesterday and just pulled 250.7. It has been around this number for a week or so without much fluctuation. 

See post #53
[http://ubuntuforums.org/showthread.php?t=1468995](http://ubuntuforums.org/showthread.php?t=1468995)

Where did you see your 3mb/s speed?
Even if not aligned, it should be almost 100mb/s at least.

---

### Post by 98cwitr on 2010-06-04
> **andrewabc said:**
> Where did you see your 3mb/s speed?
Even if not aligned, it should be almost 100mb/s at least.

no no, it was decreasing at a rate of 3 MBps per day on average and now has stabilized at 250ish.

---

