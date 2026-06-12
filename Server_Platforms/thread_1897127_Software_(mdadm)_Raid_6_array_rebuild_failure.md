---
title: "Software (mdadm) Raid 6 array rebuild failure"
date: 2011-12-18
forum: Server Platforms
---

### Post by jhon614 on 2011-12-18
First, some specs:

Ubuntu 11.04
kernel 2.6.38-13
mdadm 1.2
Raid6 with 7 sata2 drives, plugged into 2 SiI(Silicon Image) 3114 based cards.

Everything was running fine for quite a long time. Then one day a drive failed, so I replaced it and started to rebuild. During the process, 2 other drives hit bad sectors and were removed from the array.  This stopped the rebuild and left the array with 4 discs online, 2 removed and 1 partially synced. This is what I'm left with.

johnny@Ubuntu:~$ sudo mdadm --detail /dev/md0
/dev/md0:
Version : 1.2
Creation Time : Mon Jan 31 23:19:09 2011
Raid Level : raid6
Used Dev Size : 1953466624 (1862.97 GiB 2000.35 GB)
Raid Devices : 7
Total Devices : 5
Persistence : Superblock is persistent

Update Time : Wed Sep 14 12:39:46 2011
State : active, FAILED, Not Started
Active Devices : 4
Working Devices : 5
Failed Devices : 0
Spare Devices : 1

Layout : left-symmetric
Chunk Size : 64K

Name : :Raid6
UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
Events : 288197

Number Major Minor RaidDevice State
   5     8     81      0      spare rebuilding
   1     8     65      1      active sync /dev/sde1
   8     8     33      2      active sync /dev/sdc1
   3     0      0      3      removed
   4     0      0      4      removed
   6     8     49      5      active sync /dev/sdd1
   7     8    129      6      active sync /dev/sdi1

Notice the 2 discs that are marked as "removed" and the 1 marked "spare rebuilding".

I would understand mdadm removing a disc with bad sectors during a Raid5 rebuild because this would render the array broken, since 1 failed disc and some bad sectors on another disc means you have lost data. But in Raid6 this isn't necessarily the case due to the double parity.  Bad sectors on multiple drives should only be a problem if they occur in the same stripe.

1. Can I force the removed discs back into the array?

2. Can I force the removed discs with bad sectors to remain in the array (prevent removal) and successfully resync the spare?

3. Is there any way to get mdadm to scan the array on some schedule to prevent bad sectors only being discovered during a rebuild?

Please be as detailed as possible in your responses since I'm not an mdadm pro.  Include any commands necessary.  Any other advice and/or suggestions are welcome.  Thank you very much ahead of time for your help.

---

### Post by rubylaser on 2011-12-18
> **jhon614 said:**
> 
1. Can I force the removed discs back into the array?

2. Can I force the removed discs with bad sectors to remain in the array (prevent removal) and successfully resync the spare?

3. Is there any way to get mdadm to scan the array on some schedule to prevent bad sectors only being discovered during a rebuild?

Please be as detailed as possible in your responses since I'm not an mdadm pro.  Include any commands necessary.  Any other advice and/or suggestions are welcome.  Thank you very much ahead of time for your help.

1. You try to force the array back together like this.
```
mdadm --assemble --force /dev/md0 /dev/sd[cdefghi]1
```
I'm not sure those are the correct disk letters.  The output of mdadm -E /dev/sd[cdefghi]1 would be useful.

2. Maybe, they'll likely get kicked back out again.  I'd likely use ddrescue on the 

3. mdadm already has a cron job that runs bi-monthly to check your array.  Have you set up and verified mdadm monitoring and emailing?  Also, have you set up smartmontools and approriate periodic testing to catch bad disks early to hopefully prevent this scenario?

---

### Post by jhon614 on 2011-12-31
I was given some advice on another forum to do this.

> johnny@Ubuntu:~$ sudo mdadm --assemble /dev/md0 --scan --force
mdadm: forcing event count in /dev/sdh1(3) from 288194 upto 288197
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdh1
mdadm: /dev/md0 has been started with 5 drives (out of 7) and 1 rebuilding.

While it was rebuilding Ubuntu Disk Utility showed that there were disks that were part of the array that could be added.  Without thinking about it I added one of them as a spare.  I guess I was assuming the rebuild would succeed.  Well it didn't succeed.  Now there is a drive that got added as a spare and probably had very important info on it.

Is there a way to "rollback" the state of a drive from being a spare to the way it was before being added as a spare?

Also, I tried your assemble command.  The drives have different letters due to a restart, but this is all the same hardware.

> johnny@Ubuntu:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
johnny@Ubuntu:~$ sudo mdadm --assemble --force /dev/md0 /dev/sd[bcdefgh]1
mdadm: /dev/md0 assembled from 4 drives and 2 spares - not enough to start the array.

See the 2 spares?  I think that was due to what I did during the first assemble attempt.  Is there anything I can do to fix that?

Here is the info you said would be useful also.

> johnny@Ubuntu:~$ sudo mdadm -E /dev/sd[bcdefgh]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
           Name : :Raid6
  Creation Time : Mon Jan 31 23:19:09 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3906933253 (1862.97 GiB 2000.35 GB)
     Array Size : 19534666240 (9314.85 GiB 10001.75 GB)
  Used Dev Size : 3906933248 (1862.97 GiB 2000.35 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 250cfe86:e5fd1bcd:260b4478:c771bd9b

    Update Time : Tue Dec 20 21:01:39 2011
       Checksum : 93f652ab - correct
         Events : 288204

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 6
   Array State : .AAA..A ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
           Name : :Raid6
  Creation Time : Mon Jan 31 23:19:09 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3906933253 (1862.97 GiB 2000.35 GB)
     Array Size : 19534666240 (9314.85 GiB 10001.75 GB)
  Used Dev Size : 3906933248 (1862.97 GiB 2000.35 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 34258aad:8ac3939f:438b66af:73c98d3f

    Update Time : Tue Dec 20 21:01:39 2011
       Checksum : 67ed08f6 - correct
         Events : 288204

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : spare
   Array State : .AAA..A ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
           Name : :Raid6
  Creation Time : Mon Jan 31 23:19:09 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3906933253 (1862.97 GiB 2000.35 GB)
     Array Size : 19534666240 (9314.85 GiB 10001.75 GB)
  Used Dev Size : 3906933248 (1862.97 GiB 2000.35 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : afea20e8:57998d2a:4ab1bd26:59f4bd08

    Update Time : Tue Dec 20 21:01:39 2011
       Checksum : 6e04f55d - correct
         Events : 288204

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : .AAA..A ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
           Name : :Raid6
  Creation Time : Mon Jan 31 23:19:09 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3906933287 (1862.97 GiB 2000.35 GB)
     Array Size : 19534666240 (9314.85 GiB 10001.75 GB)
  Used Dev Size : 3906933248 (1862.97 GiB 2000.35 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f74ec4e7:e01c916d:3003d7fa:f15761a5

    Update Time : Tue Dec 20 21:01:39 2011
       Checksum : 216892c8 - correct
         Events : 288204

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : .AAA..A ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
           Name : :Raid6
  Creation Time : Mon Jan 31 23:19:09 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3906933287 (1862.97 GiB 2000.35 GB)
     Array Size : 19534666240 (9314.85 GiB 10001.75 GB)
  Used Dev Size : 3906933248 (1862.97 GiB 2000.35 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 66b10d93:354a565e:388d4ab8:09629b1b

    Update Time : Tue Dec 20 21:01:39 2011
       Checksum : f124b683 - correct
         Events : 288204

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : .AAA..A ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f4d0374a:0aaa0563:a6fed9f2:9931a37f
           Name : :Raid6
  Creation Time : Mon Jan 31 23:19:09 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3906933287 (1862.97 GiB 2000.35 GB)
     Array Size : 19534666240 (9314.85 GiB 10001.75 GB)
  Used Dev Size : 3906933248 (1862.97 GiB 2000.35 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 522a13c0:e41315ca:8070933c:4fa37f46

    Update Time : Tue Dec 20 21:01:39 2011
       Checksum : 39164cfe - correct
         Events : 288204

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : spare
   Array State : .AAA..A ('A' == active, '.' == missing)

---

### Post by rubylaser on 2011-12-31
Adding a disk back to the array as a spare is not a good idea when your array is failed.  You caused a resync event and since your Event counter changed on all disks from your original posting, you rewrote the superblock metadata, which is a bad thing.  There since you don't just have out of sync disks anymore, it really doesn't make any sense to try to recreate the array with the assume-clean flag.  So, you'll need to try this.

```
sudo -i
mdadm --stop /dev/md0
mdadm --assemble --run --force /dev/md0 /dev/sd[bcdefgh]1
```

If that doesn't work, which I'm pretty sure it won't, it looks like you might have lost your array :(

---

### Post by jhon614 on 2011-12-31
Ok, I tried it.  Here's what I got.

```
root@Ubuntu:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@Ubuntu:~# mdadm --assemble --run --force /dev/md0 /dev/sd[bcdefgh]1
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array.
```

So there's no way to "unwind" or "rollback" the event counter?  Is there at least a way to tell it to assemble the drives in a manual order?  I think I can still figure out the order they belong in.  Is there a command to assemble that way?

---

### Post by jhon614 on 2011-12-31
Is zeroing the superblocks and rebuilding it manually an option in any way?  I'm assuming if it is still possible, I'll likely want to rebuild it with "assume-clean" so I don't set it off resyncing the wrong thing?  I do have a lot of saved text files with everything I did in the terminal so I'd have a history of the data for all the drives before I messed with this.  Maybe this data would help rebuilding manually after zeroing the superblocks?

Does anyone have any other ideas?  Or is this approach possible?

---

### Post by rubylaser on 2012-01-01
> **jhon614 said:**
> Is zeroing the superblocks and rebuilding it manually an option in any way?  I'm assuming if it is still possible, I'll likely want to rebuild it with "assume-clean" so I don't set it off resyncing the wrong thing?  I do have a lot of saved text files with everything I did in the terminal so I'd have a history of the data for all the drives before I messed with this.  Maybe this data would help rebuilding manually after zeroing the superblocks?

Does anyone have any other ideas?  Or is this approach possible?

It would have been if you hadn't re-added the drive as a spare.  It essence, when you recreate an array with assume clean, you build the array with the out of sync drives left out and put the array back together degraded with the assume clean option.  Then, I would zero the superblock on the out of sync disk, so as far as mdadm is concerned, it's a new disk, and add it back to the array.  At this point, you would cause a resync.

Unfortunately, your disks are already in sync as seen by the event counter, so a recreate probably won't have any benefit because they've already incorrectly re-synced.

But, it won't hurt at this point to try.

```
mdadm --create --verbose /dev/md0 --level=6 --raid-devices=7 /dev/sd[bcdefgh]1
```

It probably won't come up, so you'll need to assemble it.
```
mdadm --assemble /dev/md0 /dev/sd[cdefghi]1
```

Good Luck:)

---

### Post by jhon614 on 2012-01-01
> Unfortunately, your disks are already in sync as seen by the event counter, so a recreate probably won't have any benefit because they've already incorrectly re-synced.

Here's what I don't understand about this.  You're correct that I assigned a drive as spare (really bad idea), but when the resync failed there weren't enough active drives to continue.  Data was never written to the spare.  Aren't all the bits right where they were before I set it to a spare?  Can that data still be recovered somehow?  What, if anything, is truly lost on the spare?

---

### Post by rubylaser on 2012-01-01
You synced over the metadata tells the array how to assemble itself.  Have you tried the commands I pasted above?  That would recreate the array with metadata version 1.2 and a 512K chunk size just as you had before.  If you haven't written to the array at all, that's a good thing, but that doesn't necessarily mean that your data is intact. There factors other than mdadm state that can cause this to happen and be unrecoverable: disk health, incorrect commands entered, an fsck at the wrong time, etc.

---

### Post by jhon614 on 2012-01-01
I honestly don't know what to think about this one.

```
johnny@Ubuntu:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
johnny@Ubuntu:~$ sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=7 /dev/sd[bcdefgh]1
mdadm: You haven't given enough devices (real or missing) to create this array
```

I count 7 letters in there (b-h) and all the drives still respond individually when I do this (I won't show the entire output unless you want me to.

```
johnny@Ubuntu:~$ sudo mdadm -E /dev/sd[bcdefgh]1
```

---

### Post by rsvancara on 2012-01-01
I like software RAID.  I use it on my home servers.  No matter what RAID you use, I always maintain well tested backups.

---

### Post by rubylaser on 2012-01-01
You shouldn't have to do this, but to get it to work, you might need to zero the superblocks on each disk, then try the recreate again.

---

### Post by jhon614 on 2012-01-04
> You shouldn't have to do this, but to get it to work, you might need to zero the superblocks on each disk, then try the recreate again.

Are there any good tutorials online on how to do this?  Or could you give me a quick explanation of what I want to do?

---

### Post by rubylaser on 2012-01-04
If you have to zero the superblocks to recreate the array, it's very likely your data is not going to be in a functioning state after recreating the array. Here are the directions to zero the superblocks.

```
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdd1
etc...
```

```
mdadm --create --verbose /dev/md0 --level=6 --raid-devices=7 /dev/sd[bcdefgh]1
```

---

