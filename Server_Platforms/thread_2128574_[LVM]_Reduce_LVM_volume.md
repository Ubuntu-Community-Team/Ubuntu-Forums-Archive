---
title: "[LVM] Reduce LVM volume"
date: 2013-03-23
forum: Server Platforms
---

### Post by sjoa on 2013-03-23
Hi All

**Background**:
I've got a Ubuntu 10.04 server functioning as file, web and back-end TV server. I had 3 1TB disks, root (), swap () and LVM on first drive, second and third only LVM, *fdsik -l*, *pvdisplay -m*, *vgdisplay* and *lvdisplay* (should have looked like this):
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: XXXXXXXXX

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080        6577     4000185   82  Linux swap / Solaris
/dev/sda3            6578      121601   923930280   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: XXXXXXXXX

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: XXXXXXXXX

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

```

I bought a new 2TB drive and I planned to create one partition on it and extend the volumegroup. However, since the first three disks had MBR partition tables which is not suitable for bigger drives I created a GTP table on the new drive. I splitted the new drive in two partitions (for various reasons) and added the first (sdd1) to the volume and everything was great. Then (at 2.30 am) I changed my mind, and wanted to have the new drive as one big partition... long story short... I repartitioned the drive and managed to delete the volumegroup! I've now managed to get the volumegroup back with *vgcfgrestore* and *lvchange*.

**Problem**:
My LVM configuration is not aligned with my partition tables on the new drive. LVM display command gives me following printouts:
```


root@tux ~ # pvdisplay -m
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               datavg
  PV Size               881.13 GiB / not usable 3.66 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              225568
  Free PE               0
  Allocated PE          225568
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-CDl3mJ
   
  --- Physical Segments ---
  Physical extent 0 to 225567:
    Logical volume	/dev/datavg/datalv
    Logical extents	476932 to 702499
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               datavg
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-YiGoBd
   
  --- Physical Segments ---
  Physical extent 0 to 238465:
    Logical volume	/dev/datavg/datalv
    Logical extents	0 to 238465
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               datavg
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-6KVlvH
   
  --- Physical Segments ---
  Physical extent 0 to 238465:
    Logical volume	/dev/datavg/datalv
    Logical extents	238466 to 476931
   
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               datavg
  PV Size               931.50 GiB / not usable 3.36 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238464
  Free PE               0
  Allocated PE          238464
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-9GzHQa
   
  --- Physical Segments ---
  Physical extent 0 to 238463:
    Logical volume	/dev/datavg/datalv
    Logical extents	702500 to 940963
   
root@tux ~ # pvdisplay -m
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               datavg
  PV Size               881.13 GiB / not usable 3.66 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              225568
  Free PE               0
  Allocated PE          225568
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-CDl3mJ
   
  --- Physical Segments ---
  Physical extent 0 to 225567:
    Logical volume	/dev/datavg/datalv
    Logical extents	476932 to 702499
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               datavg
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-YiGoBd
   
  --- Physical Segments ---
  Physical extent 0 to 238465:
    Logical volume	/dev/datavg/datalv
    Logical extents	0 to 238465
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               datavg
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
  PV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-6KVlvH
   
  --- Physical Segments ---
  Physical extent 0 to 238465:
    Logical volume	/dev/datavg/datalv
    Logical extents	238466 to 476931
   
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               datavg
  PV Size               931.50 GiB / not usable 3.36 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238464
  Free PE               0
  Allocated PE          238464
  PV UUID               XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-9GzHQa
   
  --- Physical Segments ---
  Physical extent 0 to 238463:
    Logical volume	/dev/datavg/datalv
    Logical extents	702500 to 940963
   
root@tux ~ # vgdisplay 
  --- Volume group ---
  VG Name               datavg
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  17
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               3.59 TiB
  PE Size               4.00 MiB
  Total PE              940964
  Alloc PE / Size       940964 / 3.59 TiB
  Free  PE / Size       0 / 0   
  VG UUID               XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-FgIdt5
   
root@tux ~ # lvdisplay 
  --- Logical volume ---
  LV Name                /dev/datavg/datalv
  VG Name                datavg
  LV UUID                XXXXX-XXXX-XXXX-XXXX-XXXX-XXXX-UUhxOI
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.59 TiB
  Current LE             940964
  Segments               4
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0

```

My gdisk print command looks like this:
```

root@tux ~ # gdisk /dev/sdd
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sdd: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): XXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 5070 sectors (2.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      3907024064   1.8 TiB     FD00  

Command (? for help): 

```

I can mount and read/write to the volume so I've backed up the important stuff, however I can't backup everything due to the amount of data. 

**Question**:
I'd like to remove sdd1 from the volumegroup and then add it again as one big partition to utilize the whole disk.
Do I have to shrink the ext3 filesystem and logical volume before I do a pvmove /dev/sdd1? Since I will add "new" bigger partition I will resize the logicalvolume and filesystem anyway. 

I guess I need to delete some files in the volume since I'm getting following from pvmove?
```

root@tux ~ # pvmove -v /dev/sdd1 --alloc anywhere
    Finding volume group "datavg"
  No extents available for allocation

```

Thanks!
/David

---

### Post by darkod on 2013-03-23
How much data you have on datalv? What does this say:
df -h

---

### Post by sjoa on 2013-03-23
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G   19G   25G  44% /
none                  1.5G  352K  1.5G   1% /dev
none                  1.5G  660K  1.5G   1% /dev/shm
none                  1.5G  548K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/mapper/datavg-datalv
                      3.6T  2.7T 1001G  73% /media/data

```
e2fsck -f
```

e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
vgdis	Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/datavg/datalv: 588095/3763968 files (8.5% non-contiguous), 701186524/963547136 blocks

```

---

### Post by darkod on 2013-03-23
You should be able to remove sdd1 but just barely. If my calculation is not wrong, sdd1 has about 930GB and you have 1001GB available on datalv. That means you should be able to shrink the filesystem and move the LV extents to another PVs. Not sure if it will work though.

Also, the datalv has to be unmounted and these operations might take long if there is much data to move, so be patient. Since sdd1 was added recently, in most cases there will be only small amount of data to move.

The problem is also that you don't have too much spare space for maneuvering.

Can you move part of the data to external storage temporarily? About 200GB approx. That should give you enough to work with.

Another option, which is probably much safer, why don't you simply add the sdd2 partition as PV to the LVM and keep using the system like that. You will still have the same total space as if you created single partition on sdd and added it to the LVM. And you don't do any data manipulation which sometimes can go wrong. Especially since you don't have the opportunity to make a full backup.

---

### Post by sjoa on 2013-03-23
Thanks for the answers darkod. 


I agree, the safest would be to add the sdd2, but that's part of my problem, I've got a mismatch between the  LVM configuration and the partition table. LVM is using ~50% of sdd (old sdd1) but in reality it's one partition on the whole drive:
```

root@tux ~ # gdisk /dev/sdd
GPT fdisk (gdisk) version 0.5.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sdd: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): XXXXXXXXXXXXXXXXXXXXXXXXXX
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 5070 sectors (2.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      3907024064   1.8 TiB     FD00  

Command (? for help): 

```

If I go for the first option, do I have to shrink the filesystem and logicalvolume if I:
[LIST=1]
[*]Remove 2-300GB from the volume
[*]Do a pvmove /dev/sdd1
[*]pvcreate ...
[*]lvextend ...
[*]resize2fs ...
[/LIST]

---

### Post by darkod on 2013-03-23
I'm not sure if you need to shirnk the FS before using pvmove, maybe not. I would still do it just in case.

Also, when shrinking the FS make sure you leave some overhead, but not too much (since you don't have space to waste). For example, if after moving 300GB you have 2.4TB used on datalv, unmount it and use resize2fs to make the new size 2.5TB. Also make sure both commands are using the same type of capacity value (TiB vs TB). In the LVM and the FS I think even though it says TB it's using TiB actually.

Then with lvreduce shrink the LV size to 2.6TB again leaving some overhead compared to the FS size you selected in resize2fs. Not sure if you can try the pvmove without shrinking the LV with lvreduce.

After the pvmove is done you should be able to remove sdd1 with vgreduce. Only after sdd1 is removed from the VG with vgreduce, you can delete the sdd1 partition and create a new partition taking the whole disk.

As additional info, a 2TB disk can still work with msdos table so you can create new msdos table if you want, and one LVM partition on it. You have to use gpt on disks larger than 2.2TB, which usually means on 3TB disks.

After you have the new partition, you know what to do: pvcreate, vgextend (to add it to the VG), lvextend (to extend the LV), resize2fs. Mount the datalv again.

Older but still useful LVM how to:
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

You have everything in section 11, Common Tasks.

---

### Post by sjoa on 2013-03-23
Thanks darkod,

I'm currently moving ~300GB to another computer with 100Mbps NIC... it takes some time...

I'm following your're advice when the transfer is complete, this is what i'm planning to do. Please let me know if I should do something differently, I've got some planning time ;):
[LIST=1]
[*]df -h 
[*]umount /media/data
[*]e2fsck -f /dev/datavg/datalv
[*]resize2fs -P /dev/datavg/datalv
[*]resize2fs -p /dev/datavg/datalv 2560G (depending on printout in step 1 and 4)
[*]e2fsck -f /dev/datavg/datalv (new check on the filesystem, just to be sure it worked well)
[*]lvreduce -L2670G /dev/datavg/datalv (size depending on size in step 5)
[*]vgreduce datavg /dev/sdd1
[*]gdisk /dev/sdd
[*]pvcreate /dev/sdd1
[*]vgextend datavg /dev/sdd1
[*]pvscan (check that I've got a new physical volume assigned to datavg)
[*]lvextend /dev/datavg/datalv /dev/sda3 (I had 74.14 GiB unallocated on sda3 after the lvreduce in step 7)
[*]lvextend /dev/datavg/datalv /dev/sdd1
[*]resize2fs -p /dev/datavg/datalv
[*]mount /dev/datavg/datalv /media/data
[*]df -h
[*]
[/LIST]

A couple of questions:
After the pvmove command (step 8) the sdd-disk should be "free" from LVM, is there any need for me to repartition the disk?
Since I'm expanding the FS in step 13 I don't need to create a FS on the drive before I add it back to LVM  in step 9, right?

EDIT:
I've done all these steps and my LVM is up and running, here are what I did:
```

root@tux ~ # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G   19G   25G  44% /
none                  1.5G  352K  1.5G   1% /dev
none                  1.5G  660K  1.5G   1% /dev/shm
none                  1.5G  1.7M  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/mapper/datavg-datalv
                      3.6T  2.4T  1.3T  65% /media/data
root@tux ~ # umount /media/data 
root@tux ~ # e2fsck -f /dev/datavg/datalv
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/datavg/datalv: 587800/3763968 files (8.4% non-contiguous), 623687992/963547136 blocks
root@tux ~ # resize2fs -P /dev/datavg/datalv
resize2fs 1.41.11 (14-Mar-2010)
Estimated minimum size of the filesystem: 623583217
root@tux ~ # resize2fs -p /dev/datavg/datalv 2560G
resize2fs 1.41.11 (14-Mar-2010)
Resizing the filesystem on /dev/datavg/datalv to 671088640 (4k) blocks.
Begin pass 2 (max = 29388161)
Relocating blocks             XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Begin pass 3 (max = 29406)
Scanning inode table          XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Begin pass 4 (max = 35564)
Updating inode references     XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/datavg/datalv is now 671088640 blocks long.

root@tux ~ # e2fsck -f /dev/datavg/datalv
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/datavg/datalv: 587800/2621440 files (8.5% non-contiguous), 623598732/671088640 blocks
root@tux ~ # lvreduce -L2670G /dev/datavg/datalv
  WARNING: Reducing active logical volume to 2.61 TiB
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce datalv? [y/n]: y
  Reducing logical volume datalv to 2.61 TiB
  Logical volume datalv successfully resized
root@tux ~ # pvmove -v /dev/sdd1 --alloc anywhere
    Finding volume group "datavg"
    Archiving volume group "datavg" metadata (seqno 18).
    Creating logical volume pvmove0
  No data to move for datavg
root@tux ~ # vgreduce datavg /dev/sdd1
  Removed "/dev/sdd1" from volume group "datavg"
root@tux ~ # gdisk /dev/sdd
root@tux ~ # pvcreate /dev/sdd1
  Physical volume "/dev/sdd1" successfully created
root@tux ~ # vgextend datavg /dev/sdd1
  Volume group "datavg" successfully extended
root@tux ~ # pvscan 
  PV /dev/sda3   VG datavg   lvm2 [881.12 GiB / 74.14 GiB free]
  PV /dev/sdb1   VG datavg   lvm2 [931.51 GiB / 0    free]
  PV /dev/sdc1   VG datavg   lvm2 [931.51 GiB / 0    free]
  PV /dev/sdd1   VG datavg   lvm2 [1.82 TiB / 1.82 TiB free]
  Total: 4 [4.50 TiB] / in use: 4 [4.50 TiB] / in no VG: 0 [0   ]
root@tux ~ # lvextend /dev/datavg/datalv /dev/sdd1
  Extending logical volume datalv to 4.43 TiB
  Logical volume datalv successfully resized
root@tux ~ # vgdisplay 
  --- Volume group ---
  VG Name               datavg
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  22
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               4.50 TiB
  PE Size               4.00 MiB
  Total PE              1179429
  Alloc PE / Size       1179429 / 4.50 TiB
  Free  PE / Size       0 / 0   
   
root@tux ~ # lvdisplay 
  --- Logical volume ---
  LV Name                /dev/datavg/datalv
  VG Name                datavg
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                4.50 TiB
  Current LE             1179429
  Segments               5
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
root@tux ~ # pvdisplay 
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               datavg
  PV Size               881.13 GiB / not usable 3.66 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              225568
  Free PE               0
  Allocated PE          225568
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               datavg
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               datavg
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               0
  Allocated PE          238466
   
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               datavg
  PV Size               1.82 TiB / not usable 2.75 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476929
  Free PE               0
  Allocated PE          476929
   
root@tux ~ # pvdisplay -s
  Device "/dev/sda3" has a capacity of 74.14 GiB
  Device "/dev/sdb1" has a capacity of 0   
  Device "/dev/sdc1" has a capacity of 0   
  Device "/dev/sdd1" has a capacity of 0   
root@tux ~ # lvextend /dev/datavg/datalv /dev/sda3
  Extending logical volume datalv to 4.50 TiB
  Logical volume datalv successfully resized
root@tux ~ # pvdisplay -s
  Device "/dev/sda3" has a capacity of 0   
  Device "/dev/sdb1" has a capacity of 0   
  Device "/dev/sdc1" has a capacity of 0   
  Device "/dev/sdd1" has a capacity of 0   
root@tux ~ # resize2fs -p /dev/datavg/datalv
resize2fs 1.41.11 (14-Mar-2010)
Resizing the filesystem on /dev/datavg/datalv to 1207735296 (4k) blocks.
Begin pass 1 (max = 16378)
Extending the inode table     XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/datavg/datalv is now 1207735296 blocks long.

root@tux ~ # mount /dev/datavg/datalv /media/data
root@tux ~ # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G   19G   25G  44% /
none                  1.5G  352K  1.5G   1% /dev
none                  1.5G  660K  1.5G   1% /dev/shm
none                  1.5G  528K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/mapper/datavg-datalv
                      4.5T  2.4T  2.2T  52% /media/data


```

---

### Post by darkod on 2013-03-23
The steps look correct, only that I would delete the sdd1 partition after step 8 and recreate it again. Just to make sure it's a good, new partition. Then continue with pvcreate /dev/sdd1.

No, you don't need to create any FS on sdd1 before adding it to the LVM. The FS is onto the LVs, not the physical partitions. The partitions only serve as devices to hold the LVM.

In step 14 I believe the command would be mount /dev/sdd1 /media/data, not sure if it will work without specufying /dev/sdd1. Since you probably have the entry in fstab it might work without it.

EDIT PS. I don't get what's the purpose of step 4. After the fsck you can go straight to resizing the filesystem to XXXX GB (step 5 in your list).

---

### Post by sjoa on 2013-03-23
> **darkod said:**
> The steps look correct, only that I would delete the sdd1 partition after step 8 and recreate it again. Just to make sure it's a good, new partition. Then continue with pvcreate /dev/sdd1.
Ok, do you recommend me to go back to MBR on the disk, I got some warnings before I moved to GPT? Could it be an issue mixing MBR and GPT in the same VG/LV?

> **darkod said:**
> In step 14 I believe the command would be mount /dev/sdd1 /media/data, not sure if it will work without specufying /dev/sdd1. Since you probably have the entry in fstab it might work without it.
Correct, I've got it in fstab, I'll change the steps in my previous post. 

> **darkod said:**
> EDIT PS. I don't get what's the purpose of step 4. After the fsck you can go straight to resizing the filesystem to XXXX GB (step 5 in your list).
The -P option prints the minimum size of the FS, I'd like to do that in order to see how much I can reduce it.

---

### Post by darkod on 2013-03-23
If the -P option does that, then it's a very good idea.

Mixing msdos with gpt tables shouldn't affect anything. The only thing I can think of when switching to gpt table is that you need a small 1MiB partition with no filesystem (RAW) and the bios_grub flag set if you ever want to install grub2 on the MBR of this disk. That's because gpt MBR is smaller than msdos MBR and grub2 doesn't fit, so it uses the bios_grub flag to see where to put part of its code. It's very small code so literary 1MiB is enough only there should be no filesystem, it uses it raw.

So, it seems like you are good to go as soon as the data move finishes.

---

### Post by sjoa on 2013-03-23
Thanks, much appreciated!
It's still ~10 hours of moving... I'll bump the thread when I've got any news.

---

### Post by sjoa on 2013-03-24
pvmove don't remove the drive from the volume group, I'm getting following from the command:
```
root@tux ~ # pvmove -v /dev/sdd1 --alloc anywhere
    Finding volume group "datavg"
    Archiving volume group "datavg" metadata (seqno 18).
    Creating logical volume pvmove0
  No data to move for datavg

```

So I guess I should use pvremove instead? I tried with the test flag first and got following output.
```
root@tux ~ # pvremove -v -t /dev/sdd1 
  Test mode: Metadata will NOT be updated.
  Can't pvremove physical volume "/dev/sdd1" of volume group "datavg" without -ff
    Test mode: Wiping internal cache
    Wiping internal VG cache
root@tux ~ # pvremove -v /dev/sdd1 
  Can't pvremove physical volume "/dev/sdd1" of volume group "datavg" without -ff

```
Is the *-ff* standard, should I do a pvremove -v -ff /dev/sdd1?

---

### Post by darkod on 2013-03-24
I think the No data to move only means the extends on sdd1 are not used in the LVM, there is no actual data on them. Which is good news since you can only remove a physical device that hold no LVM data in use.

The command to remove sdd1 from the LVM is not pvremove, it's vgreduce. It should be like:
```
sudo vgreduce datavg /dev/sdd1
```

[http://www.tldp.org/HOWTO/LVM-HOWTO/removepvsfromvg.html](http://www.tldp.org/HOWTO/LVM-HOWTO/removepvsfromvg.html)

You did reduce the filesystem first, right? Anyway, if pvmove says there is no data to move then sdd1 hasn't been used yet and will be easy to remove.

---

### Post by sjoa on 2013-03-24
Yes, I should off course use vgreduce, thanks.
I've updated my [list]("http://ubuntuforums.org/showthread.php?t=2128574&p=12570883#post12570883") with vgreduce, another lvextend due to some unallocated space on sda3 after lvreduce. 

The LVM is now configures as I want, thanks for your help darkod.

---

