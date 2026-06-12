---
title: "How to convert mdadm N disks RAID5 to mdadm N-1 disks RAID5?"
date: 2009-03-07
forum: Server Platforms
---

### Post by cesarzea on 2009-03-07
Hello all:

I have a server with 8 disks in a mdadm RAID5. I want to change the configuration to 4 disk mdadm RAID5 + 4 disks mdadm RAID0. 

How can I extract the disks from the RAID5 without destroying the data?. 

NOTE: I have enought free space to storage all data on the 4 disks RAID5.

Thanks a lot.

---

### Post by kpatz on 2009-03-07
You'll have to backup all the data on the array and then recreate the array with 4 of the disks, then restore your data.

There's no way to remove disks from a RAID5 array (except for "failing" one and removing it) without losing your data.

---

### Post by fjgaude on 2009-03-08
I see nothing wrong with using **mdadm** to fault, remove one disk at a time, until you get to four. You will have to wait after failing one drive for it to resync which should go automatically... it will take a long time depending on the size of the drives.

```
sudo mdadm /dev/md[n] -f -r /dev/sd[nn]
```

That should do it for the first drive, then use:

```
watch cat /proc/mdstat
```

to watch the array rerync.

I would copy all important data to a spare drive before doing any of this. Backup, backup...

---

### Post by kpatz on 2009-03-09
> **fjgaude said:**
> I see nothing wrong with using **mdadm** to fault, remove one disk at a time, until you get to four. You will have to wait after failing one drive for it to resync which should go automatically... it will take a long time depending on the size of the drives.Assuming that even works, it will take far longer than just backing up, recreating the array, and restoring.

AFAIK, if you create a N-disk array, and fail/remove 1 disk, it becomes a N-1 degraded array.  So, with 8 disks, you pull one, it becomes 8-1 degraded.  It will continue to run, but it won't rebuild itself into a 7-disk redundant array.  It will run degraded until the 8th disk is replaced.  If a second drive fails/is removed, it's bye-bye.

Now, if you don't have an extra drive(s) to backup on to, and all your data could fit on one of the array's drives, you could fail that drive, remove it from the array, then set it up as a standalone disk (put a filesystem on it) and back everything up to that drive.  Then rebuild the array with 4 drives, copy everything back, and then do what you want with the remaining drives.

---

### Post by fjgaude on 2009-03-09
If you are right then I'm wrong... thanks for setting us straight.

---

### Post by cesarzea on 2009-03-17
Thanks for the answers.

---

