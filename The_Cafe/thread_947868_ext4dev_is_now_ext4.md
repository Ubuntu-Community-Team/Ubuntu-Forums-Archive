---
title: "ext4dev is now ext4"
date: 2008-10-14
forum: The Cafe
---

### Post by bigbear2350 on 2008-10-14
Sounds like ext4 is almost stable. I hope ext4 will be in Jackalobe. 


[http://www.linuxpromagazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status](http://www.linuxpromagazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status)

---

### Post by Swarms on 2008-10-14
I hope it brings great features.

---

### Post by bigbear2350 on 2008-10-14
It does i have been following development since November 2007

It brings
Extents
Hashed B-trees
Delayed allocation
Improved Inode and block allocation

---

### Post by Sam on 2008-10-14
> **bigbear2350 said:**
> It does i have been following development since November 2007

It brings
Extents
Hashed B-trees
Delayed allocation
Improved Inode and block allocation
... and online defragmentation!

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by master5o1 on 2008-10-14
**almost** stable means almost certain to **not** be in ... oh wait you said Jackelope.


Yeah, I guess it would be n Jackelope. Remind me: Ext4 is ext3+1 and still has backwards compatibility?

---

### Post by bigbear2350 on 2008-10-14
Yeah but once you mount it as ext4 with extents enabled it cant be mounted as ext3.

---

### Post by Calmatory on 2008-10-14
But how do these improvements show up for regular user? Or are they just that server guys bling bling which gives them 2 % better write speeds and half a millisecond less latency under very special and strict circumstances?

---

### Post by SunnyRabbiera on 2008-10-14
well i know that ext3 will probably still be supported for those who do upstream updates as opposed to doing a fresh install.

---

### Post by Polygon on 2008-10-14
> **Calmatory said:**
> But how do these improvements show up for regular user? Or are they just that server guys bling bling which gives them 2 % better write speeds and half a millisecond less latency under very special and strict circumstances?

from wikipedia:

> 
**Faster file system checking**

In ext4, unallocated block groups and sections of the inode table are marked as such. This enables e2fsck to skip them entirely on a check and greatly reduce the time it takes to check a file system of the size ext4 is built to support. This feature is implemented in version 2.6.24 of the Linux kernel.

**Extents**

Extents are introduced to map a range of contiguous physical blocks into a single descriptor. A single extent can map up to 128MiB of contiguous space with a 4KiB block size.[6]

An extent is a contiguous area of storage in a computer file system, reserved for a file. When starting to write to a file, a whole extent is allocated. When writing to the file again, possibly after doing other write operations, the data continues where the previous write left off. This reduces or eliminates file fragmentation.

**Journal checksumming**

Ext4 uses checksums in the journal to improve reliability, since the journal is one of the most used files of the disk. This feature has a side benefit; it can safely avoid a disk IO wait during the journaling process, improving performance slightly. The technique of journal checksumming was inspired by research from Wisconsin on IRON File Systems (Section 6, called "transaction checksums").[7]


so, better reliability, less fragmentation, can do online defragmentation, and faster file system checks at the time of the month every 30 days, yeah i think users will appreciate some of this stuff =)

---

### Post by bigbear2350 on 2008-10-14
1.Extents are what JFS+xfs Use. They improve file deletion times compared to what ext3 uses. Ext3 uses indirect blocks and it is very ineffiecent for large Files.
2.Hashed Btrees speed up directory lookup times as each directory entrie is sorted.

---

