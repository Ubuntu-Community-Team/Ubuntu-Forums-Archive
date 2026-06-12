---
title: "ZFS Mirrored to Raidz2 Migration"
date: 2016-09-08
forum: Server Platforms
---

### Post by Soon_Yew on 2016-09-08
I currently have Ubuntu server 14.04 installed on a RAID array plus another two 3TB Western Digital (WD) drives in a Mirrored ZFS pool. Some time ago one of the 3TB drives failed and while I sent that for RMA I bought a replacement drive to restore the ZFS pool. Now I plan to get another 3TB drive and using the returned RMA drive, migrate the Mirrored pool to a RAIDz2 setup. So before I proceed, I was hoping someone can tell me if my planned steps and codes below is correct before I run and screw up stuff.
The general idea is to create two sparse files and using a loop to create 'dummy' drives to create the new Raidz2 pool, degrade it by removing the 'dummy' drives and migrate first the data, then re-purpose each drive from the old pool to the new pool. The sites which I used as reference is at the bottom. Just assume I am running at root for all the codes below:


Steps:
1. Identify the current drives installed (showing below without /dev/sdf which would be the new 3TB drive I will need to get and install)
```

lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda           8:0    0 298.1G  0 disk
&#9492;&#9472;sda1        8:1    0 298.1G  0 part
  &#9492;&#9472;md0       9:0    0   298G  0 raid1
    &#9500;&#9472;md0p1 259:0    0     1K  0 md
    &#9500;&#9472;md0p2 259:1    0 223.5G  0 md    /
    &#9492;&#9472;md0p5 259:2    0  74.5G  0 md    [SWAP]
sdb           8:16   0 298.1G  0 disk
&#9492;&#9472;sdb1        8:17   0 298.1G  0 part
  &#9492;&#9472;md0       9:0    0   298G  0 raid1
    &#9500;&#9472;md0p1 259:0    0     1K  0 md
    &#9500;&#9472;md0p2 259:1    0 223.5G  0 md    /
    &#9492;&#9472;md0p5 259:2    0  74.5G  0 md    [SWAP]
sdc           8:32   0   2.7T  0 disk
&#9500;&#9472;sdc1        8:33   0   2.7T  0 part
&#9492;&#9472;sdc9        8:41   0     8M  0 part
sdd           8:48   0   2.7T  0 disk
&#9500;&#9472;sdd1        8:49   0   2.7T  0 part
&#9492;&#9472;sdd9        8:57   0     8M  0 part
sde           8:64   0   2.7T  0 disk
&#9492;&#9472;sde1        8:65   0     2T  0 part

```


and the current Zpool


```

zpool status
pool: zpool1
state: ONLINE
status: Some supported features are not enabled on the pool. The pool can
        still be used, but some features are unavailable.
action: Enable all features using 'zpool upgrade'. Once this is done,
        the pool may no longer be accessible by software that does not support
        the features. See zpool-features(5) for details.
  scan: scrub repaired 0 in 8h5m with 0 errors on Mon Sep  5 10:05:54 2016
config:


        NAME                                          STATE     READ WRITE CKSUM
        zpool1                                        ONLINE       0     0     0
          mirror-0                                    ONLINE       0     0     0
            ata-WDC_WD30EZRX-xxxxxxx_WD-SNxxxxxxxxxxx ONLINE       0     0     0
            ata-WDC_WD30EZRX-xxxxxxx_WD-SNxxxxxxxxxxx ONLINE       0     0     0

```


From this I know:
  sda & sdb - ubuntu install
  sdc - 1 of 2 drives for the Zpool
  sdd - 2 of 2 drives for the zpool
  sde - New 3TB drive no.1 (a badly formated drive but is not in use anyway)
  sdf - New 3TB drive no.2 (once it is actually installed)
As a precaution and as recommended I will run 'Parted' to delete all partitions and confirm they are GPT labelled before mounting any of the drives in the new pool. zpool1 is the old Mirrored ZFS pool, while the new RAIDz2 ZFS pool will be called zpool2. Again as recommended I will be mounting whole drives and not partitions.


2. Create 2 sparse files and mount them as 3TB drives
```

dd if=/dev/zero of=disk1.img bs=1 count=0 seek=3T
dd if=/dev/zero of=disk2.img bs=1 count=0 seek=3T
mount -o loop disk1.img /dev/loop1
mount -o loop disk2.img /dev/loop2

```


3. Create using the 2 new 3TB drives and 2 sparse files to create a new zpool in RAIDz2 (zpool2) with 4k alignment
```

zpool create -o ashift=12 zpool2 raidz2 /dev/loop1 /dev/loop2 /dev/sde /dev/sdf

```


4. Degrade the new RAIDz2 pool by removing and deleting the two sparse files
```

zpool offline zpool2 /dev/loop1 && umount /dev/loop1 && rm disk1.img
zpool offline zpool2 /dev/loop2 && umount /dev/loop2 && rm disk2.img

```


5. Copy all data from old Mirrored ZFS pool into degraded RAIDz2 using rsync to leverage the checksum verification used by rsync
```

rsync -av /zpool1/ /zpool2/

```


6. Take offline one of the old Mirrored ZFS pool 3TB disks and replace into the new RAIDz2. Delete all partitions before replacing. Wait for resilvering to complete.
```

zpool offline zpool1 /dev/sda
zpool replace zpool2 /dev/loop1 /dev/sda

```


7. Destroy the old Mirrored ZFS pool and replace into new RAIDz2.  Delete all partitions before replacing. Wait for resilvering to complete.
```

zpool destroy zpool1
zpool replace zpool2 /dev/loop2 /dev/sdb

```


Did I miss anything? Is my codes wrong or did I missed any steps? 
The biggest risk to my data during this migration from my view is during steps 6 and 7 as I move to destroy the original pool and re-purpose the drives. 


[http://docs.oracle.com/cd/E19253-01/819-5461/gazgd/index.html](http://docs.oracle.com/cd/E19253-01/819-5461/gazgd/index.html)
[https://ubuntuforums.org/showthread.php?t=1576011](https://ubuntuforums.org/showthread.php?t=1576011)
[https://blogs.oracle.com/zhangfan/entry/how_to_turn_a_mirror](https://blogs.oracle.com/zhangfan/entry/how_to_turn_a_mirror)
[http://askubuntu.com/questions/517354/terminal-method-of-formatting-storage-drive](http://askubuntu.com/questions/517354/terminal-method-of-formatting-storage-drive)
[https://wiki.archlinux.org/index.php/ZFS#Create_a_storage_pool](https://wiki.archlinux.org/index.php/ZFS#Create_a_storage_pool)
[https://github.com/zfsonlinux/zfs/wiki/faq#advanced-format-disks](https://github.com/zfsonlinux/zfs/wiki/faq#advanced-format-disks)
[http://wiki.illumos.org/display/illumos/ZFS+and+Advanced+Format+disks](http://wiki.illumos.org/display/illumos/ZFS+and+Advanced+Format+disks)

---

### Post by TheFu on 2016-09-08
I would do a fresh backup the data, then wipe all the disks to be used and create the RAID2z pools and restore the data as needed.

No RAID replaces the needs for backups, though ZFS does help a bunch.  Anything too complicated is prone to errors and forgotten steps.  Plus, you need a backup before starting anything this complex anyway, so why not use them to make it easier?

---

### Post by Soon_Yew on 2016-09-09
Well my thoughts was to have another drive sitting in the same server running rsync on a monthly basis as the backup - if i had the space and ports available after the migration. Alternatively rather than moving from a Mirrored to a four drive Raidz2 setup, I could also run a 3 drive Raidz + 1 drive backup. But even that would seem to be no less secure if anything was to happen to the server (fire, theft, etc). As of now I do not have any options in getting an offsite backup solution, so until I do I figured it would make sense to not spend on a drive which would become obsolete (for my use case) later on.

---

### Post by TheFu on 2016-09-09
No offsite backups?

$99 gets a cheap 4-disk eSATA/USB3 external array. Good enough for home use, but not in a business (reasons). Put in it whatever SATA disks you like; unlike those $700 NAS devices, it isn't picky about "supported" disks. Use encryption, since that array would be "portable" relative to the server and all portable devices need to be encrypted, period.  

Internal disks are a liability if inside the same case they are trying to back up. Ever seen a server melt?

Lacking off-site backups, if you have to evacuate this building with 15 min of warning, what would you take?  I'd leave all the servers, but grab 2 backup arrays and a chromebook. For computing, that would be it and sufficient to save the company. Companies can be ruined by the lack of off-site backups.

---

### Post by bob_jones2 on 2016-09-09
[I]As of now I do not have any options in getting an offsite backup solution

[/I]I'm sorry, but I don't buy that excuse.You *"don't have any options"* ?  Really ?  Ever heard of AWS, Azure or other cloud services ?

As TheFu says.  RAID is not a backup mechanism.  ZFS is not a backup system.  Whatever fancy name you give it, a logical array of drives is still _***ONE***_ drive.  

The rule of thumb is for critical data you should have a **_minimum_** three _***INDEPENDENT***_ backup copies.Preferably one (or more) of those copies should be located off-site.

I apologise for the strong words, but it is critical that you get a professional grip on data integrity before it gets a grip on you !  You're a sysadmin, your boss is paying you to be professional.  You will be the first one to be fired if you can't recover your company's data in the event of a disaster !

P.S. Please please please.... don't forget test restores !!!! An untested backup is as good as no backup !

---

### Post by TheFu on 2016-09-09
> **bob_jones2 said:**
>  You will be the first one to be fired if you can't recover your company's data in the event of a disaster !

The way around this lack is to write up a **Risk Acceptance** document and have a company officer sign it concerning the lack of offsite backups. This lets someone high up know, perhaps gets budget approved, and keeps them from blaming you.  win-win-win.  Wonder if Ms. Clinton signed one of those for her email server(s)?

 "*Cloud computing is careless computing*." -rms  
"*Cloud computing becomes fog when it goes down.*" - Todd Spragins

---

### Post by Soon_Yew on 2016-09-12
Woooaahhh there people. Before we start going into a spiral discussing what the whole Business Continuity and Disaster Recovery process/philosophy should be, lets just get back into the original question on hand please? All I wanted to ask, given the circumstances I have and what I plan to achieve, is the code and process I highlighted above correct. Even if taking what all of you have said that this is not a good idea, treat this as an academic "proof of concept". You all are one enthusiastic bunch (in a good way)! :D Thanks

---

### Post by Soon_Yew on 2016-09-28
Hi sorry but can someone help me please? Still hoping someone can confirm if the above works. Thanks

---

