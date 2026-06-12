---
title: "effect of not partitioning &amp; does btrfs support 4k sectors"
date: 2012-02-15
forum: Server Platforms
---

### Post by finite9 on 2012-02-15
Im buying some new hdds for my server (11.10).

I have 160GB sata disk for the OS

2x 1TB WD RE-3 disks in a RAID-1 mdadm array with ext3.

I will soon have 2 x 1TB Seagate Barracudas with 4k sectors.

I want to test out btrfs.

First off:

What are the disadvantages of NOT creating a partition?  I see no need to create a partition for these two new disks, as they are pure data disks, dont even contain the OS.  With my RAID-1 array, I did use some partition tool to set fd as the partition type.

Secondly:

Im going to create a btrfs raid-0 array out of the 2 new disks.  Does btrfs handle 4k sectors automatically?  Is this something I have to tell btrfs to use?

Do I need to use a partition tool to set fd as the partition type?

---

### Post by renkinjutsu on 2012-02-15
There really isn't any disadvantages to not partitioning your data drives. If you partition your drives, you'll run the risk of not having your filesystems properly aligned anyway.

Also, btrfs does support 4k sectors and it is the default (I think). If you want to be sure, mkfs.btrfs has the -s flag that allows you to set the sector size. 'mkfs.btrfs -s 4k /dev/blah' should work

---

### Post by finite9 on 2012-02-16
thanks for the info.

If I create the btrfs filesystem on the raw device, and assuming the default with mkfs.btrfs is 4k, will the alignment be correct, or do you still have to specify an offset?

---

### Post by renkinjutsu on 2012-02-16
I don't think you have to worry about drive alignment if you're not partitioning drives. Though, mkfs.btrfs *does* give a method to offset where the filesystem starts, but I've never tried it.

The main concern a while back was that all of our partition tools assumed 512 sectors while writing partitions. But I don't think it's a concern if you're not even going to partition

---

