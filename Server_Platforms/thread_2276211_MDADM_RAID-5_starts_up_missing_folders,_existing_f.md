---
title: "MDADM RAID-5 starts up missing folders, existing folders error on opening"
date: 2015-04-30
forum: Server Platforms
---

### Post by tylersontag on 2015-04-30
After a routine reboot the other day my RAID wouldn't assemble.  Looking closer it said only 2/3 drives were included.   Assembling with --force didn't fix this.

So i took one of the working drives and the one that wouldn't assemble and assembled them without the 3rd and it adjusted the count on the 3rd and assembled.  I took it back down and assembled all three without issue, or so i thought.

When i went to look out in the drive i noticed a few folders were missing.  Exploring any of the other folders i got an error that there was an I/O error reading some random subfolder and none of the subfolders will display.

I unmounted the drive and am running a data scrub on it now.  My hope is when it finishes along with a reboot everything will be alright.

However, if im still experiencing this issue, is there anything i can do to recover my data?  All three drives seem to be working.

-Tyler

---

### Post by darkod on 2015-05-01
Let us know how it goes... Unfortunately I'm not sure what can be done because you already assembled the disks in a "new" array and they probably synced.

Did you check the events counters before you did the reassemble? If the counters differ much you shouldn't force any type of assemble because adjusting the counters is losing information. The bigger the difference in the counters, the more possibility to lose more data.

It is also strange raid5 didn't want to assemble with 2 out of 3 members. It is possible you had other issues with one member before the failure so with another failed it leaves only 1 good member to work with. But we can't know that since you didn't post any output before doing the reassemble.

If your array doesn't assemble first you need to get some detailed info, for example with:
```
sudo mdadm --detail /dev/mdX
sudo mdadm --examine /dev/sdXY
```

That will show you details on mdX and on each member, including counters etc.

---

### Post by tylersontag on 2015-05-01
So, I didn't rebuild the array... the same array came up having the much of the same data on it... i'm just seeing some folders and files missing as though the LVM is corrupted.   I'm wondering if its possible to rollback to an earlier seed value or anything.

Here's my array info

```

XXX@XXXXXXXXX:~$ sudo mdadm -S /dev/md0
mdadm: stopped /dev/md0
XXX@XXXXXXXXX:~$ sudo mdadm -A /dev/md0
mdadm: /dev/md0 has been started with 3 drives.
XXX@XXXXXXXXX:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953511424 (1863.01 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent
  Intent Bitmap : Internal
    Update Time : Fri May  1 00:07:12 2015
          State : active
Active Devices : 3
Working Devices : 3
Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 512K
           Name : :XXXXXXX
           UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
         Events : 573314
    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       8       97        1      active sync   /dev/sdg1
       3       8       81        2      active sync   /dev/sdf1

```
```

xxx@XXXXXX:~$ sudo mdadm --examine /dev/sd[f,g,h]1
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
           Name : :TagRAID
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
   Raid Devices : 3
Avail Dev Size : 3907022850 (1863.01 GiB 2000.40 GB)
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 1152 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a9c1a20d:9f0005a1:a54b977c:26624121
Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  1 00:03:55 2015
       Checksum : 3c942197 - correct
         Events : 573314
         Layout : left-symmetric
     Chunk Size : 512K
   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
           Name : :TagRAID
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
   Raid Devices : 3
Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f6c6f6c9:4ba185eb:e7bbac15:22dec345
Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  1 00:07:12 2015
       Checksum : fcab63 - correct
         Events : 573314
         Layout : left-symmetric
     Chunk Size : 512K
   Device Role : Active device 1
   Array State : AA. ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : e75e7cfe:1509311f:bd0aec7f:702bf588
           Name : :TagRAID
  Creation Time : Mon Aug 29 22:09:26 2011
     Raid Level : raid5
   Raid Devices : 3
Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 3907022848 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 57d63e25:a17b7770:2fc56a58:23a99531
Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  1 00:07:12 2015
       Checksum : fca7328 - correct
         Events : 573314
         Layout : left-symmetric
     Chunk Size : 512K
   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)

```

---

### Post by tylersontag on 2015-05-01
> **darkod said:**
> Let us know how it goes... Unfortunately I'm not sure what can be done because you already assembled the disks in a "new" array and they probably synced.

Did you check the events counters before you did the reassemble? If the counters differ much you shouldn't force any type of assemble because adjusting the counters is losing information. The bigger the difference in the counters, the more possibility to lose more data.

It is also strange raid5 didn't want to assemble with 2 out of 3 members. It is possible you had other issues with one member before the failure so with another failed it leaves only 1 good member to work with. But we can't know that since you didn't post any output before doing the reassemble.

If your array doesn't assemble first you need to get some detailed info, for example with:
```
sudo mdadm --detail /dev/mdX
sudo mdadm --examine /dev/sdXY
```

That will show you details on mdX and on each member, including counters etc.

Also, the data scrub finished but the folders still have the same issue as before :-/

Would it be possible to run data recovery on the RAID?  I was thinking about replacing the drives anyway (they are getting up there in years).  I have a 5 bay enclosure, I could toss in 2 4TB drives and dump data recover from the current 3 into they.  Would something like this be possible if I can't get the drive to mount properly?

---

### Post by darkod on 2015-05-01
You didn't rebuild the array? I understood your first post differently:
> So i took one of the working drives and the one that wouldn't assemble and assembled them without the 3rd and it adjusted the count on the 3rd and assembled.

You mentioned count adjustment yourself. The above doesn't sound like normal assemble.

Right now, the array info shows all three members working good, and the array as assembled. The data you are missing, can you recover it from backups? Otherwise running a full recovery on array of that size from the existing disks will take a lot of time, and the results will be messy... it's a question whether you will be able to use anything at all. Recovering the missing folders from backups should be the best choice. Assuming you have backups...

---

### Post by tylersontag on 2015-05-02
> **darkod said:**
> You didn't rebuild the array? I understood your first post differently:


You mentioned count adjustment yourself. The above doesn't sound like normal assemble.

Right now, the array info shows all three members working good, and the array as assembled. The data you are missing, can you recover it from backups? Otherwise running a full recovery on array of that size from the existing disks will take a lot of time, and the results will be messy... it's a question whether you will be able to use anything at all. Recovering the missing folders from backups should be the best choice. Assuming you have backups...

I did assemble the RAIDS in a weird order, yes... this was an old work around for when one of my drives would think the other to be faulty, when it appeared it was not (I don't think the drives i bought were intended for RAID utilization, i've had problems like this since i first built it)  But i didn't recreate the array, merely assembled it from a subset of its drives.

Doing some command line interogating, it looks like most of the data is still there... several of the subfolders in one of the drives are reporting the following error when i run ls * from the parrent folder

ls: cannot access XX_A_FOLDER_XX: Input/output error

And several more of the folders are marked as being files (of roughly the same size as the sum of their contents)

So, most of my data is there and i;ll be moving what i can onto a new drive.  I think we've just seem some kind of catastrophic data corruption event, possibly  caused by forcing a lagging event count as you mentioned.

So, on a related note, does any one know how to delete these folders marked giving "Input/Output error" ?  i can't rm -r them  Also, does anyone know of a way to mark these folders that are showing up as files as actually being folders to see if the data therein is still recoverable?

---

### Post by tylersontag on 2015-05-04
I'll probably start a new threat to track this issue, since it seems to be different, but i'll post any updates i have (and link to the new thread)

It looks like the underlying LUKS LVM got corrupted, probably from forcing an event counter change on one of the drives in the RAID 5 setup.

I found a utility that can check EXT3 filesystems for such issues, but i'm having problems getting it to finish

running (i've tried with the primary superblock, and a backup as listed below)
```
xxx@yyyy:~$ sudo e2fsck -C 0 -b 32768 -v -p /dev/mapper/luks-ddbcd457-cbeb-442f-b720-8f0383c86a6a 
```
I get to *Step 1B* which is checking for blocks assigned to multiple inodes and it starts spitting out millions of numbers, mostly in sequence.

While this is going on, the memory usage of e2fsck begins to go up at a steady rate until around 93% memory usage the program crashes, saying "Unable to allocate XX bytes for inode"

I've tried enabling [scratch_files] in e2fsck.conf and it seems to be using the space, which was the suggested fix for the process running out of memory, but it still runs for a while and ends in a failure.

So, thats where i'm at now... i gather i could use fsck, but im not really sure which would be appropriate or if i'd even expect a different behavior.  I'm going to let the process run once more to see if i get the same behavior (i should, its been consistent)  and i'll post my findings in some thread more specific to fsck.

Thanks for the help so far.

---

