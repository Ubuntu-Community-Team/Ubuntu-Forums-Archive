---
title: "Resizing an ext4 partition"
date: 2013-08-13
forum: Server Platforms
---

### Post by MakOwner on 2013-08-13
I have a 10 x 2TB disk mdadm RAID5 volume.  I added 4 more 2 TB disks, grew the array and tried to resize the partition.
I ran into this:

```

resize2fs: /dev/md8: The combination of flex_bg and
	!resize_inode features is not supported by resize2fs.

```


A little googling shows this:
[http://serverfault.com/questions/419196/cant-resize2fs-combination-of-flex-bg-and-resize-inode](http://serverfault.com/questions/419196/cant-resize2fs-combination-of-flex-bg-and-resize-inode)

which leads to this:
[http://www.spinics.net/lists/linux-ext4/msg27511.html](http://www.spinics.net/lists/linux-ext4/msg27511.html)


Is there really no way to resize this filesystem?

---

### Post by MakOwner on 2013-10-17
I could find no way around this so I just blew the array away and rebuilt it.

I'm working with a couple of other arrays that I need to grow and I'm running into an issue where resize2fs is saying the volume is already maxed out, when it clearly isn't.

Is there a way to set up an array that *_will_* grow safely later?

I'm using ext4 file system on RAID5.

---

### Post by rubylaser on 2013-10-17
You may be running into the 16TB limit on your ext4 partitions if it was created without the 64bit flag. As a side note, a 14 drive RAID5 is a bit insane :)  If you fail a disk and need to resync, the ***LENGTHY*** restore time could very easily cause another disk to die and take out the whole array.  I'd strongly consider moving to a RAID6 unless this is just a backup, but with the cost of disks, I'd still have RAID6, because needed to transfer back over 16TB+ takes a long time over gigabit (good time to move to 10GBe or better Infiniband).  All this being said, my big home arrays are now on SnapRAID (still ext4 backed disks) or ZFS, so I haven't messed with >16TB ext4 volumes in a while.  

Those links you provided have the proper flags to create the filesystem so it can be resized later.  Or, you could look at XFS, but I shutter to suggest that, because I experienced corruption in the past the made the filesystems completely unmountable, so I've avoided it like the plague (it works great for many other people though).

---

### Post by MakOwner on 2013-10-17
> **rubylaser said:**
> You may be running into the 16TB limit on your ext4 partitions if it was created without the 64bit flag. As a side note, a 14 drive RAID5 is a bit insane :)  If you fail a disk and need to resync, the ***LENGTHY*** restore time could very easily cause another disk to die and take out the whole array.  I'd strongly consider moving to a RAID6 unless this is just a backup, but with the cost of disks, I'd still have RAID6, because needed to transfer back over 16TB+ takes a long time over gigabit (good time to move to 10GBe or better Infiniband).  All this being said, my big home arrays are now on SnapRAID (still ext4 backed disks) or ZFS, so I haven't messed with >16TB ext4 volumes in a while.  

Those links you provided have the proper flags to create the filesystem so it can be resized later.  Or, you could look at XFS, but I shutter to suggest that, because I experienced corruption in the past the made the filesystems completely unmountable, so I've avoided it like the plague (it works great for many other people though).

Even with RAID6 once you get to 15 or so 2TB disks you are still approaching an issue with recovery time on a disk failure.
Regarding xfs, I have used it before, but I have never seen a filesystem check complete -- even on a machine with 16GB of RAM it would exhaust all memory and the check would die.
I got lucky and never lost data with xfs, but I just got too nervous never being able to check the filesystem.
If I understand SnapRAID it won't present all the disks as one large volume, which is one of my requirements.

Is it the "-t huge" parameter that allows resize2fs to work?

---

### Post by rubylaser on 2013-10-18
> **MakOwner said:**
> Even with RAID6 once you get to 15 or so 2TB disks you are still approaching an issue with recovery time on a disk failure.
You are correct, that's why I either use Snapshot RAID (SnapRAID), so that the most I can lose even if I've lost all my parity disks is the data on the failed disk.  Each disk stands alone and is mountable by itself.  The version 5.0 of SnapRAID supports up to quadruple parity if you want to go crazy :) If I did this with ZFS, I would be breaking this volume up into (2) 10 disk RAIDz2 vdevs.  This would give give a good mix of performance and reliability.  All that being said, if this is for home media storage, SnapRAID makes a lot of sense.  I've stopped using mdadm at home for media storage (tv, movies, pictures, etc.) and use SnapRAID instead.  

> **MakOwner said:**
> Regarding xfs, I have used it before, but I have never seen a filesystem check complete -- even on a machine with 16GB of RAM it would exhaust all memory and the check would die.
I got lucky and never lost data with xfs, but I just got too nervous never being able to check the filesystem.
I've had similar experiences and even lost data with XFS in the past, that's why I said I would avoid it personally.

> **MakOwner said:**
> 
If I understand SnapRAID it won't present all the disks as one large volume, which is one of my requirements.
It won't by itself, but you can easily use AUFS or mhddfs to pool the disks as one big volume that you can share out via NFS, CIFS, or AFP just like you normally would.  Here's look at my backup server at home.  Note the /storage mountpoint.  That's a SnapRAID volume of the disks that can be seen above it.  I'm not trying to sway you away from mdadm, because it's awesome, but for large home storage, SnapRAID has worked great for me.   Another side benefit, is you'd never need to worry about growing over a 16TB filesystem like you ran into here, because each disk has it's own filesystem. If you are interested, I have a [tutorial for SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") including AUFS setup on my site. It's very easy to setup and maintain.

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       583G   41G  536G   7% /
udev            3.9G   12K  3.9G   1% /dev
tmpfs           1.6G  900K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  4.0K  3.9G   1% /run/shm
/dev/sdb1       2.7T  1.5T  1.3T  56% /media/SEA-Z3100YUU
/dev/sdc1       1.8T  486G  1.4T  27% /media/SEA-6YD1PU85
/dev/sdd1       1.8T  1.4T  369G  79% /media/SEA-5XW0U890
/dev/sde1       1.8T  1.3T  417G  77% /media/SEA-5YD2IO6D
/dev/sdf1       1.8T  1.4T  380G  79% /media/SEA-5YD179LK
/dev/sdg1       1.8T  1.3T  412G  77% /media/HIT-ML0220F30YUI98
/dev/sdh1       1.8T  380G  1.4T  22% /media/SEA-6YD0ZYT6
/dev/sdi1       1.8T  384G  1.4T  23% /media/SEA-5YD6N4HG
/dev/sdj1       1.8T  382G  1.4T  22% /media/SEA-6YD1E43T
/dev/sdk1       2.7T  1.5T  1.3T  56% /media/SEA-Z3100ZTE
none            14.4T  6.9T  7.5T  55% /storage

```

> **MakOwner said:**
> 
Is it the "-t huge" parameter that allows resize2fs to work?

You need to enable the 64bit option.  Here's a [post]("http://www.unix-ninja.com/kb/Formatting_Ext4_volumes_beyond_the_16TB_limit/") that covers the options.

---

### Post by MakOwner on 2013-10-24
Also, for anyone else googling or searching and finding this thread -- apparently, while the 64 bit version of Ubuntu ships with 64 bit tools for creating and mounting 64 bit ext4 filesystems, the resizefs binary does not.  
After a week of putzing around with various options while building a file system and trying to resize larger, I would get this message:
```

resize2fs 1.42 (29-Nov-2011)
resize2fs: New size too large to be expressed in 32 bits

```

---

### Post by david121 on 2013-12-03
**Does anyone happen to know whether newer versions of resize2fs can correctly resize to >16TB if the 64bit setting is present?**

I have a filesystem with the 64bit feature set:
**> sudo tune2fs -l /dev/mapper/tank-lode **
tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /lode
Filesystem UUID:          b9360c6d-3c49-489d-9156-61724d09c4f2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr dir_index filetype needs_recovery extent **64bit **flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              274700288
Block count:              4395199488
Reserved block count:     219759974
Free blocks:              1872823492
Free inodes:              259439354
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         2048
Inode blocks per group:   128
RAID stride:              128
RAID stripe width:        768
[...]

However, after I expanded the underlying logical volume to 32TB:
**> sudo lvextend --extents +100%FREE /dev/tank/lode**
  Extending logical volume lode to 32.75 TiB
  Logical volume lode successfully resized

I cannot seem to resize the filesystem properly:
**> sudo resize2fs /dev/mapper/tank-lode **
resize2fs 1.42 (29-Nov-2011)
resize2fs: /dev/mapper/tank-lode: The combination of flex_bg and
        !resize_inode features is not supported by resize2fs.

Does anyone know if this is corrected in newer (presumably devel) versions of e2fsprogs?  If so, is there a newer (or devel) e2fsprogs package that can be installed apt-get?  Apologies for not knowing how to look this up.

Many thanks for any insights!

---

### Post by jfolsom2 on 2013-12-04
You should really start a new thread for this question, but it looks like the bug may be fixed in the latest version of e2fsprogs. [https://launchpad.net/ubuntu/+source/e2fsprogs/1.42.8-1ubuntu1](https://launchpad.net/ubuntu/+source/e2fsprogs/1.42.8-1ubuntu1)

You haven't said what version of Ubuntu you are using, so it's hard to go looking for a PPA or Backport.


GoodLuck

---

