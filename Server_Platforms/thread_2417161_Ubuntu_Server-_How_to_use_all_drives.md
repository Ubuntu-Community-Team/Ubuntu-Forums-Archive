---
title: "Ubuntu Server- How to use all drives?"
date: 2019-04-21
forum: Server Platforms
---

### Post by ejach2000 on 2019-04-21
Hello,
I am running Ubuntu 18.04 on my home server.
I am also running Plex on the server, and it is working great.
I have about 8TB from 4 different drives (I think) installed on the machine, but I do not know how to access it.
When I run ```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```
I get:
[IMG]https://i.ibb.co/n6Bm0NG/dedotatedwam.jpg[/IMG]
So, as far as I can see, the drives are recognized as available.
I have been tinkering around with Ubuntu for a little while now with no difficulty, but when it comes to messing with storage and drives, I tend to hesitate a lot.
I want to be able to access all 4 drives at once in a single directory (if this is even possible).
This seems to be a simple fix, but I wanted to check here before I decided to do anything.
I can provide any additional information upon request.
Thanks!

---

### Post by TheFu on 2019-04-22
Some rules of thumb for storage:
* Always create at least 1 partition on a disk.
* Use GPT for the partition table whenever possible.
* Setup your primary storage in such a way that backups are easiest.
* Backups must be on separate physical storage.
* Don't ignore backups, ever.
* NEVER, NEVER, allocate 100% of the storage. Always leave 10-20% unallocated. This is extremely important on SSDs, but also important for HDDs, since it is very handy to have 10% left when an LV fills up. Then you can add a small amount to the LV (about 20 seconds and 1 command), that will prevent an outage while more/new storage is purchased.

So, from the data posted, it looks like you have 3 HDDs, each 3TB in size.  That is an unfortunate size, because the 3TB model from almost every vendor have a significantly higher failure rate than 4T, 6T, 8T, or 10T sized disks - like over 2x more failures.  To address this less-than-great-reliability, you NEED excellent backups.  Search for "backblaze disk failures" for their quarterly reports to validate my statements on 3TB disks.

Next, it appears that you've setup the first disk with a huge, single, partition, that holds /.  2.7TB for /.  That is unfortunate and makes backups harder.

What I would do is backup everything I couldn't loose, backup a list of manually installed packages, all system and personal settings, and all data, DBs, whatever else I couldn't lose, then
I world do a fresh, minimal, install using LVM on the main disk.  That should create a few partitions for booting and 1 for a logical volume about 2.6TB in size.  Then I'd use the power of LVM to reduce that LV to 25G for /.  Then I'd create a home-lv of about 50G in size, followed by a nextcloud-lv sized just a little larger than needed, perhaps 50G, and then 100G for the plex library and DB LV.

So, what's with all the logical volumes?  LVM stands for Logical Volume Manager.  It is a disk management system that allows easily adding storage, where it is needed, as it is needed, to running systems.  The LVs can cross physical HDD separations, though that isn't usually a good idea.  Making an LV larger than you can easily backup is NOT to be done.  Merging LVs across file systems can lead to total data loss on both disks, if one of those disks fails.  

Plex doesn't need to see all the Movies inside just 1 directory, nor TV shows, nor Music, nor Photos.  The Plex library can logically merge multiple Movie directories into a single view in the interface.  I have 4 disks in my plex library, each has Movies, TV, Videos, Music and Photo directories.

LVM doesn't include file systems, so you'll want to pick one that provides good performance, good flexibility.  For me, that was EXT4.  EXT4 file systems can be reduced using LVM commands. The other file system commonly used for large amounts of data is XFS.  XFS file systems do not support reduction, only expansion.

Do about 10 minutes of reading on disk partitioning and LVM on Linux systems.  It isn't hard, but extremely valuable for situations like yours. Also, work out how you will backup all the data.  Think about the time it would take to recreate all the media from your source materials.  Ripping my music CDs took me months of effort.  A backup of that data is pretty trivial and only costs the storage to hold the backups - so about $100/4TB.  I limit all my partitions/LVs to 4TB in size, because 4TB disks are what I use for backup storage.  When I got an 8TB disk (crazy deal!), I partitioned it into 2x4TB partitions, setup LVM on each with separate PVs, VGs, and LVs, then decided it would be used only as backup storage.  That was 3 yrs ago, and that backup disk has been working perfectly.  SMART data on all the storage devices are watched closely.  The SMART data has prompted me to swap SATA cables a few times, which limited any data corruption and drastically helped with performance since faults require re-transmission of the data.

Many people with large storage amounts choose to use ZFS for their data.  ZFS isn't ready for the OS or booting in Ubuntu, but for data, like media files, it would be worth considering. Think of ZFS as LVM+filesystems.

Both ZFS and LVM will let you create file systems that span across different physical disk.  I would strongly caution against doing this.  Many years ago, I lost 80% of my data because I'd expanded an LVM LV across 3 disks.  1 of those disks failed, so I lost data on all 3 disks. This was before I was good at backups.  

Please learn from my mistake. Design your solution with backups BEFORE doing anything else, please.

As for accessing the other disks, forget using any GUI.  You'll want to manually, in a shell, do everything.

Some reading:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

Some of that reading shows using LVM on entire disks without creating any partitions first. Please don't do this. There are reasons why you want a partition table and don't just want to slap LVM on an entire disk.  The same reasons apply for RAID storage, BTW.

I haven't mentioned most of the amazing features that LVM brings. Those can be learned later, as needed.  Just know that when it is time to replace a 3TB disk with an 8TB or 10TB disk, LVM has that covered. Moving LVs to new storage and removing the old physical disk is where LVM shines.  It is also really good for consistent backups. 

I left out lots of details. You can get those from the links provided. LVM is one of those things that you cannot add later. It needs to be added from the beginning.  However, LVM doesn't remove the need to understand booting, partitioning, for linux systems.  You still need to have an excellent understanding of those too.
As for manually mounting LVs, they work just like partitions work in the /etc/fstab file.  Where you might see /dev/sda3 inside the fstab file, you'd place the path to the canonical LVM device name.  That is usually /dev/{volume-group-name}/{logical-volume-name} . This is just as unique as using UUIDs, so there isn't any chance of the old time device rename issue that UUIDs solved.

One more thing.  You may have read about overlay file systems that merge other files systems into 1 large view.  Only home users touch those programs.  Enterprises do not.  Think about that.  Enterprises use ZFS and LVM all the time, daily, for the last 20 yrs (for LVM).  ZFS on Linux has been pretty good the last decade, but ZFS has some requirements that many home systems cannot meet.

Anyways, hope this was helpful in some way and that I didn't jump around too much.

---

### Post by TheFu on 2019-04-22
Please don't post images.  Use text copy/paste wrapped in "code" tags (see below). Many people pay for their data by the byte and it is easier for people trying to help to copy/paste specific lines to make points.

My plex/NAS system:

```
$ df -Th|grep /dev
/dev/sdb2                                    ext2      237M  150M   75M  67% /boot
/dev/mapper/istar--vg-root                   ext4      101G   74G   23G  77% /
/dev/mapper/istar--stuff-lv--tv              ext4      294G  100G  194G  35% /TV
/dev/mapper/istar--vg2-lv_media2             ext4      3.5T  3.5T   26G 100% /DD
/dev/mapper/istar--vg-lv_media               ext4      3.5T  3.5T   42G  99% /D
/dev/mapper/istar--vg2--back-lv_media2_back  ext4      3.6T  3.6T   39G  99% /misc/D5
/dev/mapper/istar--8TB-istar--back3--a       ext4      3.6T  3.5T  154G  96% /misc/b-D3
/dev/mapper/istar--8TB-istar--back3--b       ext4      3.6T  3.5T   97G  98% /misc/b-D4
/dev/sdf2                                    ext4      3.6T  3.6T   18G 100% /misc/b-D5
```

Nothing is perfect, including my setup above. ;(  
It uses legacy boot, not UEFI. The last 3 lines are backup storage.  If I were doing this fresh, I'd have D1, D2, D3, for primary storage and b-D1, b-D2, b-D3 for the backups.   The root-lv gets backed up to a different system, over the network, nightly, automatically, with versioning.  /TV/ is a temporary area, not backed up.  

sdf2 needs something, soon. Either I need to clean up some of that storage or buy more. My array has 2 open slots and there have been 8TB disk deals this week. I'd also mount the primary storage on /D1, /D2, /D3.  When I started all this, the case only supported 1 HDD and /D/ was clearly sufficient and easy to NFS mount to other systems here.  Changing those mount locations above means changing mounts and scripts on 5 other boxes too.

I'd also be more generic about VG names.  vg1, vg2, vg3, ... LV names are something I want to be descriptive.

Learn the pvs, vgs, and lvs commands. They provide a complete view.
```
$ sudo pvs
  PV         VG             Fmt  Attr PSize   PFree  
  /dev/sda3  istar-vg2      lvm2 a--    3.64t  94.04g
  /dev/sdb3  istar-vg       lvm2 a--    3.64t 928.00m
  /dev/sdc1  istar-stuff    lvm2 a--  298.09g  88.00m
  /dev/sdd1  istar-8TB      lvm2 a--    7.28t  14.03g
  /dev/sde3  istar-vg2-back lvm2 a--    3.64t  34.04g

$ sudo vgs
  VG             #PV #LV #SN Attr   VSize   VFree  
  istar-8TB        1   2   0 wz--n-   7.28t  14.03g
  istar-stuff      1   1   0 wz--n- 298.09g  88.00m
  istar-vg         1   3   0 wz--n-   3.64t 928.00m
  istar-vg2        1   1   0 wz--n-   3.64t  94.04g
  istar-vg2-back   1   1   0 wz--n-   3.64t  34.04g

$ sudo lvs 
  LV             VG             Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  istar-back3-a  istar-8TB      -wi-ao----   3.65t                                                    
  istar-back3-b  istar-8TB      -wi-ao----   3.62t                                                    
  lv-tv          istar-stuff    -wi-ao---- 298.00g                                                    
  lv_media       istar-vg       -wi-ao----   3.53t                                                    
  root           istar-vg       -wi-ao---- 102.27g                                                    
  swap_1         istar-vg       -wi-ao----   3.61g                                                    
  lv_media2      istar-vg2      -wi-ao----   3.55t                                                    
  lv_media2_back istar-vg2-back -wi-ao----   3.60t    
```   


Anyways, hope this is helpful.

---

### Post by ejach2000 on 2019-04-22
Thank you once again for the detailed replies!
I will use some of your methods once I have some free time and tell you how it goes!

---

### Post by slickymaster on 2019-04-22
*Thread moved to **Server Platforms**.*

---

### Post by aljames2 on 2019-04-23
@TheFu, thanks for sharing all of this info on additional storage utilization.  I use LVM, its great.  I learned a few things here as well :)

---

