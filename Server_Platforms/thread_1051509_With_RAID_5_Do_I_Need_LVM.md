---
title: "With RAID 5 Do I Need LVM ?"
date: 2009-01-26
forum: Server Platforms
---

### Post by thornomad on 2009-01-26
Hi - sorry if this question is naive, but I don't think I understand how this all works fully yet ...

I am going to install 3 drives in a RAID 5 array.  I chose RAID 5 so I could add drives (of the same size), in the future to expand my storage needs.  

My question, though, is do I need to utilize LVM to access the space of an additional drive ?  Or will mdadm handle the space expansion (and how) ?

Currently, my (old) NAS has three partitions:

1. swap
2. / (root)
3. /home

I planned to do the same thing on my next system ... I know this means I need to partition each drive the same way three times (same size partitions, all set for "software raid") but wasn't sure if, after setting up the RAID devices, I needed to add LVM devices on top of that for root or /home (or both) ... or if RAID was enough.

Hope my question makes sense ... am still learning.

Thanks,
Damon

---

### Post by Xianath on 2009-01-27
Technically, no, but it does have its benefits. Online snapshots are good, also you could add various size disks (they do tend to get larger with time) or move your entire filesystem to a different bunch of disks.

Two things I notice in your setup plan. You definitely do not want your swap to reside on a RAID partition. Just use regular swap partitions on separate spindles. Also, I see no partition to mount as /boot. I always give my boxen an ext3 /boot and an xfs / and /home. This is especially true with LVM and/or RAID because xfs can grow on the fly and, what's more important, can be defragmented. 

mdadm can easily grow a RAID5 array, try 'sudo mdadm --grow --help' for details. One thing you'll run into that is not in the manpage is that when growing, the rebuild speed is appalling. This is controlled by a kernel tunable, /sys/block/<md_device>/md/sync_speed_min which is 1MB/sec by default (ugh!). When you start a rebuild, do "echo 100000 | sudo tee /sys/block/<md_device>/md/sync_speed_min" while keeping an eye on "watch -n 1 cat /proc/mdstat". Just so you can enjoy the results :)

One thing you need to keep in mind, at least with xfs, is that mkfs parameters make a great difference with regards to performance. If you make the filesystem aware of the number of spindles and the RAID stripe size, it will perform much better by optimizing writes so they are stripe aligned. You do this by giving it the stripe size and the number of active data spindles (n for RAID0, n-1 for RAID5, n-2 for RAID6). My 6-disk RAID5 setup with 256k stripes has this xfs on top of LVM:

sudo mkfs.xfs -d su=256k,sw=5 -l su=256k,internal,lazy_writes=1,version=2 /dev/RAID5/Data

Finally -- sorry I can't help with this one yet as I myself am still investigating -- I'm not sure if your boot partition can be on either RAID5 or LVM2. I'll be starting a thread on the subject shortly.

HTH,
Peter

---

### Post by cdtech on 2009-01-27
I love listening to people who know what their talking about. Very good Xianath................

I'm also planning a RAID setup.

---

### Post by Xianath on 2009-01-27
LOL if I knew what I was talking about I wouldn't have come here searching for help and stumbled upon this thread in the first place :D Just thought I'd share what I've been googling the last few days to save the OP some time.

Anyway, this very forum answered the remaining questions. You can NOT boot from RAID5. To get redundancy, set up your /boot partition on RAID1 instead. There's a bug that prevents Hardy from booting off a RAID1 with a failed disk, and there's also a patch. The following should help:

[http://kuparinen.org/martti/comp/ubuntu/en/raid.html](http://kuparinen.org/martti/comp/ubuntu/en/raid.html)

Cheers, and good luck.

Peter

---

### Post by windependence on 2009-01-27
Just FYI, you certainly CAN boot from RAID5, the problem is you CAN'T boot software RAID if the boot is on the RAID partition (makes sense since the RAID has to be live to use it). This goes for any type of software RAID. With a hardware controller card, you can indeed boot from the RAID array.

Just a few comments. LVM can be very useful, and different file systems like XFS and ZFS are great, but adding LVM and XFS may add a level of complexity for the OP that may be too much since he is learning. In fact, on my production servers I run EXT3 in Linux and UFS in FreeBSD. The reason I use "standard" file systems is because if you have problems, recovery is much easier as more information is available about recovery with a standard file system. Contrary to popular belief, EXT3 can also be tuned for better performance if you so desire.

-Tim

---

### Post by Xianath on 2009-01-27
Apparently the bug I mentioned is fixed in 8.04.2 which is already out. See [https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2#Server%20bugs](https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2#Server%20bugs) and [https://help.ubuntu.com/community/DegradedRAID](https://help.ubuntu.com/community/DegradedRAID) . Dustin, if you ever read this -- thanks!!!

Regarding XFS, it's my personal FS of choice. EXT3, even after excessive tuning, has never been able to cope with the way I use my computer (25GB mail, over 75GB in customer log files some over 1GB in size, etc.) JFS was good performance-wise but would lose data every time my laptop would freeze (about once or twice a day on average with Hardy). XFS has been the only FS that able to handle this without either crumbling down or corrupting. Of course, de gustibus non disputandum :) Ext3 is perfect for generic use, it just didn't work for me.

Cheers,
Peter

---

### Post by thornomad on 2009-01-27
> **Xianath said:**
> Two things I notice in your setup plan. You definitely do not want your swap to reside on a RAID partition. Just use regular swap partitions on separate spindles. Also, I see no partition to mount as /boot. I always give my boxen an ext3 /boot and an xfs / and /home. This is especially true with LVM and/or RAID because xfs can grow on the fly and, what's more important, can be defragmented.

Thanks for these tips; good idea about the swap ... one less thing to do.  I hadn't thought about setting /boot off of the RAID5 ... didn't realize I had to, I guess ... maybe, instead, I can do RAID1 with /boot (now that you mention the bug is fixed).

Does that mean I'll be limited to two disks in a RAID1, I wonder -- or can I do RAID1 over many disks ?  I'll have to look that up.

> **Xianath said:**
> One thing you need to keep in mind, at least with xfs, is that mkfs parameters make a great difference with regards to performance. If you make the filesystem aware of the number of spindles and the RAID stripe size, it will perform much better by optimizing writes so they are stripe aligned. You do this by giving it the stripe size and the number of active data spindles (n for RAID0, n-1 for RAID5, n-2 for RAID6). My 6-disk RAID5 setup with 256k stripes has this xfs on top of LVM:

sudo mkfs.xfs -d su=256k,sw=5 -l su=256k,internal,lazy_writes=1,version=2 /dev/RAID5/Data

I have used ext3 just because, well, that was the default; and also because my Ubuntu NAS box is on a 1998 Dell with PCI slots ... so, all that performance boosting (at the time) didn't seem like it would get me anywhere.  Now, though, I am upgrading the system and will take it into account.

If I have time, I am going to look at testing the performance with Bonnie++ and Iozone to see what works best.  Though, as of today, I still am unclear about the stripes and blocks and all the intricacies of that.  I just use it for file storage: anything for document/text files (4kb), to flac files(30MB), to movie files (5+ gigabytes uncompressed).  I don't do databases or anything -- is just storage.

If I *don't* have an LVM and I grow my RAID5 disk (either / root or /home) I guess I still have to expand the file system on top of it ... sounds like XFS will let me do that ... although, ext3 would (with LVM).  

More reading for me!  Thanks again for this input.  It's very helpful.

Damon

---

### Post by electrogeist on 2009-01-27
> **Xianath said:**
> mdadm can easily grow a RAID5 array, try 'sudo mdadm --grow --help' for details. One thing you'll run into that is not in the manpage is that when growing, the rebuild speed is appalling. This is controlled by a kernel tunable, /sys/block/<md_device>/md/sync_speed_min which is 1MB/sec by default (ugh!). When you start a rebuild, do "echo 100000 | sudo tee /sys/block/<md_device>/md/sync_speed_min" while keeping an eye on "watch -n 1 cat /proc/mdstat". Just so you can enjoy the results :)

That sir, is a golden tip!

Also here is a performance tweek: play with blockdev readahead buffer.   You can check results with bonnie++ or something.  This tends to help both hardware and software RAID, reads as well as rewrites:

sudo blockdev --getra /dev/DEVICE
(its prob 256!!)
sudo blockdev --setra 4096 /dev/DEVICE
(and try other values much higher: 8192, 16384, 32768 )

---

### Post by Xianath on 2009-01-30
To get back to the OP's question, I just ran into a situation where I wished I had LVM. My VMWare box (Ubuntu 8.04 x64 Server) had a 20G partition for VMWare itself (virtual swap etc.) and a 120G partition for the actual virtual  machines. Turned out that this was suboptimal and I'd rather have them on a single partition so I could defragment better with more free space available. To do that I had to delete the larger partition and grow the smaller one. I couldn't do that on the fly, I had to reboot to a live CD and waste over an hour in burning the CD, getting to the server room, getting a CDROM drive installed, etc. With LVM I could have just moved stuff around with everything still running on top.

To the LP's points. Read-ahead helps a lot with reads, but I haven't seen it help  so much with writes. For those, you may want to tweak the actual write cache. This is a tunable which (from memory as I don't have access to home from work) should be in /sys/block/<device>/md/stripe_cache_size. There's a read-only entry in there which lists the current stripe cache size, I think it's stripe_cache_active.

For (crude) tuning, I did "while true; do cat stripe_cache_active; done > /tmp/stripe_cache.stat" while copying a large file to the array from somewhere else (eg. dd if=/dev/zero of=largefile bs=1048576 count=4096). I then fed the resulting stat file into kst and made a histogram which showed (statistical noise aside) a peak where the optimum stripe_cache_size should be. In my case it was around 1400 so I made it 1536. YMMV depending on how fast your CPU is in comparison with your I/O subsystem.

This is really starting to get fun :)

Cheers,
Peter

---

### Post by thornomad on 2009-01-30
> **Xianath said:**
> To get back to the OP's question, I just ran into a situation where I wished I had LVM. My VMWare box (Ubuntu 8.04 x64 Server) had a 20G partition for VMWare itself (virtual swap etc.) and a 120G partition for the actual virtual  machines. Turned out that this was suboptimal and I'd rather have them on a single partition so I could defragment better with more free space available. To do that I had to delete the larger partition and grow the smaller one. I couldn't do that on the fly, I had to reboot to a live CD and waste over an hour in burning the CD, getting to the server room, getting a CDROM drive installed, etc. With LVM I could have just moved stuff around with everything still running on top.

Yea - I see what you mean.  I already have partitions I made that I wish were LVM because they are really unused and I would love to swallow them up and gain the space.  

Do you recommend having *everything* in an LVM (except for, I guess, swap and /boot) ?

> **Xianath said:**
> To the LP's points. Read-ahead helps a lot with reads, but I haven't seen it help  so much with writes. For those, you may want to tweak the actual write cache. This is a tunable which (from memory as I don't have access to home from work) should be in /sys/block/<device>/md/stripe_cache_size. There's a read-only entry in there which lists the current stripe cache size, I think it's stripe_cache_active.

For (crude) tuning, I did "while true; do cat stripe_cache_active; done > /tmp/stripe_cache.stat" while copying a large file to the array from somewhere else (eg. dd if=/dev/zero of=largefile bs=1048576 count=4096). I then fed the resulting stat file into kst and made a histogram which showed (statistical noise aside) a peak where the optimum stripe_cache_size should be. In my case it was around 1400 so I made it 1536. YMMV depending on how fast your CPU is in comparison with your I/O subsystem.

Oooooh - now that is the kind of thing I am interested in!  I am hoping my three new drives will arrive today, so I can start playing with this.

Have you ever used [Iozone]("http://iozone.org") ?  (I think it is iozone3 in the repositories.)  I have only played with it a little, but I was going to run that too and see if I could use it to figure out the optimal stripe size too.  Though, I think I would have to have a bunch of different mds to test ... your method, it would seem, would require just one.

> **Xianath said:**
> This is really starting to get fun :)

It sure is.  Am glad I have a little time before I need to put the new machine into "home production" -- this way I can play with all this stuff.  Love hearing your ideas.  Thanks!

---

### Post by electrogeist on 2009-01-30
> **thornomad said:**
> Have you ever used [Iozone]("http://iozone.org") ?  (I think it is iozone3 in the repositories.)  I have only played with it a little, but I was going to run that too and see if I could use it to figure out the optimal stripe size too.  Though, I think I would have to have a bunch of different mds to test ... your method, it would seem, would require just one.

Unfortunately you will need to recreate the array to change the stripe size.  stripe_cache_size is a cache, its not setting the actual stripe size.  

Since building a RAID5 array is timely you can make it small for testing, but at least a few times the size of your RAM (maybe pull some RAM too in order to reduce caching).

Here is a thread with a number of benchmarks with different stripe sizes.  It won't match your hardware but a number of people posted results and it may give you some ideas:
[INDENT]some SW RAID bonnie++ benchmarks  
[http://forums.2cpu.com/showthread.php?t=79364](http://forums.2cpu.com/showthread.php?t=79364)[/INDENT]

---

### Post by Xianath on 2009-01-30
electrogeist is right, apologies if my post was misleading. stripe_cache_size will (as I understand it) increase the number of stripes that can be held in memory. Since this only needs to be done when writing data, this acts as a write-behind cache for actual checksum calculations. This should help smooth peaks in burst load patterns, I think.

XFS itself has a bunch of mount options as well as tunables both in /proc and sysctl, see Documentation/filesystems/xfs.txt in the kernel source. These should come last though, once the underlying hardware has been tuned for top performance, and then the software RAID layer.

Back to the topic of LVM, for all its benefits, it does add another of complexity and therefore a possible (likely minor) performance penalty. My concern is mostly with PE/LE size and whether it should be the same as stripe size, and then of course LV fragmentation and whether it's an issue in the real world at all. There's a tool to defrag LVM2, [http://bisqwit.iki.fi/source/lvm2defrag.html](http://bisqwit.iki.fi/source/lvm2defrag.html) , and though it's just an interface to pvmove it seems useful. Whether that's merited... see the next paragraph :)

I haven't tried with iozone and bonnie++ yet as I don't have the time for serious tests right now. I am planning to do that after exams... I am hoping to be able to pass this as my Master's project, provided the committee accepts it. Then things will get really serious (and hopefully still fun).

Cheers,
Peter

---

### Post by electrogeist on 2009-01-30
> **Xianath said:**
> To the LP's points. **Read-ahead helps a lot with reads, but I haven't seen it help  so much with writes.** For those, you may want to tweak the actual write cache. This is a tunable which (from memory as I don't have access to home from work) should be in /sys/block/<device>/md/stripe_cache_size. There's a read-only entry in there which lists the current stripe cache size, I think it's stripe_cache_active 

You are right that read-ahead has no effect on writes.  However, I wanted to point out that read-ahead does help with **re-**writes.  More of a significant difference than it has on reads actually. 

In the benchmark thread I linked to, in the Sequential Throughput section, compare lines marked "RA" to the ones not marked as such with the same parameters.  Those had "blockdev --setra 32768 /dev/md0" versus defaults
[INDENT][http://forums.2cpu.com/showthread.php?t=79364](http://forums.2cpu.com/showthread.php?t=79364)[/INDENT]

> I am hoping to be able to pass this as my Master's project, provided the committee accepts it. Then things will get really serious (and hopefully still fun).

Well I hope you can pull that off too...and I look forward to reading about it

---

### Post by Xianath on 2009-02-09
Apologies for the late comeback, I just found out about another caveat, potentially very ugly. LVM2 does not support write barriers. This means that any journalled file system on top of LVM2 is in jeopardy in case of power failure (and, to a lesser extent, kernel panics). That is, unless:

1) You disable write cache on md component disks. Performance drops through the floor.

2) You have a controller with battery-backed cache. These cost more than my entire home NAS

3) You use a device such as Gigabyte i-RAM, USB stick, flash, SSD or similar that has low write latency and no chance to leave data unwritten without the kernel knowing it. i-RAM aside, the rest suffer from wear (wear levelling may not work well for journals due to their cyclical nature and small size)

4) You buy a UPS :)

Personally, I'll opt for the latter.

WRT file systems, though I've recommended XFS, it's not without its drawbacks to keep in mind. You can't shrink an XFS partition, there's no undelete facility, and there's the annoying 32-bit inode thing. Check out the FAQ here: [http://xfs.org/index.php/XFS_FAQ](http://xfs.org/index.php/XFS_FAQ)

Cheers,
Peter

---

### Post by waster on 2009-03-22
this is the most useful and well-informed thread I've ever read on ubuntuforums. thanks!

i'm currently working out the best way to stop the suboptimal defaults of RAID10, LVM and ext4 from destroying my disk performance. There seem to be thousands of configurables, all with certain dependencies. Surely this could be automated...

it seems that each layer adds extra data to a partition, so subsequent data doesn't fit neatly into the lower level blocks/stripes/whatever they are called. LVM stride I THINK have something to do with not bunching ext3/4 metadata on a single disk.

LVM stripes are a further confusion, and should be ignored if you are doing LVM on RAID, as RAID will already stripe for you.

---

### Post by Brazilian Joe on 2009-04-02
Personally, being paranoid about bad blocks on swap I put them on top of my RAID, even though it takes a hit in performance. You should try to have as much RAM as possible to get your app running as smooth as possible. Extra RAM is always good, as it is used as disk cache.

One good thing I have read some time ago is that if you have several swap partitions on several disks, the swap automatically stripes the data across them (like a RAID 0). That does not apply to my setup though.

Personally, I like to use LVM because it gives me flexibility to resize my swap partitions. I do one small primary partition on each disk to have multiple copies of the boot partition just in case. If you want swap out of the raid, do one swap partition on each disk as well and let the kernel stripe them automagically. Then do another very big partition for you raid.
On top of that very big partition, use LVM to fit your heart's contents, do the partition only as big as you believe you will need, and leave your extra space unallocated. Use the free space as needed, as it will give you more flexibility.

Don't forget to backup, RAID or not RAID. UPS is also a VERY good idea.

---

