---
title: "Accidentally added disk to a partition-based mdadm raid6 array"
date: 2018-09-24
forum: Server Platforms
---

### Post by Benoe on 2018-09-24
Hi!

I just grew my 3-disk raid5 array to a 4-disk raid6 one, but added the whole disk, not just the partition. Sync has finished already.

```
md127 : active raid6 sdc[4] sda1[0] sdb1[1] sdd1[3]
      3906561024 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

```

What would be the best take to remove the new disk and re-add as partition?
Do I need to fail, remove the disk, add and resync the partition again?

Thanks.

---

### Post by darkod on 2018-09-24
Yeah, if you want to do it, it would be to fail /dev/sdc, to remove it from the array, then to zero the mdadm superblock on it. Then create a partition and add it to the array.

---

### Post by Benoe on 2018-09-26
> **darkod said:**
> Yeah, if you want to do it, it would be to fail /dev/sdc, to remove it from the array, then to zero the mdadm superblock on it. Then create a partition and add it to the array.

Thanks. The thing is that I have already partitioned it, just forgot to put 1 after sdc at adding:

```
Disk /dev/sdc: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x30fa4bfe

Eszköz     Indítható Start       Vége  Szektorok  Size Id Típus
/dev/sdc1             2048 3906826239 3906824192  1,8T fd Linux raid
```

---

