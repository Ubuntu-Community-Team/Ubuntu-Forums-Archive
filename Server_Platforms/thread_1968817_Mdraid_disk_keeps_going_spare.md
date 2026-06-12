---
title: "Mdraid disk keeps going spare"
date: 2012-04-29
forum: Server Platforms
---

### Post by movieman on 2012-04-29
I have an mdraid RAID1 in my server with two 3TB disks. I noticed yesterday that it's only running on one of the disks and the other is marked as a spare instead.

I rebooted and it tried to sync, but got a read error on the active disk. It later said 'recovery done' but the good disk is still marked as a spare rather than an active part of the RAID.

Any idea how I recover this? If the active disk has bad sectors then I clearly need to sync it to the good disk and let that take over so I can replace the bad one. But I can't, because it keeps dropping that disk from the RAID. Which is particularly stupid because a RAID1 with only one disk is useless.

sudo mdadm --detail /dev/md0

/dev/md0:
        Version : 01.02
  Creation Time : Thu Jun 30 21:47:15 2011
     Raid Level : raid1
     Array Size : 2930262872 (2794.52 GiB 3000.59 GB)
  Used Dev Size : 5860525744 (5589.03 GiB 6001.18 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Apr 29 10:48:56 2012
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           Name : kirin:0  (local to host kirin)
           UUID : c05cb1b1:34b811e8:bde06c05:64707862
         Events : 4389298

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       65        1      active sync   /dev/sde1

       0       8       49        -      spare   /dev/sdd1

cat /proc/mdstat:

mark@kirin:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd1[0](S) sde1[1]
      2930262872 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>

How can I possibly fix this if it won't let me sync to another disk because it gets a read error?

---

### Post by movieman on 2012-04-29
BTW, this RAID was fine as of a few weeks ago. Somehow it's decided to keep the bad disk in the RAID but drop the good one, and refuse to sync over to the good one. 

This is precisely the opposite of anything I would regard as sensible behaviour, because the good one probably had good copies of the blocks it can't read on the bad disk.

---

### Post by movieman on 2012-06-15
So, to answer my own question:

If mdraid has to resync between disks and it finds a bad block on the online disk, rather than just skipping that block and copying the rest, it stops syncing and flags the good disk as a spare. Even if the only reason it's resyncing is because the system didn't shut down cleanly and the last write went to the bad disk.

This is clearly stupid and defeats the point of having a RAID, but it's what it does in 10.04. Perhaps it's smarter in later kernel versions.

In the end I had to remove the good disk from the RAID, create a new RAID with only the good disk in it, manually copy over all the files from the bad disk to the good one, then replace the bad disk with a new one and add it to the new RAID.

Anyone know of a robust software RAID implementation on Linux? I looked at switching to ZFS, but it doesn't understand disks with 4k blocks and can't export files over NFS.

---

### Post by rubylaser on 2012-06-15
> **movieman said:**
> So, to answer my own question:

If mdraid has to resync between disks and it finds a bad block on the online disk, rather than just skipping that block and copying the rest, it stops syncing and flags the good disk as a spare. Even if the only reason it's resyncing is because the system didn't shut down cleanly and the last write went to the bad disk.

This is clearly stupid and defeats the point of having a RAID, but it's what it does in 10.04. Perhaps it's smarter in later kernel versions.

In the end I had to remove the good disk from the RAID, create a new RAID with only the good disk in it, manually copy over all the files from the bad disk to the good one, then replace the bad disk with a new one and add it to the new RAID.

Anyone know of a robust software RAID implementation on Linux? I looked at switching to ZFS, but it doesn't understand disks with 4k blocks and can't export files over NFS.

I'm sorry I missed your post earlier. I likely could have helped you with this without all of the steps you went through. But, without seeing your old metadata info from each disk and your smartctl info, I can't give you a definitive reason for the behavior you where seeing other than to say it is not the proper way for mdadm to perform even on 10.04. mdadm is very robust and very proven on all Linux distros.  The [Linux RAID mailing list]("http://vger.kernel.org/vger-lists.html#linux-raid") is also a great place to get problems like this answered in the future.

ZFS on Linux works fine with 4k disks, you just need to create your array with the [ashift=12]("http://zfsonlinux.org/faq.html#HowDoesZFSonLinuxHandlesAdvacedFormatDrives") option and it will be properly aligned for 4k disks (You can even use 4K aligned arrays in FreeBSD or even Solaris if you use and modified zpool binary or use FreeBSD to create a 4K aligned array and then export it).  Also, you [can export]("http://zfsonlinux.org/faq.html#HowDoISetupShares") NFS shares with ZFS on Linux just like you would with Solaris.

---

### Post by movieman on 2012-06-15
> **rubylaser said:**
> But, without seeing your old metadata info from each disk and your smartctl info, I can't give you a definitive reason for the behavior you where seeing other than to say it is not the proper way for mdadm to perform even on 10.04

At boot it would sit there resyncing for hours and then when it got to approx 75% it reported a bad block, stopped resyncing and marked the disk as a spare. So clearly the bad block was making it stop, if there's a way to configure it not to do that it would be good to know.

> ZFS on Linux works fine with 4k disks, you just need to create your array with the [ashift=12]("http://zfsonlinux.org/faq.html#HowDoesZFSonLinuxHandlesAdvacedFormatDrives") option and it will be properly aligned for 4k disks

I tried that, but it said that was an invalid option. I presume that it's not supported on the version of ZFS that comes with 10.04.

I also tried exporting the files using the ZFS NFS option and nothing could see them. It's possible that the kernel can't handle ZFS and the kernel NFS server exporting things at the same time.

---

### Post by rubylaser on 2012-06-15
> **movieman said:**
> At boot it would sit there resyncing for hours and then when it got to approx 75% it reported a bad block, stopped resyncing and marked the disk as a spare. So clearly the bad block was making it stop, if there's a way to configure it not to do that it would be good to know.

You need to remap the bad sector, you can either write to that sector with dd, mark it with badblocks + an fsck or just dd to write zeros to the whole drive. Here are some other [directions]("http://www.sjvs.nl/?p=12").

> **movieman said:**
> I tried that, but it said that was an invalid option. I presume that it's not supported on the version of ZFS that comes with 10.04.

I also tried exporting the files using the ZFS NFS option and nothing could see them. It's possible that the kernel can't handle ZFS and the kernel NFS server exporting things at the same time.

This support was added in version 0.6.0-rc5.  zfsonlinux has a repository, so all versions of Ubuntu will run the same version of it if they are up to date. Since July of 2011 this option has been supported on 10.04.  I use all of these options just fine on my 10.04 test server at home (including NFS exports).

---

### Post by movieman on 2012-06-15
Strange. It's possible that I typed the command wrong, but I was following instructions from the web and it rejected them.

BTW, according to this thread on the mailing list you pointed me to:

[http://marc.info/?l=linux-raid&m=131435966516526&w=2](http://marc.info/?l=linux-raid&m=131435966516526&w=2)

The behaviour I saw with the RAID refusing to resync is apparently by design.

I honestly can't see why anyone thought that it was a good design, as the recommended solution appears to be 'manually copy everything to the other disk as the resync would have done by itself if we didn't force it to fail'.

---

### Post by rubylaser on 2012-06-15
That doesn't seem to be the same scenario.  That poster removed the faulty disk from the area.  Unfortunately, the only good remaining disk had bad blocks as well.  Since this was the only copy of the data, the only way to sync it over was to copy it.  In your case, you had 1 good disk and 1 disk with a few bad blocks.  I would guess that the bad disk's event counter was higher than the good disk, so that's way mdadm would have tried to use that for the sync (it was a newer copy).

Maybe I'm misunderstanding your original issue though :)

---

