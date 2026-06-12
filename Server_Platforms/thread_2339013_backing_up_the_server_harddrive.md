---
title: "backing up the server harddrive"
date: 2016-10-03
forum: Server Platforms
---

### Post by pradtf2 on 2016-10-03
our server is set up with 2 drives one which is a pop-in backup for the other (we can simply replace one drive with the other at anytime).

we have in the past 
1. installed the os on both drives.
2. rsynced from sda to sdb excluding grub and fstab so sdb can boot on its own if required.

is there a more efficient way of achieving the same goal? we are doing a new installation with ubuntu (instead of debian as it was in the past).

for instance, can we just 
1. note down the uuids for sdb
2. rsync sda to sdb
3. manually replace all sda uuids with sdb uuids in fstab and grub.cfg

will that be sufficient?

in friendship,
prad

---

### Post by CharlesA on 2016-10-04
rsync could work, yes, but are you only backing up the drive so you do not have any downtime in the event the primary drive fails?

I'd look into RAID 1 if you need to have guaranteed uptime in the event of disk failure.

---

### Post by pradtf2 on 2016-10-04
hi charles! thx for the input. our server has never been 'mission-critical'. we had a raid card in one of them about 10yrs ago when we were using freebsd.

we didn't set it up on the ones after that because we had the wd green drives and figured that there was no point it running a drive continuously when it wasn't really going to be used - did the rsync at 4am each morning.

however, we aren't on green drives anymore, so i'm really starting to like the raid idea. it not only does the backup, we don't have to deal with the uuid matter afaik.

never tried software raid. any suggestions on what ubuntu has for this and where to look?
i'll start investigating it tomorrow morning.

thx!

UPDATE: just googled it and see that there are plenty of resources!
[https://help](https://help).**ubuntu**.com/lts/**server**guide/advanced-installation.html
[https://help](https://help).**ubuntu**.com/community/Installation/Software[B]RAID
[/B][https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)
as well as some youtube videos!

so i'll look at these tomorrow, but if you have any suggestions, they'd be most welcome.
the configuration is for 2 drives one being a duplicate of the other. each drive will have 3 partitions.


in friendship,
prad

---

### Post by darkod on 2016-10-04
Don't forget not to consider raid as backup. Again, it depends on how much protection you need for your data. Raid helps with downtime but it is not a replacement for backup.

For example, if a file gets deleted/modified accidentally or intentionally, raid can't help you there.

You can convert current install to raid1 mdadm software raid. The steps in general go like:
1. On the second disk create the partitions with the size that you need.
2. Create three mdadm arrays with each of the three partitions and a missing member (mdadm --create allows you to do this).
3. Copy the data from the primary disk to the corresponding mdadm arrays.
4. Boot from the raid1 arrays and make sure it boots and works correctly.
5. Add each partition from the primary disk to the corresponding mdadm array (with or without deleting and then recreating the partitions).

---

### Post by CharlesA on 2016-10-04
Yes, RAID is not backup as darkod pointed out, but it does ensure the system stays running in the event of a failure.

It will not prevent corruption or deletion/modification of files either, so you should be backing up any data you cannot allow to be lost.Versioned back ups are best - I use a combination of rsync and rdiff-backup, but I am slowly migrating to BorgBackup because it supports encryption and deduplication. It might not be the best thing for an enterprise, though.

---

### Post by pradtf2 on 2016-10-04
thx darkod and charlesA!
i went ahead and did a regular bkp this morning.
i'll look into raid - saw that i can actually set it up from the install!

and i'll keep your wise words about raid and bkp in mind.

in friendship,
prad

---

### Post by TheFu on 2016-10-04
> **CharlesA said:**
> Yes, RAID is not backup as darkod pointed out, but it does ensure the system stays running in the event of a failure.

It will not prevent corruption or deletion/modification of files either, so you should be backing up any data you cannot allow to be lost.Versioned back ups are best - I use a combination of rsync and rdiff-backup, but I am slowly migrating to BorgBackup because it supports encryption and deduplication. It might not be the best thing for an enterprise, though.

I'll be checking out **BorgBackup**.  I like **rdiff-backup**, but really wish it did encryption.   I have no use for on-system backups, however. Remote or nothing.  Looked through their docs and watched the video - seems much like git.  Not sure I buy the "dedup" claims at this point. Thanks for the lead.  My backups for 20-30 systems uses just under 1TB.  Would be good to make that smaller - can't imagine it being any faster than it is today.  

The dedup aspect does concern me - all those references could be screwed if a byte gets messed up. Seems ZFS would be required ... which means my current backup server can't be used.  Would need to move to 16.04 first.  Typical. 1 requirement leads to another and another and another.

---

### Post by CharlesA on 2016-10-04
> **TheFu said:**
> I'll be checking out **BorgBackup**.  I like **rdiff-backup**, but really wish it did encryption.   I have no use for on-system backups, however. Remote or nothing.  Looked through their docs and watched the video - seems much like git.  Not sure I buy the "dedup" claims at this point. Thanks for the lead.  My backups for 20-30 systems uses just under 1TB.  Would be good to make that smaller - can't imagine it being any faster than it is today.  

The dedup aspect does concern me - all those references could be screwed if a byte gets messed up. Seems ZFS would be required ... which means my current backup server can't be used.  Would need to move to 16.04 first.  Typical. 1 requirement leads to another and another and another.

Probably not much faster, but you can set Borg to do compression as well as encryption (using keyfiles, which is what I do).

It doesn't seem to be that bad as far as the dedupe goes. I do wonder how they handle corruption - there is a [check command]("https://borgbackup.readthedocs.io/en/stable/usage.html#borg-check") that is supposed to compare a hash and determine if a file is OK or not. Have you already looked at the internals doc for them? [http://borgbackup.readthedocs.io/en/stable/internals.html](http://borgbackup.readthedocs.io/en/stable/internals.html)

I've been running it on Debian Jessie. I've been using it to backup to my second server via SSH. It took my giant Steam folder and got it down to 1.96TB after dedupe. Granted, the way the all archives stats are calculated are kinda odd, but it seems to work well for me.
```
                       Original size      Compressed size    Deduplicated size
This archive:                2.71 TB              2.16 TB             59.20 GB
All archives:               10.58 TB              8.46 TB              1.96 TB
```

---

### Post by TheFu on 2016-10-05
When you type **df -h** what does it show for the backup areas?
Need to look at this closer, no time.  At this point, my questions really will be answered quickest by trying it and looking around.

Wish they'd say approximate sizes and times.  For example, I know that rdiff-backup needs 1.2x the original storage to support 30-60 days of versioned backups on most of my systems and have daily durations so I know how long a backup will take.  A few examples from today ... 
```
ElapsedTime 6.05 (6.05 seconds)
ElapsedTime 281.66 (4 minutes 41.66 seconds)
ElapsedTime 9.81 (9.81 seconds)
ElapsedTime 156.35 (2 minutes 36.35 seconds)
ElapsedTime 89.63 (1 minute 29.63 seconds)
ElapsedTime 261.89 (4 minutes 21.89 seconds)
```

On those systems, the changed data is almost always less than 15MB (+/-).  Of course, some systems take longer and have lots of change data daily.

---

### Post by CharlesA on 2016-10-05
> **TheFu said:**
> When you type **df -h** what does it show for the backup areas?
Need to look at this closer, no time.  At this point, my questions really will be answered quickest by trying it and looking around.

Wish they'd say approximate sizes and times.  For example, I know that rdiff-backup needs 1.2x the original storage to support 30-60 days of versioned backups on most of my systems and have daily durations so I know how long a backup will take.  A few examples from today ... 
```
ElapsedTime 6.05 (6.05 seconds)
ElapsedTime 281.66 (4 minutes 41.66 seconds)
ElapsedTime 9.81 (9.81 seconds)
ElapsedTime 156.35 (2 minutes 36.35 seconds)
ElapsedTime 89.63 (1 minute 29.63 seconds)
ElapsedTime 261.89 (4 minutes 21.89 seconds)
```

On those systems, the changed data is almost always less than 15MB (+/-).  Of course, some systems take longer and have lots of change data daily.

I have two repositories for borg on that drive - one is my regular data, the other is steam.

Last time I backed up to that drive was in May (I think?). It's not my normal daily backup drive.

Total run time for that was:
Backup started at:  10/02/16  11:36:53
Backup finished at: 10/02/16  17:24:48

Looks like the regular backup took about two an a half hours, but I'm also using moderate compression and Borg is single threaded, so it'll be pretty slow. This is backing up to a USB 3.0 external drive.

Regular:
```

Time (start): Sun, 2016-10-02 11:36:54
Time (end):   Sun, 2016-10-02 13:54:47
Command line: /usr/bin/borgbackup create --stats --progress --compression zlib,6 /mnt/daily::10-02-2016 /array/ --exclude /array/charles/Steam --exclude /array/dvds --exclude /array/mediatomb
Number of files: 378138

                       Original size      Compressed size    Deduplicated size
This archive:                1.05 TB            944.41 GB             43.95 GB
All archives:                1.99 TB              1.84 TB            878.41 GB

                       Unique chunks         Total chunks
Chunk index:                  527098              1499185

```
Steam:
```

Time (start): Sun, 2016-10-02 13:54:56
Time (end):   Sun, 2016-10-02 17:24:25
Command line: /usr/bin/borgbackup create --stats --progress --compression zlib,6 /mnt/steam::10-02-2016 /array/charles/Steam
Number of files: 1320884

                       Original size      Compressed size    Deduplicated size
This archive:                2.71 TB              2.16 TB             59.20 GB
All archives:               10.58 TB              8.46 TB              1.96 TB

                       Unique chunks         Total chunks
Chunk index:                 1937054              9049824

```

df -h before:
```
/dev/sde1               4.6T  2.5T  2.1T  56% /mnt
```
df -h after:
```
/dev/sde1               4.6T  2.6T  2.0T  58% /mnt
```

I know that doesn't help much at all - I have a chunk of code in my backup script that emails me a summary after the backup completes, but it isn't super detailed.

---

### Post by TheFu on 2016-10-06
2.5 hours. Wow. That is slow. Couldn't use duplicity because it wouldn't complete within the allowed backup window.
Daily backups send a summary email like this for each system (only 1 email total):

```
=== Time for Backups to spam2 === 
StartTime 1475736606.00 (Thu Oct  6 02:50:06 2016)
EndTime 1475736613.38 (Thu Oct  6 02:50:13 2016)
ElapsedTime 7.38 (7.38 seconds)
TotalDestinationSizeChange 852 (852 bytes)

``` It is just a grep from the rdiff-backup status files. Enough that I know when there are issues or not.

---

### Post by TheFu on 2016-10-06
2.5 hours. Wow. That is slow. Couldn't use duplicity because it wouldn't complete backups within the allowed backup window.  For media files - 8+TB, I'm seeing backup times of less than 10min using rsync. Clearly it completely depends on the amount of change data, but I'm not completely happy with the actual data protection provided.  Either I need ZFS or need to manually add par2 files.  10% par2 has saved data corruption back when using optical media. Wouldn't use it for OS files, just media.

Here, daily backups send a summary email like this for each system (only 1 email total):

```
=== Time for Backups to spam2 === 
StartTime 1475736606.00 (Thu Oct  6 02:50:06 2016)
EndTime 1475736613.38 (Thu Oct  6 02:50:13 2016)
ElapsedTime 7.38 (7.38 seconds)
TotalDestinationSizeChange 852 (852 bytes)

``` It is just a grep from the rdiff-backup status files. Enough that I know when there are issues or not.  There is some pre-backup and post-backup stuff happening too, add 1 more min, tops, to the total time.  That extra stuff is cleaning up temp files/caches, dumping DBs and stopping starting services. Just depends on the system.

---

### Post by CharlesA on 2017-04-01
> **TheFu said:**
> 
The dedup aspect does concern me - all those references could be screwed if a byte gets messed up. Seems ZFS would be required ... which means my current backup server can't be used.  Would need to move to 16.04 first.  Typical. 1 requirement leads to another and another and another.

Old thread, but I wanted to mention this because it bit me when I was doing a check of my backups...

I ran: ```
borgbackup check --info /path/to/repo
```

Which returned:
```
Starting repository check
Segment entry checksum mismatch [segment 122543, offset 8]
Segment entry checksum mismatch [segment 123063, offset 4929700]
Segment entry checksum mismatch [segment 130204, offset 3987119]
Segment entry checksum mismatch [segment 130227, offset 3856066]
Segment entry checksum mismatch [segment 130229, offset 3185505]
Segment entry checksum mismatch [segment 158064, offset 8]
Segment entry checksum mismatch [segment 167645, offset 2381813]
Segment entry checksum mismatch [segment 184532, offset 4297028]
Segment entry checksum mismatch [segment 184543, offset 5006513]
Segment entry checksum mismatch [segment 198020, offset 4974927]
Segment entry checksum mismatch [segment 235903, offset 3026529]
Segment entry checksum mismatch [segment 252582, offset 5010272]
Segment entry checksum mismatch [segment 252593, offset 2367407]
Segment entry checksum mismatch [segment 252596, offset 8]
Segment entry checksum mismatch [segment 266363, offset 5083924]
Index object count mismatch. 2095233 != 2095181
Completed repository check, errors found.
```

After some [research]("https://borgbackup.readthedocs.io/en/stable/usage.html#borg-check") and help from the borg guys on freenode, I was able to run a repair against the data:

```
borgbackup check --info --repair /path/to/repo
```

Which returned:
```

Starting repository check
Segment entry checksum mismatch [segment 122543, offset 8]
attempting to recover /array/working/steam/data/12/122543
Segment entry checksum mismatch [segment 123063, offset 4929700]
attempting to recover /array/working/steam/data/12/123063
Segment entry checksum mismatch [segment 130204, offset 3987119]
attempting to recover /array/working/steam/data/13/130204
Segment entry checksum mismatch [segment 130227, offset 3856066]
attempting to recover /array/working/steam/data/13/130227
Segment entry checksum mismatch [segment 130229, offset 3185505]
attempting to recover /array/working/steam/data/13/130229
Segment entry checksum mismatch [segment 158064, offset 8]
attempting to recover /array/working/steam/data/15/158064
Segment entry checksum mismatch [segment 167645, offset 2381813]
attempting to recover /array/working/steam/data/16/167645
Segment entry checksum mismatch [segment 184532, offset 4297028]
attempting to recover /array/working/steam/data/18/184532
Segment entry checksum mismatch [segment 184543, offset 5006513]
attempting to recover /array/working/steam/data/18/184543
Segment entry checksum mismatch [segment 198020, offset 4974927]
attempting to recover /array/working/steam/data/19/198020
Segment entry checksum mismatch [segment 235903, offset 3026529]
attempting to recover /array/working/steam/data/23/235903
Segment entry checksum mismatch [segment 252582, offset 5010272]
attempting to recover /array/working/steam/data/25/252582
Segment entry checksum mismatch [segment 252593, offset 2367407]
attempting to recover /array/working/steam/data/25/252593
Segment entry checksum mismatch [segment 252596, offset 8]
attempting to recover /array/working/steam/data/25/252596
Segment entry checksum mismatch [segment 266363, offset 5083924]
attempting to recover /array/working/steam/data/26/266363
Completed repository check, errors found and repaired.
Starting archive consistency check...
Analyzing archive 03-22-2017 (31/34)
array/charles/Steam/steamapps/common/Saints Row IV/packfiles/pc/cache/sr3_city_0.vpp_pc: New missing file chunk detected (Byte 2024739556-2029037726). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/Sam and Max 301/Pack/4_SamMax301_pc_tx.ttarch: New missing file chunk detected (Byte 4025147-7185284). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: New missing file chunk detected (Byte 174132878-178961563). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: New missing file chunk detected (Byte 349916350-356376504). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: New missing file chunk detected (Byte 367444001-371048547). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/Thief/ThiefGame/CookedPCNG/Maps/CM/C/000_CM_C_Interior02-Art.umap: New missing file chunk detected (Byte 29060510-30391289). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/X-Blades/music/amb03.ogg: New missing file chunk detected (Byte 0-2531453). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/X-Blades/music/track_06.ogg: New missing file chunk detected (Byte 2587453-3525402). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/bioshock 2/SP/Content/BulkContent/DynamicBulkFileAnimGroups.blk: New missing file chunk detected (Byte 22713652-31102260). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/metro 2033/textures.vfs0: New missing file chunk detected (Byte 710186498-717607948). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/05_Mosque_Fight__Damjan_Mravunac__Serious_Sam_III_OST.aac: New missing file chunk detected (Byte 0-2114396). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/35_MP_War01_Gone_4ever__Filip_Brtan__Serious_Sam_III_OST.aac: New missing file chunk detected (Byte 0-2483894). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Flac/01_City_Relax__Damjan_Mravunac__Serious_Sam_III_OST.flac: New missing file chunk detected (Byte 3745162-12133770). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/the witcher enhanced edition/Data/textures00.bif: New missing file chunk detected (Byte 567584461-575973069). Replacing with all-zero chunk.Analyzing archive 06-19-2016 (1/34)
array/charles/Steam/steamapps/common/Saints Row IV/packfiles/pc/cache/sr3_city_0.vpp_pc: New missing file chunk detected (Byte 2024739556-2029037726). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/Sam and Max 301/Pack/4_SamMax301_pc_tx.ttarch: New missing file chunk detected (Byte 4025147-7185284). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: New missing file chunk detected (Byte 174132878-178961563). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: New missing file chunk detected (Byte 349916350-356376504). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: New missing file chunk detected (Byte 367444001-371048547). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/The Witcher 3/DLC/bob/content/streaming.cache: New missing file chunk detected (Byte 446183847-449066067). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/Thief/ThiefGame/CookedPCNG/Maps/CM/C/000_CM_C_Interior02-Art.umap: New missing file chunk detected (Byte 29060510-30391289). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/X-Blades/music/amb03.ogg: New missing file chunk detected (Byte 0-2531453). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/X-Blades/music/track_06.ogg: New missing file chunk detected (Byte 2587453-3525402). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/bioshock 2/SP/Content/BulkContent/DynamicBulkFileAnimGroups.blk: New missing file chunk detected (Byte 22713652-31102260). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/metro 2033/textures.vfs0: New missing file chunk detected (Byte 710186498-717607948). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/05_Mosque_Fight__Damjan_Mravunac__Serious_Sam_III_OST.aac: New missing file chunk detected (Byte 0-2114396). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/35_MP_War01_Gone_4ever__Filip_Brtan__Serious_Sam_III_OST.aac: New missing file chunk detected (Byte 0-2483894). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Flac/01_City_Relax__Damjan_Mravunac__Serious_Sam_III_OST.flac: New missing file chunk detected (Byte 3745162-12133770). Replacing with all-zero chunk.
array/charles/Steam/steamapps/common/the witcher enhanced edition/Data/textures00.bif: New missing file chunk detected (Byte 567584461-575973069). Replacing with all-zero chunk.
Archive consistency check complete, problems found.

```

After the repair was done, I ran a backup as normal and then another repair and this was the result:
```

Analyzing archive 06-19-2016 (1/36)
array/charles/Steam/steamapps/common/Saints Row IV/packfiles/pc/cache/sr3_city_0.vpp_pc: Healed previously missing file chunk! (Byte 2024739556-2029037726).
array/charles/Steam/steamapps/common/Saints Row IV/packfiles/pc/cache/sr3_city_0.vpp_pc: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/Sam and Max 301/Pack/4_SamMax301_pc_tx.ttarch: Healed previously missing file chunk! (Byte 4025147-7185284).
array/charles/Steam/steamapps/common/Sam and Max 301/Pack/4_SamMax301_pc_tx.ttarch: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: Healed previously missing file chunk! (Byte 174132878-178961563).
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: Healed previously missing file chunk! (Byte 349916350-356376504).
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: Healed previously missing file chunk! (Byte 367444001-371048547).
array/charles/Steam/steamapps/common/SleepingDogsDefinitiveEdition/AnimationNIS.big: Completely healed previously damaged file!
[COLOR="#FF0000"]array/charles/Steam/steamapps/common/The Witcher 3/DLC/bob/content/streaming.cache: Previously missing file chunk is still missing (Byte 446183847-449066067). It has a all-zero replacement chunk already.[/COLOR]
array/charles/Steam/steamapps/common/Thief/ThiefGame/CookedPCNG/Maps/CM/C/000_CM_C_Interior02-Art.umap: Healed previously missing file chunk! (Byte 29060510-30391289).
array/charles/Steam/steamapps/common/Thief/ThiefGame/CookedPCNG/Maps/CM/C/000_CM_C_Interior02-Art.umap: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/X-Blades/music/amb03.ogg: Healed previously missing file chunk! (Byte 0-2531453).
array/charles/Steam/steamapps/common/X-Blades/music/amb03.ogg: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/X-Blades/music/track_06.ogg: Healed previously missing file chunk! (Byte 2587453-3525402).
array/charles/Steam/steamapps/common/X-Blades/music/track_06.ogg: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/bioshock 2/SP/Content/BulkContent/DynamicBulkFileAnimGroups.blk: Healed previously missing file chunk! (Byte 22713652-31102260).
array/charles/Steam/steamapps/common/bioshock 2/SP/Content/BulkContent/DynamicBulkFileAnimGroups.blk: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/metro 2033/textures.vfs0: Healed previously missing file chunk! (Byte 710186498-717607948).
array/charles/Steam/steamapps/common/metro 2033/textures.vfs0: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/05_Mosque_Fight__Damjan_Mravunac__Serious_Sam_III_OST.aac: Healed previously missing file chunk! (Byte 0-2114396).
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/05_Mosque_Fight__Damjan_Mravunac__Serious_Sam_III_OST.aac: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/35_MP_War01_Gone_4ever__Filip_Brtan__Serious_Sam_III_OST.aac: Healed previously missing file chunk! (Byte 0-2483894).
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Aac/35_MP_War01_Gone_4ever__Filip_Brtan__Serious_Sam_III_OST.aac: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Flac/01_City_Relax__Damjan_Mravunac__Serious_Sam_III_OST.flac: Healed previously missing file chunk! (Byte 3745162-12133770).
array/charles/Steam/steamapps/common/serious sam 3 serious digital edition bonus/Soundtrack_Flac/01_City_Relax__Damjan_Mravunac__Serious_Sam_III_OST.flac: Completely healed previously damaged file!
array/charles/Steam/steamapps/common/the witcher enhanced edition/Data/textures00.bif: Healed previously missing file chunk! (Byte 567584461-575973069).
array/charles/Steam/steamapps/common/the witcher enhanced edition/Data/textures00.bif: Completely healed previously damaged file!
Archive consistency check complete, no problems found.

```

So in summary, borgbackup does have some healing ability built in, but it looks like it requires a good backup before it will actually be able to fix the errors. Thankfully this means it can repair the backup archives, so no data is actually lost, but it still has it's limitations which you can see highlighted in red - that file was from late 2016 and apparently changed since then, so borg was unable to repair it. The archive is still accessible but that file should be considered lost.

---

