---
title: "Disk, partition and backup layout"
date: 2012-08-30
forum: Server Platforms
---

### Post by chrisbay90 on 2012-08-30
Hello everyone

Thought I would drop in and see if I can get the opinion of you smart folks. I am adding another disk to my home server and would like to know your opinion on how I should lay out my filesystem.

I have 3 SATA HDD's.
1 x 320GB <- new (to the server)
1 x 1000GB <- pre-existing (currently has 1 partiton with the OS and about 400GB worth of movies)
1 x 1500GB <- pre-existing (has bits and peices of system backups, and a share for the whole LAN)

Was thinking of migrating the system over to the 320GB. Using the 1Tb as a media drive and the 1.5TB as a backup drive. (the backup HD would have system backups + backups of LAN user data)

I would like to have backups of the system that I can roll back changes from or just grab an old conf file when needed. I would also like a whole image style backup to restore from in the event of disk failure or total system meltdown. I would like to use the system disk itself for the former backups and the 1.5TB drive for the latter. Can you recommend the best way to achieve both these methods of backup? For the latter, a system that involves a sort of, please restore this now thing that reloads the whole system (OS, boot loader etc).

Given that I'm migrating to anew system disk I want to partition it up properly according to best practices. Also noting I want to keep a separate copy of system backups on the system disk as well. Could you recommend me a partition layout? Presently the system is only occupying <100GB, all told except for movies and backups etc shared off the other disks.

---

