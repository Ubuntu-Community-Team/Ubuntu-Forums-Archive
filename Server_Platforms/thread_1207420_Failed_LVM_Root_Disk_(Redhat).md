---
title: "Failed LVM Root Disk (Redhat)"
date: 2009-07-08
forum: Server Platforms
---

### Post by Ampage on 2009-07-08
Hello

I'm a solaris chap myself and have been handed a load of redhat AS3 servers at work. Figured I'd come here because you are usually damn good.

One of the servers appears to have a failed rootdisk, I've had a look around and can't seem to find a solid procedure to replace the disks on the fly.. which I assume you should be able to do!

With veritas its straightforward,  you just stick the disk in and run some commands to re-mirror. With Solaris volume manager you have to re-partition then run a few commands to re-mirror.

I just want to compare responses on here before I call the vendor :D

```
[root@xxxxxx root]# fdisk -l

Disk /dev/sda: 72.9 GB, 72999763968 bytes
255 heads, 63 sectors/track, 8875 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/sda1   *         1   sdb : READ CAPACITY failed.
s     13    1043db : status = 1, message = 00, host = 0, driver = 08
C1   83  Linux
urrent dsev/sda2       d00:00: sense key Not Ready
 A   14      887dditional sense indicates Medium not present
 s 71184015   8edb : block size assumed to be 512 bytes, disk size 1GB.
 Linux LVM
sdb: test WP failed, assume Write Enabled
 I/O error: dev 08:10, sector 0
 unable to read partition table
 I/O error: dev 08:10, sector 0
sdb : READ CAPACITY failed.
sdb : status = 1, message = 00, host = 0, driver = 08
Current sd00:00: sense key Not Ready
Additional sense indicates Medium not present
sdb : block size assumed to be 512 bytes, disk size 1GB.
sdb: test WP failed, assume Write Enabled
 I/O error: dev 08:10, sector 0
 unable to read partition table
 I/O error: dev 08:10, sector 0
```


sda2 is my lvm partition.

Snippet of df:

```

[root@xxxxxx root]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/vol0/lv02         15G  3.6G   11G  26% /
/dev/sda1              99M   16M   78M  17% /boot
/dev/vol0/lv05        9.7G  1.9G  7.3G  21% /home
none                  2.0G     0  2.0G   0% /dev/shm
/dev/vol0/lv04        4.9G  211M  4.4G   5% /var

```

Thanks guys :guitar:

---

### Post by drave99 on 2009-07-08
what does "cat /proc/mdstat" show

---

