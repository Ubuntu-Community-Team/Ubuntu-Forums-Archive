---
title: "Lost space when formating HDD"
date: 2008-10-03
forum: Server Platforms
---

### Post by botfish on 2008-10-03
Hi,

I have formated a new 640Gb hard drive as ext3 using fdisk. I have not written any files to it and $df -h reports:
/dev/sdb1             592G  198M  562G   1% /mnt/backup

I remember that the instructions I was following mentions fdisk leaves some space for the root user and that it can be freed some how.

What is the idea behind this and is it worth freeing?

Cheers

---

### Post by Krupski on 2008-10-03
> **botfish said:**
> Hi,

I have formated a new 640Gb hard drive as ext3 using fdisk. I have not written any files to it and $df -h reports:
/dev/sdb1             592G  198M  562G   1% /mnt/backup

I remember that the instructions I was following mentions fdisk leaves some space for the root user and that it can be freed some how.

What is the idea behind this and is it worth freeing?

Cheers

EXT3 uses some space for it's overhead (in addition to the standard 5% reserved for root).

You can eliminate the reservation for root by using the "-m" option... as in:

> mkfs.ext3 -m0 /dev/yourdisk

You will still have a fair amount of space used by the filesystem.

If you want virtually 99.5% of your disk space, format with XFS instead. 

You may need to get XFS programs (apt-get install xfsprogs).

Then, just do a "mkfs.xfs /dev/yourdisk".

XFS is also quite a bit faster than EXT3. However, I've read that EXT3 is much more robust and able to recover from power fails and other minor corruption (better than XFS that is).

My question always was "If XFS leaves so much more disk space available and is faster too, why doesn't Ubuntu use it?".

The answer I got was "EXT3 is much more robust".

So there you go... you decide!

-- Roger

---

