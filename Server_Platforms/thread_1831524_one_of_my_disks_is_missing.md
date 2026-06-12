---
title: "one of my disks is missing"
date: 2011-08-23
forum: Server Platforms
---

### Post by davidmaxwaterman on 2011-08-23
Hi,

I have a 3 disk RAID5 array, seemingly working fine, but one of them doesn't show up in the output of blkid. I'm using whole devices so I was thinking partition tables are irrelevant, but the 'missing' disk is the only one that actually has a partition.

Is this something to worry about, and, if so, can anyone recommend a course of action?

I was going to delete the partition just to try, but I figured I'd ask to make sure first.

I'm running 11.04.

```

davidmaxwaterman@jeeves:/mnt/array/home/davidmaxwaterman$ sudo -s
root@jeeves:/mnt/array/home/davidmaxwaterman# blkid
/dev/sda1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdb1: UUID="cf7dc75b-2960-d15c-cfa0-401463e1c0a4" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/md0: LABEL="bigarray" UUID="67ba7bf6-d421-47d9-ac94-09dfe0a221b6" TYPE="xfs" 
/dev/sdc: UUID="e754a744-b981-e9d8-3b06-9c64eb12f36b" LABEL="jeeves:0" TYPE="linux_raid_member" 
/dev/sde: UUID="e754a744-b981-e9d8-3b06-9c64eb12f36b" LABEL="jeeves:0" TYPE="linux_raid_member" 
/dev/md1: UUID="2Zxdfy-pQOv-tuFl-beGD-3QqZ-NyJW-NPWGQW" TYPE="LVM2_member" 
/dev/mapper/server-root: UUID="8deb8591-2ffb-4fbc-9953-692ae284d34a" TYPE="ext4" 
/dev/mapper/server-swap: UUID="90e8572f-07f5-4163-9beb-18b945932ebc" TYPE="swap" 
root@jeeves:/mnt/array/home/davidmaxwaterman# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020815

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   fd  Linux RAID autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020815

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   fd  Linux RAID autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003870f

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/md0: 2000.4 GB, 2000407232512 bytes
2 heads, 4 sectors/track, 488380672 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b539b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008c845

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    0  Empty
Partition 1 does not start on physical sector boundary.

Disk /dev/md1: 80.0 GB, 80022594560 bytes
2 heads, 4 sectors/track, 19536766 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/dm-0: 75.2 GB, 75161927680 bytes
255 heads, 63 sectors/track, 9137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table
root@jeeves:/mnt/array/home/davidmaxwaterman# uname -a
Linux jeeves 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 athlon i386 GNU/Linux
root@jeeves:/mnt/array/home/davidmaxwaterman# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb1[0] sda1[2]
      78147065 blocks super 1.2 [2/2] [UU]
      
md0 : active raid5 sdd[3] sde[0] sdc[1]
      1953522688 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```

Thanks, in advance.

Max.

---

### Post by Vegan on 2011-08-23
Looks like a real mess. Hope you have a backup.

This looks like a combination file system and array failure


I suggest a backup machine that you can rsync to to be sure your production machine can be recovered fast

---

### Post by rubylaser on 2011-08-23
What do you have in /etc/mdadm/mdadm.conf?
```
/etc/mdadm/mdadm.conf
```

Looks like mdadm is confused about your setup because it's conf file maybe goofed up.

---

### Post by davidmaxwaterman on 2011-08-24
> **Vegan said:**
> Looks like a real mess. Hope you have a backup.

This looks like a combination file system and array failure


I suggest a backup machine that you can rsync to to be sure your production machine can be recovered fast

I do have a backup, yes, but I'd prefer to fix this if at all possible.

What is it you see, exactly?

---

### Post by davidmaxwaterman on 2011-08-24
> **rubylaser said:**
> What do you have in /etc/mdadm/mdadm.conf?
```
/etc/mdadm/mdadm.conf
```

Looks like mdadm is confused about your setup because it's conf file maybe goofed up.

```
root@jeeves:~# cat /etc/mdadm/mdadm.conf 
#DEVICE /dev/sd[abcdefghij]

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR davidmaxwaterman@localhost

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=1a3b684b:4e4bebcd:cff49cf8:ce5aef13
#ARRAY /dev/md1 level=raid1 num-devices=2 UUID=781b5a6f:9319f858:db360d74:6a96127d
#ARRAY /dev/md2 level=raid5 num-devices=6 UUID=15bfec75:595ac793:0914f8ee:862effd8 spares=2
#ARRAY /dev/md2 level=raid5 num-devices=6 metadata=0.90 spares=2 UUID=15bfec75:595ac793:0914f8ee:862effd8
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=e754a744:b981e9d8:3b069c64:eb12f36b
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=cf7dc75b:2960d15c:cfa04014:63e1c0a4
```

regards

---

### Post by toshko3 on 2011-08-24
Why does sdd have a partition, after the whole of it is used in the RAID5? :-s

---

### Post by davidmaxwaterman on 2011-08-24
> **toshko3 said:**
> Why does sdd have a partition, after the whole of it is used in the RAID5? :-s

Probably just something left over from a previous use. It doesn't matter, does it? I thought the partition table was only relevant if you *don't* use the whole disk - ie if you use partitions.

---

### Post by toshko3 on 2011-08-24
I have to admit that I haven't done any soft raid with the whole devices instead of partitions.
What does these commands output:
ls -alk /dev/disk/by-uuid/
mdadm -E /dev/sdc /dev/sdd /dev/sde /dev/sdd1

---

### Post by davidmaxwaterman on 2011-08-24
> **toshko3 said:**
> I have to admit that I haven't done any soft raid with the whole devices instead of partitions.
What does these commands output:
ls -alk /dev/disk/by-uuid/
mdadm -E /dev/sdc /dev/sdd /dev/sde /dev/sdd1

```
root@jeeves:/mnt/array/home/davidmaxwaterman# ls -alk /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 1 2011-08-24 18:09 .
drwxr-xr-x 6 root root 1 2011-08-24 18:09 ..
lrwxrwxrwx 1 root root 1 2011-08-24 18:10 67ba7bf6-d421-47d9-ac94-09dfe0a221b6 -> ../../md0
lrwxrwxrwx 1 root root 1 2011-08-24 18:10 8deb8591-2ffb-4fbc-9953-692ae284d34a -> ../../dm-0
lrwxrwxrwx 1 root root 1 2011-08-24 18:10 90e8572f-07f5-4163-9beb-18b945932ebc -> ../../dm-1
root@jeeves:/mnt/array/home/davidmaxwaterman# mdadm -E /dev/sdc /dev/sdd /dev/sde /dev/sdd1
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e754a744:b981e9d8:3b069c64:eb12f36b
           Name : jeeves:0  (local to host jeeves)
  Creation Time : Thu Jan 27 21:37:11 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953523120 (931.51 GiB 1000.20 GB)
     Array Size : 3907045376 (1863.02 GiB 2000.41 GB)
  Used Dev Size : 1953522688 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e6c87ed6:a3514a37:e81c268e:d039252d

    Update Time : Wed Aug 24 18:16:59 2011
       Checksum : 8abd401d - correct
         Events : 367

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e754a744:b981e9d8:3b069c64:eb12f36b
           Name : jeeves:0  (local to host jeeves)
  Creation Time : Thu Jan 27 21:37:11 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953523120 (931.51 GiB 1000.20 GB)
     Array Size : 3907045376 (1863.02 GiB 2000.41 GB)
  Used Dev Size : 1953522688 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bd9b87e1:3569090f:b3678c95:5a87ad23

    Update Time : Wed Aug 24 18:16:59 2011
       Checksum : 6b73c2dd - correct
         Events : 367

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e754a744:b981e9d8:3b069c64:eb12f36b
           Name : jeeves:0  (local to host jeeves)
  Creation Time : Thu Jan 27 21:37:11 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953523120 (931.51 GiB 1000.20 GB)
     Array Size : 3907045376 (1863.02 GiB 2000.41 GB)
  Used Dev Size : 1953522688 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 80663704:9d56af95:6f114878:b821082c

    Update Time : Wed Aug 24 18:16:59 2011
       Checksum : ffdfbf1e - correct
         Events : 367

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
mdadm: No md superblock detected on /dev/sdd1.
root@jeeves:/mnt/array/home/davidmaxwaterman# 
```

Oh, one more thing...the Disk Utility (yeah, this is regular ubuntu though with pae) gives a warning :

WARNING: The partition is misaligned by 512 bytes. This may result in very poor performance. Repartitioning is suggested.

I guess this is irrelevant since I'm not using the partition.

I'm very tempted to just remove it, since I'm suspecting it is behind these issues and they're all red herrings...I'll wait though.

---

