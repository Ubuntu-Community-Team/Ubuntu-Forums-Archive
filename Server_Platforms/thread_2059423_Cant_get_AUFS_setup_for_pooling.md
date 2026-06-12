---
title: "Cant get AUFS setup for pooling"
date: 2012-09-18
forum: Server Platforms
---

### Post by zac_haryy on 2012-09-18
I am making a home server (mv from 5 year RAID-5 to something new) and trying to get my pooling correct.

Just making sure that I am understanding the functionality of AUFS here. I was thinking AUFS was a pooling software that would all me to "mount" three hdd partitions and it would show me the free space on all the drives under one mount point. Then I would share that mount point on my smb conf. So from a user computer I would right a file to that share and it would (if it were a big backup file) file up the first hdd and then move to the next or judging by space right to a disk with more space (or an hdd that had enough space for the file). Here is my setup:

fdisk - l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c03c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     5236735     2617344   83  Linux
/dev/sda2       100665344   201328639    50331648   83  Linux
/dev/sda3       201328640   301991935    50331648   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d3375

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   389693439   194845696   83  Linux
/dev/sdb2       389695486   390721535      513025    5  Extended
/dev/sdb5       389695488   390721535      513024   82  Linux swap / Solaris

```

df -h
```
harold@ms:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/sdb1                183G  2.1G  172G   2% /
udev                     236M  4.0K  236M   1% /dev
tmpfs                     98M  668K   97M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     243M     0  243M   0% /run/shm
/dev/sda1                2.5G  2.4G  132K 100% /mnt/t1
/dev/sda2                 48G  3.2G   42G   7% /mnt/t2
/dev/sda3                 48G  180M   45G   1% /mnt/t3
/mnt/t1;/mnt/t2;/mnt/t3   97G  5.7G   87G   7% /mnt/mhddfs

```

mount
```
/dev/sda1 on /mnt/t1 type ext4 (rw)
/dev/sda2 on /mnt/t2 type ext4 (rw)
/dev/sda3 on /mnt/t3 type ext4 (rw)
/mnt/t1;/mnt/t2;/mnt/t3 on /mnt/mhddfs type fuse.mhddfs (rw,nosuid,nodev,allow_other)

```

I tried the two different commands and both would only write to t1 in the following:
```
sudo mount -t aufs -o dirs=/mnt/t1=rw:/mnt/t2=rw:/mnt/t3=rw none /mnt/aufs
```
```
sudo mount -t aufs -o br:/mnt/t1=rw:/mnt/t2=rw:/mnt/t3=rw none /mnt/aufs
```

I put the -o in there because that is what I've seen in examples I could find. Not exactly possitive what it does. But is there something that I am doing wrong becuase I dont understand what this program is doing otherwise. I am just testing the program before I put the "real" data on their. But I am guessing since AUFS is using mount points that it shouldn't matter if I'm using one disk or two would it? The server in the end will have 3 3tb for the pooling. Please let me know if there is something I am doing wrong here. Thanks for any help :guitar:


-haryy

---

