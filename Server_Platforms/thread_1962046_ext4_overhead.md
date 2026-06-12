---
title: "ext4 overhead?"
date: 2012-04-20
forum: Server Platforms
---

### Post by MakOwner on 2012-04-20
Setting up a new software array under 12.04 LTS (64 bit) beta and noticed some things.

I have an array of 8x750GB drives in raid 5.
```

# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md2 : active raid5 sdi1[8] sdh1[6] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdc1[1] sdb1[0]
      5128005120 blocks super 1.2 level 5, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]
      
unused devices: <none>

```
This produces a 5251.1GB md device
```

# fdisk -l /dev/md2

Disk /dev/md2: 5251.1 GB, 5251077242880 bytes
2 heads, 3 sectors/track, 1709335040 cylinders, total 10256010240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 3670016 bytes
Disk identifier: 0x8bef43f3

```

When I create an ext4 filesystem, however
```

# mke2fs -j -L md2p1 -m 1 -T ext4 -U 2d67f5c3-83a4-41a9-a41f-5af082f039c7 /dev/md2p1 
mke2fs 1.42 (29-Nov-2011)
Filesystem label=md2p1
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=896 blocks
134217728 inodes, 536870015 blocks
5368700 blocks (1.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
16384 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done  

```

I only get a 2TB filesystem.
```

# df -h
Filesystem                 Size  Used Avail Use% Mounted on
:/media/md0p1/Movies       9.5T  6.8T  2.2T  76% /mnt
/dev/md2p1                 2.0T   31G  2.0T   2% /media/md2p1

```

My questions are this: 31 GB overhead seems a little steep on a 2TB filesystem and note the NFS mount point - it was prepared in exactly the same way using 8x1.5TB disks, and it shows a filesystem that is well beyond 2TB in size.  

Is this a restriction in the beta, and where is the 31GB of overhead coming from?

---

### Post by rubylaser on 2012-04-20
Why did you put a partition on top of your mdadm array?  You should add the filesystem right on top of the array like this.

```
mkfs.ext4 -b 4096 -E stride=128,stripe-width=896 /dev/md2
```

If you chose to use ext2/3/4 you should also be aware of reserved space. By default ext2/3/4 will reserve 5% of the drives space, which only root is able to write to. This is done so a user cannot fill the drive and prevent critical daemons writing to it, but 5% of a large RAID array which isn&#8217;t going to be written to by critical daemons anyway, is a lot of wasted space. Set the reserved space to 0%, using tune2fs:

```
tune2fs -m 0 /dev/md2
```

That should get you the proper amount of space. You'd just mount /dev/md2 like this in /etc/fstab.
```
/dev/md2        /media/md2            ext4        defaults        0        0
```

---

### Post by MakOwner on 2012-04-20
> **rubylaser said:**
> Why did you put a partition on top of your mdadm array?  You should add the filesystem right on top of the array like this.

```
mkfs.ext4 -b 4096 -E stride=128,stripe-width=896 /dev/md2
```

If you chose to use ext2/3/4 you should also be aware of reserved space. By default ext2/3/4 will reserve 5% of the drives space, which only root is able to write to. This is done so a user cannot fill the drive and prevent critical daemons writing to it, but 5% of a large RAID array which isn’t going to be written to by critical daemons anyway, is a lot of wasted space. Set the reserved space to 0%, using tune2fs:

```
tune2fs -m 0 /dev/md2
```

That should get you the proper amount of space. You'd just mount /dev/md2 like this in /etc/fstab.
```
/dev/md2        /media/md2            ext4        defaults        0        0
```

The 31GB doesn't appear to be reserved space - I initially created the filessystem using the defaults for ext4 and that's 5% reserved.  I reduced in this last format to 1% (and that's why I specified the UUID to match the previous format as it was already in fstab.)


To the question of why I'm partitioning the raid device ...  Well, habit I guess.   Is it really best practice to build a filesystem on a raw device and not a partition?  Everything I have read seems to indicate that it's better to use partitions.  A little silly maybe in this case where I want a single filesystem. 

I tried once using raw disk devices as the components in a software array.  Worked great until I had to replace a failed drive. Matching the byte count of a physical device is more difficult than matching a software defined partition.  I have just been carrying that over.

I think what you are saying is the limitation is in fdisk, though, correct?

---

### Post by rubylaser on 2012-04-20
> **MakOwner said:**
> The 31GB doesn't appear to be reserved space - I initially created the filessystem using the defaults for ext4 and that's 5% reserved.  I reduced in this last format to 1% (and that's why I specified the UUID to match the previous format as it was already in fstab.)


To the question of why I'm partitioning the raid device ...  Well, habit I guess.   Is it really best practice to build a filesystem on a raw device and not a partition?  Everything I have read seems to indicate that it's better to use partitions.  A little silly maybe in this case where I want a single filesystem. 

I tried once using raw disk devices as the components in a software array.  Worked great until I had to replace a failed drive. Matching the byte count of a physical device is more difficult than matching a software defined partition.  I have just been carrying that over.

I think what you are saying is the limitation is in fdisk, though, correct?

Yes, you're running into the need for a GPT partition so you can go over the 2TB mark.  You'd need to use parted to make a partition larger than 2TB.  If you didn't put a partition on top of the array, this would not be an issue (unless you're individual disks where larger than 2TB, then you'd still need to use parted to make GPT partitions on them).

It is a best practice to build the filesystem on top of the raw mdadm device.  I build my arrays out of disk partitions (this is a common practice).  So, your array would be built out disk partitions like it is currently, but there's no need for a partition on top of the array.  I hope I explained that well enough so that you understand what I mean :)  Take a look at my [mdadm directions]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") if this was confusing.

---

### Post by iponeverything on 2012-04-20
> It is a best practice to build the filesystem on top of the raw mdadm device. I build my arrays out of disk partitions (this is a common practice). So, your array would be built out disk partitions like it is currently, but there's no need for a partition on top of the array. 

I learned something new..

---

### Post by rubylaser on 2012-04-20
Great :)  The only other thing that makes sense to put on top of an mdadm array if you need it is LVM for multiple partition support.  But, if you just want one big volume, put the filesystem right on top of the array.

---

### Post by MakOwner on 2012-04-20
> **rubylaser said:**
> Yes, you're running into the need for a GPT partition so you can go over the 2TB mark.  You'd need to use parted to make a partition larger than 2TB.  If you didn't put a partition on top of the array, this would not be an issue (unless you're individual disks where larger than 2TB, then you'd still need to use parted to make GPT partitions on them).

It is a best practice to build the filesystem on top of the raw mdadm device.  I build my arrays out of disk partitions (this is a common practice).  So, your array would be built out disk partitions like it is currently, but there's no need for a partition on top of the array.  I hope I explained that well enough so that you understand what I mean :)  Take a look at my [mdadm directions]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") if this was confusing.


Thanks.  I was doing this from memory -- I have lost my procedure document for doing this.  I remember using parted instead of fdisk now for this very reason.  Just creating the ext4 filesystem on the raw device works with no partitioning.  However I now have a 73GB consumed instead of 31GB ...

Not that I'm complaining, I'm just now curious as to why - is it because of blocksize space loss? df is smart enough to figure that out?

---

### Post by MakOwner on 2012-04-20
> **rubylaser said:**
> Great :)  The only other thing that makes sense to put on top of an mdadm array if you need it is LVM for multiple partition support.  But, if you just want one big volume, put the filesystem right on top of the array.

TIL.

I have other arryas set up on 10.04 LTS, this one is on 12.04 LTS beta 2.
Is there any danger/issue in taking an array backwards to an earlier version of mdadm?  Any idea if it will even work?




And in an effort to add at least some minor information to the topic, here's a one liner to add the new filesystem to your fstab:

echo UUD=`blkid /dev/md2 | cut -f3 -d= | cut -f2 -d\"` /mnt ext4 defaults 0 0 >> /etc/fstab

---

### Post by rubylaser on 2012-04-20
> **MakOwner said:**
> TIL.

I have other arryas set up on 10.04 LTS, this one is on 12.04 LTS beta 2.
Is there any danger/issue in taking an array backwards to an earlier version of mdadm?  Any idea if it will even work?




And in an effort to add at least some minor information to the topic, here's a one liner to add the new filesystem to your fstab:

echo UUD=`blkid /dev/md2 | cut -f3 -d= | cut -f2 -d\"` /mnt ext4 defaults 0 0 >> /etc/fstab

No, there's no danger in going backwards, but you will want to be running the same version or a newer version of mdadm.  It looks like 12.04 uses mdadm version 3.2.3.  10.04 uses 2.6.8, so you'll want to upgrade to a version that at least supports your 1.2 version metadata like 3.1.4 although, the same version would be better.

---

### Post by rubylaser on 2012-04-20
> **MakOwner said:**
> Thanks.  I was doing this from memory -- I have lost my procedure document for doing this.  I remember using parted instead of fdisk now for this very reason.  Just creating the ext4 filesystem on the raw device works with no partitioning.  However I now have a 73GB consumed instead of 31GB ...

Not that I'm complaining, I'm just now curious as to why - is it because of blocksize space loss? df is smart enough to figure that out?

What's the output of these?
```
df -h
du -h /mnt
```

---

### Post by MakOwner on 2012-04-20
> **rubylaser said:**
> What's the output of these?
```
df -h
du -h /mnt
```

I've already blowing test data onto the array.
I'll run du next time I rebuild, but the df -h showed 73GB used with no data on the filesystem.

BTW - those guides/howtos you have done are *excellent*.
Kudos.

---

### Post by rubylaser on 2012-04-20
> **MakOwner said:**
> I've already blowing test data onto the array.
I'll run du next time I rebuild, but the df -h showed 73GB used with no data on the filesystem.

BTW - those guides/howtos you have done are *excellent*.
Kudos.

Thanks :)

---

### Post by MakOwner on 2012-04-20
> **rubylaser said:**
> What's the output of these?
```
df -h
du -h /mnt
```

I used your calculation to optimize the filesystem.  
Array
```

/dev/md3:
        Version : 00.90
  Creation Time : Fri Apr 20 15:36:31 2012
     Raid Level : raid5
     Array Size : 5128021248 (4890.46 GiB 5251.09 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Fri Apr 20 15:36:31 2012
          State : clean, degraded, recovering
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 9dc9f293:50915f0d:019e8c68:2a546cbd (local to host)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       81        1      active sync   /dev/sdf1
       2       8       33        2      active sync   /dev/sdc1
       3       8       97        3      active sync   /dev/sdg1
       4       8       49        4      active sync   /dev/sdd1
       5       8      113        5      active sync   /dev/sdh1
       6       8       65        6      active sync   /dev/sde1
       8       8      129        7      spare rebuilding   /dev/sdi1


```

mke2fs command
```

# mke2fs -b 4096 -j -m 0 -L md3 -T ext4 -E stride=16,stripe-width=112 /dev/md3
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=md3
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=16 blocks, Stripe width=112 blocks
320503808 inodes, 1282005312 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
39124 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```


df -h now looks like this:
```

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md3              4.8T  190M  4.8T   1% /mnt

```


190M is much less than 30 or 70 GB ...


Another generla question -- when assembling the array, and using multiple ports/port multiplers, is it better to alternate volumes between controllers/pms or do them in the order in which they are discovered by the OS?


After comparing the physical connection and the device names in the OS, I used this command to alternate the disks between ports.  

```

mdadm --create --verbose /dev/md3 --level=5 --raid-devices=8 /dev/sdb1 /dev/sdf1 /dev/sdc1 /dev/sdg1 /dev/sdd1 /dev/sdh1 /dev/sde1 /dev/sdi1

```

Is this any better or worse than doing them in b,c,d,e,f,g,h,i order?

---

### Post by rubylaser on 2012-04-20
> **MakOwner said:**
> I used your calculation to optimize the filesystem.  
Array
```

/dev/md3:
        Version : 00.90
  Creation Time : Fri Apr 20 15:36:31 2012
     Raid Level : raid5
     Array Size : 5128021248 (4890.46 GiB 5251.09 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Fri Apr 20 15:36:31 2012
          State : clean, degraded, recovering
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 9dc9f293:50915f0d:019e8c68:2a546cbd (local to host)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       81        1      active sync   /dev/sdf1
       2       8       33        2      active sync   /dev/sdc1
       3       8       97        3      active sync   /dev/sdg1
       4       8       49        4      active sync   /dev/sdd1
       5       8      113        5      active sync   /dev/sdh1
       6       8       65        6      active sync   /dev/sde1
       8       8      129        7      spare rebuilding   /dev/sdi1


```

mke2fs command
```

# mke2fs -b 4096 -j -m 0 -L md3 -T ext4 -E stride=16,stripe-width=112 /dev/md3
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=md3
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=16 blocks, Stripe width=112 blocks
320503808 inodes, 1282005312 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
39124 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```


df -h now looks like this:
```

# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md3              4.8T  190M  4.8T   1% /mnt

```


190M is much less than 30 or 70 GB ...


Another generla question -- when assembling the array, and using multiple ports/port multiplers, is it better to alternate volumes between controllers/pms or do them in the order in which they are discovered by the OS?


After comparing the physical connection and the device names in the OS, I used this command to alternate the disks between ports.  

```

mdadm --create --verbose /dev/md3 --level=5 --raid-devices=8 /dev/sdb1 /dev/sdf1 /dev/sdc1 /dev/sdg1 /dev/sdd1 /dev/sdh1 /dev/sde1 /dev/sdi1

```

Is this any better or worse than doing them in b,c,d,e,f,g,h,i order?

The good news is neither is wrong. mdadm does not care at all about disk order, it uses the UUID stored in the superblock on each disk to assemble the array.  So the way you did it is just fine.  

It is a good idea to document your create order if your array ever gets so goofed up that you have to run mdadm create again with the assume-clean flag.  Just copy that line above and save it in a text file somewhere safe as the ultimate fallback backup option :0

---

### Post by MakOwner on 2012-04-20
> **rubylaser said:**
> The good news is neither is wrong. mdadm does not care at all about disk order, it uses the UUID stored in the superblock on each disk to assemble the array.  So the way you did it is just fine.  

It is a good idea to document your create order if your array ever gets so goofed up that you have to run mdadm create again with the assume-clean flag.  Just copy that line above and save it in a text file somewhere safe as the ultimate fallback backup option :0

Ah.. so, falling on the side of simplicity, it would be better to simply use the OS sort order of the devices.  I'm all for making things follow the path of least resistance.

---

### Post by rubylaser on 2012-04-20
> **MakOwner said:**
> Ah.. so, falling on the side of simplicity, it would be better to simply use the OS sort order of the devices.  I'm all for making things follow the path of least resistance.

I always just build the array based on their order in Debian/Ubuntu.

---

### Post by MakOwner on 2012-04-21
Marked the thread as solved - the final answer is I didn't pay attention and used fdisk where I shouldn't have and learned how to optimize the filesystem for an mdamd array - thanks to Rubylaser.

---

### Post by rubylaser on 2012-04-21
> **MakOwner said:**
> Marked the thread as solved - the final answer is I didn't pay attention and used fdisk where I shouldn't have and learned how to optimize the filesystem for an mdamd array - thanks to Rubylaser.

No problem, I'm glad you got it working correctly and are not losing a significant chunk of space :)

---

### Post by MakOwner on 2012-04-29
> **rubylaser said:**
> The good news is neither is wrong. mdadm does not care at all about disk order, it uses the UUID stored in the superblock on each disk to assemble the array.  So the way you did it is just fine.  

It is a good idea to document your create order if your array ever gets so goofed up that you have to run mdadm create again with the assume-clean flag.  Just copy that line above and save it in a text file somewhere safe as the ultimate fallback backup option :0

I really didn't want to revive this thread, but hope Rubylaser is watching this --  When creating the filesystem directly ont he md device without partitioning, do you see complaints at boot time about an unrecognized partition on the md device?

---

### Post by rubylaser on 2012-04-29
No because there shouldn't be a partition on the md device unless some remnants of your previous setup are still remaining.  What's the output of this?

```
fdisk -l
```

Is this showing up in dmesg at boot?  Is is stalling the boot process?

---

### Post by MakOwner on 2012-04-29
> **rubylaser said:**
> No because there shouldn't be a partition on the md device unless some remnants of your previous setup are still remaining.  What's the output of this?

```
fdisk -l
```

Is this showing up in dmesg at boot?  Is is stalling the boot process?

I have cut a lot out, there are 9 valid partition tables.
8 of them make up /dev/md3

```

Disk /dev/md3 doesn't contain a valid partition table

```

This pops up on the screen during boot, very briefly and is in dmesg
```

[   23.043472] md/raid:md3: raid level 5 active with 8 out of 8 devices, algorithm 2
[   23.043557] md3: detected capacity change from 0 to 5251093757952
[   23.047476]  md3: unknown partition table
[   23.293038] EXT4-fs (md3): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by rubylaser on 2012-04-29
This is a side effect of a kernel change years ago to allow any block device to be partitioned and
merely indicates that no partition table was found on your md device.  It's normal. It would be nice if they suppressed this error with md devices. The good news is that everything is fine.  You don't need a partition on that device as I mentioned, so all is well :)

---

