---
title: "Growing a 3.8Tb ext4 file system"
date: 2010-03-29
forum: Server Platforms
---

### Post by ian dobson on 2010-03-29
Hi,

I've already asked this in the mythbuntu and didn't get an answer there so I'm trying here.

OK just added another 2Tb WD drive to my mdadm controled RAID5 array, and the reshape is finished:-

```

Code:
Mar 28 18:28:36 alpha2 kernel: [104357.343421] md: md1: reshape done.
Mar 28 18:28:36 alpha2 kernel: [104357.525114] RAID5 conf printout:
Mar 28 18:28:36 alpha2 kernel: [104357.525119]  --- rd:4 wd:4
Mar 28 18:28:36 alpha2 kernel: [104357.525122]  disk 0, o:1, dev:sda2
Mar 28 18:28:36 alpha2 kernel: [104357.525124]  disk 1, o:1, dev:sdb2
Mar 28 18:28:36 alpha2 kernel: [104357.525125]  disk 2, o:1, dev:sdc2
Mar 28 18:28:36 alpha2 kernel: [104357.525127]  disk 3, o:1, dev:sdd2
Mar 28 18:28:36 alpha2 kernel: [104357.525134] md1: detected capacity change from 3960767250432 to 5941150875648
Mar 28 18:28:37 alpha2 kernel: [104358.479632] VFS: busy inodes on changed media or resized disk md1
Mar 28 18:28:37 alpha2 mdadm[1452]: RebuildFinished event detected on md device /dev/md1 

```

My question is does e2resize support expanding/growing ext4 file systems that will end up being larger than 4Tb? I've searched the internet and haven't found anything that makes any sense.

And for information
uname -a
Linux alpha2 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-30
Wow almost 70 views and not a single answer.

Someone's got to know the answer.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-30
wow 90 views and still no answer.

I think I.ve got to look else where.

Regards
Ian Dobson

---

### Post by fang0654 on 2010-03-31
If the filesystem is already over 2TB, growing it more shouldn't be a problem.  Try using parted to grow the partition.

---

### Post by ian dobson on 2010-04-01
Hi,

OK, rebooted the box into single user mode. Did a fsck (that took almost 1 hour), then started a resize2fs -p /dev/md1. 

After several minutes it displayed a message along the lines of "expanding inodes pass 1 (of maximum 1475)" which started to get me abit worried, but about 15 minutes later it finished pass 1 and ended without an error.

I mounted the device and all my files are there :)

Rebooted the box and it started as if nothing had happened (apart from a 6Tb data mount point :D:D:D).

Linux has come along way, since my first tests with an 486 and a sound blaster with CD drive attached.

Regards
Ian Dobson

---

### Post by xianthax on 2010-04-01
"expanding inodes pass 1 (of maximum 1475)"

ext4 creates all its inodes (and hence the maximum number of files) at format time.  This is just telling you its creating inodes for the new space you grew the file system in to.

---

### Post by ian dobson on 2010-04-02
hi xianthax,

Seeing that 1 pass took about 15 minutes, at it said of maximum 1475, I got the point where I though it'll take all week to grow the array (1475 * 10minutes/60 minutes in an hour)

Have you never sat there waiting for something to finish and the display says 2% finished and you start working out in your head how long it'll take?

Regards
FREF99

---

