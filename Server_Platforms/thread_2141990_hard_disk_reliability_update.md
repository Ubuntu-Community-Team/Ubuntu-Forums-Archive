---
title: "hard disk reliability update"
date: 2013-05-04
forum: Server Platforms
---

### Post by Vegan on 2013-05-04
I bought yet another new hard disk so that reduced the average power on hours slightly.

[http://www.windows-it.tk/wp/disk-reliability.php]("http://www.windows-it.tk/wp/disk-reliability.php")

With more room in the server I figured its time to modernize the storage.

The ST2000DM001 is inexpensive and ideal for a NAS shared resource or even a boot disk.

I will be using on the workstation and then I can use the older 750GB for other work I have with computer chess. Once that is done then the disk will be added to the server storage pool.

Linux takes up a lot less room than Windows Server in virtual hard disk file. This is favorable when a lot of VMs are in use.

SAMBA is helpful in the server world too, it can integrate with a Linux server or Window Server data center easily.

**BACKUP YOUR FILES**, never leave it to chance.

---

### Post by TheFu on 2013-05-04
Be careful with the ST2000DM001 model. There have been issues and Seagate has been less than forthcoming with fixes.  Definitely load the current firmware directly from Seagate to help with any clicking and faster wear issues.

Also be very careful using this model in any RAID configuration.

I agree completely that **backups are critical.**  I have learned backup religion after a local Armageddon in the early 2000s trashed 80% of my data. These days, getting a good, 100% automatic, complete, efficient for storage and networking, incremental backup on a linux system is almost bonehead-trivial. There really isn't any good excuse for NOT having daily backups for everything on every machine except huge video files.  Everything else will fit.

---

### Post by Vegan on 2013-05-04
I have looked carefully and the newer version has 2 plates instead of 3

clicking is usually means a seek error

I have corsair power supplies which mean less risk of logic board problems

---

