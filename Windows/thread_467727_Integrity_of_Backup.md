---
title: "Integrity of Backup"
date: 2007-06-08
forum: Windows
---

### Post by Sweet Mercury on 2007-06-08
I recently bought a 400GB USB2,0 external hard drive, and I plan on using it as both a backup for my music files and as extra storage for my movie files (to clear up some room on my desktop disk).

So, only part of the data I send to it will be redundantly stored. Is there any way to check the integrity of the transfered data without watching/listening to all of the files?

Secondary question, should I just transfer it all in one big, long, swoop or do it a bit at a time?

All this is going to be on my Windows machine, onto a FAT32 HD (so I can access the files with my Linux laptop).

---

### Post by gnirts on 2007-06-18
Try FileCheckMD5 ( [http://www.brandonstaggs.com/filecheckmd5.html](http://www.brandonstaggs.com/filecheckmd5.html) ) or any hash summer (eg. SHA, RIPE, etc.) to ensure that the files were copied correctly.

If you transferring it all at once you should be fine, just watch out for drive temps. If its uncomfortably hot to the touch, take a break. If you are terribly concerned get a SMART monitoring program like SpeedFan.
[http://www.almico.com/sfarticle.php?id=2](http://www.almico.com/sfarticle.php?id=2)
Although I don't know if it works with external hard drives, but its worth a try.

To make the copying easier try the MS SyncToy Power Toy, as Explorer's built in file transfer can choke on large requests and will quit if it encounters any errors.
[http://www.microsoft.com/downloads/details.aspx?FamilyId=E0FC1154-C975-4814-9649-CCE41AF06EB7&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=E0FC1154-C975-4814-9649-CCE41AF06EB7&displaylang=en)

---

### Post by Sweet Mercury on 2007-06-18
> **gnirts said:**
> Try FileCheckMD5 ( [http://www.brandonstaggs.com/filecheckmd5.html](http://www.brandonstaggs.com/filecheckmd5.html) ) or any hash summer (eg. SHA, RIPE, etc.) to ensure that the files were copied correctly.

If you transferring it all at once you should be fine, just watch out for drive temps. If its uncomfortably hot to the touch, take a break. If you are terribly concerned get a SMART monitoring program like SpeedFan.
[http://www.almico.com/sfarticle.php?id=2](http://www.almico.com/sfarticle.php?id=2)
Although I don't know if it works with external hard drives, but its worth a try.

To make the copying easier try the MS SyncToy Power Toy, as Explorer's built in file transfer can choke on large requests and will quit if it encounters any errors.
[http://www.microsoft.com/downloads/details.aspx?FamilyId=E0FC1154-C975-4814-9649-CCE41AF06EB7&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=E0FC1154-C975-4814-9649-CCE41AF06EB7&displaylang=en)


Cool, thank you.

---

