---
title: "Best storage/filesystem for heavy (and sometimes concurrent) disk IO"
date: 2009-03-28
forum: Server Platforms
---

### Post by r0g on 2009-03-28
Hi there,

I am planning a system for my new workshop (on the cheap natch ;-) ) where the file system will need to deal with some fairly heavy (and concurrent) disk IO, by my modest standards at least. The concurrency will be minimal but the load will be heavy and lengthy (disk images and file sets up to a terrabyte in size) via a gigabit LAN.

At quiet times it will be dealing with either one read job, one write job, or one of each. For this scenario I would like to achieve at least 40Mb/sec read and 40Mb/sec sustained write speed. I figure I can get some raw speed by using RAID 0 and I don't expect the system will need to deal with any more than 3 read jobs and 3 write jobs concurrently. The important thing is that the overall speed degrades gracefully as it's asked to handle more jobs...

What I want to avoid is the seek death scenario you get when doing more than one non-trivial thing to a disk, something I've run into a bunch of times and that I don't think RAID alone addresses (although I'd be delighted to find out otherwise!). While a bit of thrashing is fine some of the jobs I'm running are going to take many hours to complete and I can picture my poor non-server grade drives melting or thrashing themselves to pieces quite quickly if I used say, the ext3 filesystem or NTFS.

I was wondering if there was a filesystem / disk driver / technique that might intelligently temper this overseeking, trading latency for throughput when under stress? The box will be most dealing with large sequential reads and writes so might I be able to tweak the filesystem to use heavier buffering and throw a bunch more ram at it? I heard ext4 makes more use of lazy writing, might using this smooth things out, given a stack of memory to play with?

I have no need for redundancy and journaling or any fancy schmantzy stuff, I'm only interested in getting optimal speed without sending my drives to an early grave! Oh and being able to store the odd 999Gb file :)

Prospective hardware/software

Modest AMD64 Mobo & Chip - probably Athlon 64 Dual Core.
2Gb DDRII RAM (can be upgraded to whatever if useful)
2 x 1TB 7200 Seagate SATA 300 drives with s/w RAID 0
Ubuntu Hardy 64 bit - Gnome desktop version, not server.
Data being pulled from and pushed to Samba/NTFS drives on other machines.

All, suggestions and any other tips re: large files / disk performance, very welcome, doubly so from anyone who's built a box with broadly similar requirements.

Many thanks,

Roger Heathcote.

---

### Post by linuxuser21 on 2009-03-28
If you don't want to go with NTFS, you could probably do FAT32 if you're not worried about security and all that stuff.  Just make the Allocation Unit Size as big as you can if you're going to be transferring a lot of files.

---

### Post by mrsteveman1 on 2009-03-28
I haven't ever had to build a system with substantial I/O requirements, but I'm familiar with some of the components available. 

ZFS is definitely the new hotness, on its native platforms (opensolaris, solaris, nexenta, maybe freebsd) it can handle substantial I/O without blinking even if you don't actually need redundancy etc. On Linux there is zfs-fuse, which works quite well at this point but is beta software, i have no idea how well it handles very high I/O rates. On Solaris ZFS is known to be able to handle high I/O easily, Nexenta is probably similar since it is a native solaris kernel with the ubuntu userland, i've played with it before it is very very cool :)

There is also XFS which is native on Linux, however some of the advantages of XFS might not apply to the Linux implementation:

> XFS is capable of delivering very close to the raw I/O performance that the underlying hardware can provide. XFS has proven scalability on SGI Altix systems of multiple gigabytes-per-second on multiple terabyte filesystems. 

[http://oss.sgi.com/projects/xfs/]("http://oss.sgi.com/projects/xfs/")

If the filesystems implementation of high I/O is very important, you should be flexible with the OS you actually end up using.

It is also possible that EXT2, with no journaling, would be very fast.

I suspect the underlying storage is going to be more important to you than the filesystem.

RAID5 is one of the worst, writes are very expensive with RAID5, it is really a compromise to give users a bit more actual storage space than a pure mirror would provide. RAID0 is probably the fastest, striping writes and reads across a bunch of disks gives you close to the aggregate of those disks speeds combined, as long as the system can handle it and the filesystem is fast (zfs and xfs are known to be able to handle this sort of thing well, i suspect even ext3 would too). 

For hosting our websites (which don't actually use much I/O), we always look for RAID10, because it gives you the speed of RAID0 with the redundancy of RAID1, with no parity calculations needed. If a disk fails, a RAID5 array must be rebuilt, during which time the system will slow to a crawl. We had to deal with this a few weeks ago, for over 15 hours I/O was absurdly slow while the array rebuilt. On RAID10 this would not be a problem, there is no parity data to rebuild from, it is only necessary to replace the disk and let the system mirror the contents of the remaining safe disk again.

---

