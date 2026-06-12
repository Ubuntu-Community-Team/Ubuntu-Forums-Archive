---
title: "MDADM - Recovering RAID 5 Array with 1 spare and 1 lost superblock"
date: 2016-03-02
forum: Server Platforms
---

### Post by lexxonnet2 on 2016-03-02
Hi All,

I have a RAID 5 array with 3 drives. It seems that somehow, it got stuffed up last night and when trying to recover from it, I was faced with a situation with 2 drives with the same event number and one out of sync, as below:

```

mdadm --examine /dev/sdb1 | grep Events
         Events : 11743
mdadm --examine /dev/sdc1 | grep Events
         Events : 11719
mdadm --examine /dev/sdd1 | grep Events 
         Events : 11743

```

Normally, I'd just initialise the array with just two drives and add the other later on after setting the superblock to zero (on sdc1), forcing the array to resync.

When I tried that this time, I ended up with a situation where the array assumes one of the drives is a spare and one active. So, I get this:

```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdb1[3](S) sdd1[5](S)
      3906764972 blocks super 1.2
       
unused devices: <none>

mdadm --examine /dev/sdb1 | grep Role
   Device Role : Active device 2

mdadm --examine /dev/sdd1 | grep Role
   Device Role : spare


```

Does anyone have any idea how I can recover from this? I've been trying to work this out for a while now, and most pages on the internet seem to suggest recreating the array with *mdadm --create, *but also suggest that I need to actually know the device order (which may have changed because they were USB drives).

Here's an output of mdadm --examine for all the above drives. /dev/sdc is empty after the superblock deletion.

```

mdadm --examine /dev/sd[b-d]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5d1b6295:af1931b4:06318bbe:a85c0274
           Name : dyson:1
  Creation Time : Thu Nov 21 22:03:52 2013
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 3906764972 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2bbcf201:772984a6:9ef6c8f1:ad9b9a22


    Update Time : Wed Mar  2 18:50:02 2016
       Checksum : ccb1f01e - correct
         Events : 11743


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : ..A ('A' == active, '.' == missing)
/dev/sdc1:
   MBR Magic : aa55
Partition[0] :   1836016416 sectors at   1936269394 (type 4f)
Partition[1] :    544437093 sectors at   1917848077 (type 73)
Partition[2] :    544175136 sectors at   1818575915 (type 2b)
Partition[3] :        54974 sectors at   2844524554 (type 61)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5d1b6295:af1931b4:06318bbe:a85c0274
           Name : dyson:1
  Creation Time : Thu Nov 21 22:03:52 2013
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 3906764972 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 92b7302a:79499443:07266a53:17d09bfc


    Update Time : Wed Mar  2 18:50:02 2016
       Checksum : cda26f5c - correct
         Events : 11743


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : spare
   Array State : ..A ('A' == active, '.' == missing)

```

Any help is much appreciated :)

Cheers,
Abhinay

---

### Post by darkod on 2016-03-02
Even though it says sdd1 is spare, it is very good that the events match, so i would just try to force assemble it. You shouldn't have zeroed sdc1 superblock that fast, it also had "small" difference in the events and it can be useful if you run into issues with sdb1 and sdd1. Anyway...

It would be something like:
```
sudo mdadm --stop /dev/md1
sudo mdadm --assemble --force --verbose /dev/md1 /dev/sdb1 /dev/sdd1
```

See how that goes and post any error output.

---

### Post by lexxonnet2 on 2016-03-02
Thanks for the reply. Yep, definitely feel like a git for zero-superblocking sdc1. I tried what you suggested and still ended up with the spare drive. Here's the output:

```

sudo mdadm --assemble --force --verbose /dev/md1 /dev/sdb1 /dev/sdd1
mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot -1.
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sdd1 to /dev/md1 as -1
mdadm: added /dev/sdb1 to /dev/md1 as 2
mdadm: /dev/md1 assembled from 1 drive and 1 spare - not enough to start the array.

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdb1[3](S) sdd1[5](S)
      3906764972 blocks super 1.2
       
unused devices: <none>

```

Slot -1 certainly seems like it's an odd slot for the drive... I wonder if it's possible to force that to be slot 0 or slot 1?

---

### Post by darkod on 2016-03-02
Hmmm, so it does not convert the spare into a member. I wasn't sure about that. The next step is to try adding the --run option, but again you have to try and see if that can convert the spare:
```
sudo mdadm --assemble --run --force --verbose /dev/md1 /dev/sdb1 /dev/sdd1
```

If that also doesn't work, as far as I know the only choice left is the --create. Just make sure you use the --assume-clean option otherwise --create will create new blank array. But I'm not 100% if you need to know the disk order for this. On one hand mdadm is rather smart and it should be able to pick up the data on the disks and figure it out when using --assume-clean.

But lets see how the --assemble goes first...

---

### Post by lexxonnet2 on 2016-03-02
```

sudo mdadm --assemble --force --run --verbose /dev/md1 /dev/sdb1 /dev/sdd1
mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot -1.
mdadm: no uptodate device for slot 0 of /dev/md1
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sdd1 to /dev/md1 as -1
mdadm: added /dev/sdb1 to /dev/md1 as 2
mdadm: failed to RUN_ARRAY /dev/md1: Input/output error
mdadm: Not enough devices to start the array.

```

Didn't work unfortunately :(

---

### Post by darkod on 2016-03-03
Unfortunately all I can think of is a new --create with --assume-clean. But like you said, it's better to know the exact disk order for that, and you don't. That is also an important mental note to make, after creating an array always note down your device order/layout, so you have it in the future.

On top of that you zeroed one superblock that could have told you at least the disk slot it belonged to...

I'm not sure if -D can return any useful info, with one zeroed superblock and that...
```
sudo mdadm -D /dev/md1
```

There is also something strange... In the /proc/mdstat in your first post we can see sdb1[3] and sdd1[5] which points towards their order. But the --assemble output clearly states it sees sdb1 as slot 2 (the last one).

Do some more searching on google if it comes up with any recommendations... I will try also when I have more free time...

PS. Actually reading on the internet it seems mdadm is quite good in protecting the data and even if you recreate the array in wrong order that will not destroy the data and it still gives you a chance to get the order right. The most important part is the --assume-clean which tells mdadm NOT to do a rebuild/sync, so the recreate process will not do any changes/writes. In this case before you actually mount it and start writing on it, the data is not touched. And if you get the order wrong it will not allow you to mount it at all because it will notice the filesystem doesn't look right.

Of course, a best case is if you can first clone sdb and sdd but that means having two spare temp disks at hand to do the cloning, and then if the data gets messed up you still have the original data on the cloned disks. But people have done it without this step. It depends on what you decide...

In my bookmarks at home I actually had one article of a guy trying all these different types of recovery of a failed array and can pass it on to you later.

---

### Post by lexxonnet2 on 2016-03-05
Hey, thanks for all your help so far. Been a busy couple of days.

I initially did an mdadm --create --assume-clean and got the order wrong. But, as you mentioned, it didn't screw things up and I just recreated again with the right order and it worked. However, once I added in the zero-superblocked spare drive, it started resyncing and within a few minutes had reverted to the old situation.

Turns out, I found out the reason for the initial array collapse. Two of the drives have basically failed simultaneously! I did a smart test on all three and one's working fine, while the other two have errors. One is quite severe and fails both the short test and the long test, while the other fails the long test only.

At this point, I think I have probably lost all of the data on those drives, which is a bummer. They were 2TB drives, and I had slightly over 2TB of data overall on them, but I do have backups of some of it in different places and will probably spend the next few days seeing what I can recover. I think, however, that for the next time around, I'll just stick with a non-RAID solution (one main drive and one backup drive, which I rsync/unison to every night). 

Doing some more reading up, it seems like RAID 5 becomes increasingly unreliable past 1TB, so that might be a better option. Thanks once again for all your help.

---

### Post by darkod on 2016-03-05
I don't if you have given up completely, but what you might try is creating the array degraded without the disk that has most errors (in case that was the disk that had smaller number of events too).

You say the array failed when you added sdc1 right? Is that the disk with most errors? What if you don't try to add it at all?

The array can run with sdb1 and sdd1 only, and you can also mount it. However with another disk close to failure it can fail as soon as you start reading from it. But it's worth a shot. Because if the array holds long enough with sdb1 and sdd1, you can copy the data to another disk and have all your data.

---

### Post by lexxonnet2 on 2016-03-05
I tried rebuilding it with both of the other disks, but as you suspected, there were enough errors that it degraded as soon as I tried to copy information from it.

---

