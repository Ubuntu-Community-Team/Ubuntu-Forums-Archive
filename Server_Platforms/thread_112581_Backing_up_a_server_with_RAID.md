---
title: "Backing up a server with RAID"
date: 2006-01-04
forum: Server Platforms
---

### Post by vtec on 2006-01-04
I have a server with 3 identical drives. 2 are in a RAID 1 setup and the 3rd is in a tray that can be removed. I would like to be able to use the 3rd drive to back up the system so i'm covered in the event of a major hardware crash. I have tried to use dd to copy one of the raid drives to the 3rd drive. This worked and the 3rd drive was then bootable, however when i went to restore the drive, using dd again the RAID got all messed up and it would not boot. Is there an easy way to back up this RAID to the 3rd drive so that i could restore all of may data to 2 new drives if needed. I would prefer, since the 3rd drive is the same size, to back up to it uncompressed and bootable if possible. It would be even better if i could do this with out booting from a cd like i did last time. I'm also open to different ideas and suggestions. I have never had a good back up system in place and would like one for my new server.

PS. I just reread what I wrote. If you find it confusing, I think its based on my confusion of this topic. 

Thanks

---

### Post by psusi on 2006-01-04
What kind of raid are you using?  I am assuming you have md ( software ) raid.  You need to dd to/from the raid device, not the individual disks that make up the raid.  Also **DO NOT** dd to/from a drive while it is mounted.  If you want to use this method, you will need to boot from a livecd not the hard disks.  

Instead of dd, I sugest that you use rsync to copy from the main drive to the backup.  That way you can get away with backing up while the system is running, provided nothing important is going to be writing to the disk while you back up ( i.e. shutdown mysqld, apache, things like that ).  This will be orders of magnitude faster than dd.

You can also set up rsync snapshot backups ( google for rsync snapshot ) so the backup disk can contain all daily backups for a number of days in the past, and it will only take up as much space as the full backup plus the size of the files that changed each day.

---

### Post by vtec on 2006-01-04
It is a software RAID. I have md0 and md1. md0 is my swap (I know that its not the best idea to have swap mirrored, but at least this way if a drive goes the system will still run. Correct??) and md1 is /. Lets say for example the system takes a power hit and i lose both drives. By using the dd method the drive data is copied and the partition data. So in theory when i restore the drive i restore all the data and the partition layout. If i used the rsync method how would you go about a restore? Whould you have to create and the partition and then restore the data to them?

---

### Post by vtec on 2006-01-04
I have been reading up on rsync snapshots, and it seems very promising. However it seems more suited for backing up a home directory or user data, not an entire file system. Is this correct. My interest in dd was because it could mirror a drive to another, that then could be mirrored back in the event of drive failure. But I found that it becomes much more complex when you introduce a RAID.

---

