---
title: "EXT4 filesystem broken. Not sure how to fix"
date: 2012-04-24
forum: Server Platforms
---

### Post by malaTG on 2012-04-24
Hi,

My ext4 filesystem broke today on my biggest drive (3TB) and I don't know how to fix it. It tried some different things that I found when googling but nothing seems to work.HEre are some output

parted -l 

gives

```

Modell: ATA WDC WD30EZRX-00M (scsi)
Disk /dev/sdb: 3001GB
Sektorstorlek (logisk/fysisk): 512B/4096B
Partitionstabell: gpt

Nummer  Början  ****    Storlek  Filsystem  Namn  Flaggor
 1      1049kB  3001GB  3001GB   ext4       3TB1

```

sudo fsck.ext4 -v /dev/sdb1

gives

```
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

```

ANY help would be much appreciated....

/Marcus

---

### Post by malaTG on 2012-04-25
bump

---

### Post by Dandaman3452 on 2012-06-12
[HTML]sudo fsck.ext4 -v /dev/sda1
[sudo] password for daniel: 
sudo: unable to open /var/lib/sudo/daniel/1: Read-only file system
e2fsck 1.42 (29-Nov-2011)
/dev/sda1: recovering journal
Clearing orphaned inode 4608224 (uid=1000, gid=1000, mode=0100600, size=1)
Clearing orphaned inode 4607848 (uid=1000, gid=1000, mode=0100664, size=25166)
Clearing orphaned inode 4612941 (uid=1000, gid=1000, mode=0100664, size=32768)
Clearing orphaned inode 4610180 (uid=1000, gid=1000, mode=0100600, size=12648)
Clearing orphaned inode 4610236 (uid=1000, gid=1000, mode=0100664, size=32768)
Clearing orphaned inode 4610222 (uid=1000, gid=1000, mode=0100600, size=117092)
Clearing orphaned inode 4591559 (uid=1000, gid=1000, mode=0100600, size=1)
Clearing orphaned inode 4609947 (uid=1000, gid=1000, mode=0100664, size=25166)
Setting free inodes count to 9983353 (was 9983363)
Setting free blocks count to 2586487 (was 2586381)
/dev/sda1: clean, 387719/10371072 files, 38880136/41466623 blocks[/HTML]
same problem?

---

