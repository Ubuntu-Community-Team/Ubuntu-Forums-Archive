---
title: "Available Space issue with ZFS/iSCSI"
date: 2014-02-20
forum: Server Platforms
---

### Post by Sethar on 2014-02-20
Hello all,

I'm at a bit of a loss and looking for some guidance.  I have Windows Home Server 2011 on one end with a 12.7TB drive cluster, and on the other end I set up a Ubuntu server with ZFS and iSCSI that has 3 x 3TB hard drives.  I did the following to create a raidz1:

```
zpool create storage raidz /dev/sda /dev/sdb /dev/sdc
zfs create -V 5288G storage/data
zfs set compression=lzjb storage/data  
``` 
(I did compression because this site suggested it "doesn't hurt, as long as performance isn't a big deal": [https://pthree.org/2012/12/18/zfs-administration-part-xi-compression-and-deduplication/](https://pthree.org/2012/12/18/zfs-administration-part-xi-compression-and-deduplication/) )

This gave me a zpool which was 8.12TB in space:

```
zpool list
NAME      SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT
storage  8.12T  1.33M  8.12T    0%  1.00x  ONLINE  -
```

and zfslist showed 5.33TB of that was usable:

```
zfs list
NAME           USED  AVAIL  REFER  MOUNTPOINT
storage       5.33T   113M   181K  /storage
storage/data  5.33T  5.33T  124K  -
```


I set up iscsi and added the following to /etc/iet/ietd.conf:

```
Target iqn.2014-02.com.sethar:storage
Lun 0 Path=/dev/zd0,Type=blockio
```

On the Windows side of things, I mounted the drive and formatted it NTFS with 4k Allocation.  At this point ZFS was reporting 5.33TB free, and the NTFS on the other end was reporting 5.16TB free.  All things considered, sounded good - I had about 4.3 TB of data I actually needed to back up to this box.

The strangeness comes in here.  As the copy job went on, the amount of "AVAIL" space in zfs list shrunk faster than the amount of data that was actually being copied.  By the time the copy job failed, zfs list looked like this:

```
zfs list
NAME           USED  AVAIL  REFER  MOUNTPOINT
storage       5.33T   113M   181K  /storage
storage/data  5.33T     0K  5.33T  -
```

And NTFS was reporting ~1.2TB free of the 5.16TB volume.  Only about 3.5 TB of the 4.3TB data had copied over.  I know ZFS has overhead for redundancy, but I thought that was why it went from 8.12TB to 5.33TB of space.  Can someone explain to me what I am missing?

Problem #2 is that I quick formatted the NTFS drive in Windows so it was empty again, then tried to re-copy data and it failed, and the ZFS pool was still reporting 5.33T in the "REFER" column and 0K available.  I had to actually destroy and re-create the ZFS volume and remount/reformat to get it to start working again.  This gives me concerns for when that backup set changes and I need to override /delete existing data.  Can anyone explain why this is happening?  I get that ZFS doesn't know what NTFS is doing on top of it so it just sees a big blob of data, but when I wiped the drive I should have been able to write to it again (overriding existing written blocks), correct?

---

### Post by brokenhachi on 2014-02-20
Maybe ZFS snapshots? ```
zfs list -t snapshot
```


edit: check this out: [https://serverfault.com/questions/192927/free-space-on-zfs-file-system-unexpectedly-missing](https://serverfault.com/questions/192927/free-space-on-zfs-file-system-unexpectedly-missing)

---

### Post by Sethar on 2014-02-20
Thanks, I looked into that and it does not seem to be the same issue unfortunately.  I wiped and re-created everything and it's currently copying data as I type this, but it's already showing signs of the issue:

```
sethar@LINUX-ISCSI:~$ sudo zfs list -o space
NAME          AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
storage        118M  5.33T         0    181K              0      5.33T
storage/data  5.01T  5.33T         0    328G          5.01T          0

```

[IMG]http://i.imgur.com/v9Siz5n.png[/IMG]

As you can see, 249GB reported used by Windows, 328G reported as used by ZFS - no snapshots.

---

### Post by Sethar on 2014-02-21
So it seems that it has something to do with NTFS riding on top of ZFS.  If I just do a samba share directly to the zfs, the results are 1:1 ratio:

```
sethar@LINUX-ISCSI:~$ sudo zfs list -o space
NAME     AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
storage  4.51T   839G         0    839G              0      2.09M
```

[IMG]http://i.imgur.com/dsGFNBT.png[/IMG]

from what I am reading it has something to do with sector/block alignments.  I tried forcing everything to 4k, and then again to 8k (including the NTFS partition that sat on top of ZFS, and ISCSI set to blockio on /dev/zd0 which from what I read inherits the block size of the device it's mapped to automatically):

```
sudo zpool create -o ashift=12 storage raidz /dev/sda /dev/sdb /dev/sdc
sudo zfs create -o volblocksize=4k -V 5288G storage/data
sudo zfs set recordsize=4096 storage
sudo zfs set compression=zle storage/data
```


It made no difference, still overhead.  Unless there's some magic number or setting I am missing, or concept that is escaping my grasp, I have resigned myself to mapping the drive through SMB/CIFS and copying to it that way...which is a shame because it's significantly slower.  If anyone has the ability to explain to me how (if even possible, I suspect not) one could "align" everything from top to bottom so that a NTFS partition has a 1:1 ratio with ZFS storage, I would be immensely grateful.

---

