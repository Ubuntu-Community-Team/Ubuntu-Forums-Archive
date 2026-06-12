---
title: "Advice on migrating a RAID"
date: 2009-01-22
forum: Server Platforms
---

### Post by dcollamore on 2009-01-22
I currently have a basic fileserver running 7.10 with three 250GB SATA drives in a software RAID configuration - each individual drive is partitioned like so:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d2116

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  fd  Linux raid autodetect
/dev/sdb2            1217       30163   232516777+  fd  Linux raid autodetect
/dev/sdb3   *       30164       30175       96390   fd  Linux raid autodetect
/dev/sdb4           30176       30401     1815345   fd  Linux raid autodetect

...and the RAID configuration is as follows:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid0 sdb4[0] sdc4[1]
      3630464 blocks 64k chunks
      
md0 : active raid1 sda2[0] sdc3[2] sdb3[1]
      96320 blocks [3/3] [UUU]
      
md2 : active raid5 sda4[0] sdc2[2] sdb2[1]
      464953088 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid1 sda1[0] sdc1[2] sdb1[1]
      9767424 blocks [3/3] [UUU]
      
unused devices: <none>

md0 is a mirrored 100MB /boot partition
md1 is a mirrored 10GB / partition
md2 is a RAID5 437GB /home partition
md3 is unused

Now my goal is to migrate this intact to three 1TB drives and grow md2 to take advantage of the additional storage space.  It's not a mission critical server, so I'm open to experimentation, but I am resource limited; I have no additional storage devices to shuffle data between.

My thought was to dd each 250GB to it's corresponding 1TB drive, and use parted to grow the *db2 partition to fill the drive.  Will this work?  Or is there a better way to accomplish this?

Thanks in advance for any input!

---

### Post by Cracauer on 2009-01-22
Why wouldn't you just create the raid and filesystem on the new drives and rsync everything over?

---

### Post by dcollamore on 2009-01-22
I would like to, it would be much easier, but the situation I'm in won't allow for it.  I don't have enough SATA ports in the system to hang both arrays, I don't have another SATA controller card, I don't have any other HDD's available to act as a go-between, and I don't have another system to hang either array in to rsync over.  I have only the one tower, and the six drives.

---

### Post by Cracauer on 2009-01-22
> **dcollamore said:**
> I would like to, it would be much easier, but the situation I'm in won't allow for it.  I don't have enough SATA ports in the system to hang both arrays, I don't have another SATA controller card, I don't have any other HDD's available to act as a go-between, and I don't have another system to hang either array in to rsync over.  I have only the one tower, and the six drives.

Ah. Yeah my old friend SATA and it's limitations...

I just moved my server to new drives, in about the same situation. I connected the new drives to a spare socket 939 system that I booted diskless, then make the raid and filesystems on the new drives, then rsynced everything. The good thing about this is that your main machine stays up, cronjobs and all. Then, when ready to move I killed all scheduler everything, did a quick refresh rsync over the existing one and swapped the drives.

You can do what you say, you can do the drives one by one, including partition tables. But you must have mounted all your filesystems readonly for that stunt. On *&@^*(@ Linux that's much easier said than done since even when you boot into single user mode they mount the filesystem rw by default. Realistically you should probably do this from a boot CD/DVD and don't mount any of the filesystems.

---

### Post by dcollamore on 2009-01-24
Okay, I didn't solve it exactly the way I was expecting, but solved nonetheless.  I picked up 3 cheap SATA external USB enclosures, did a fresh install of 8.04LTS on a newly created RAID with the new drives, mounted my previous array externally and rsync'd the data over.  Done and done.  Thanks for the input!

---

