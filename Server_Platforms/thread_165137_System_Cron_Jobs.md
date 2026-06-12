---
title: "System Cron Jobs"
date: 2006-04-24
forum: Server Platforms
---

### Post by hussam_nasir on 2006-04-24
Hello Fellow Ubuntu users,

 Well i have a very strange problem that i have now noticed on our ubuntu server machines with SCSI tape drives. We normally do backups on tapes every night starting at 12:00am. Our problems started the day we switched over to Ubuntu. If our backups (we use dump/restore) ran past 12:40am , it would cry on the tapes and the dumps would fail. It would not even eject the tape on the internal drives nor let us access the tape drive saying "device or resource busy".

A sample dump log as below

DUMP: Date of this level 4 dump: Sat Apr 22 00:44:18 2006
  DUMP: Date of last level 0 dump: Thu Apr  6 18:09:31 2006
  DUMP: Dumping /dev/sda5 (/nfs4) to /dev/tape
  DUMP: Label: /nfs4
  DUMP: Writing 64 Kilobyte records
  DUMP: mapping (Pass I) [regular files]
  DUMP: mapping (Pass II) [directories]
  DUMP: estimated 1426986 blocks.
  DUMP: Volume 1 started with block 1 at: Sat Apr 22 00:46:58 2006
  DUMP: dumping (Pass III) [directories]
  DUMP: dumping (Pass IV) [regular files]
  DUMP: write error 496512 blocks into volume 1: Input/output error
  DUMP: fopen on /dev/tty fails: No such device or address
  DUMP: The ENTIRE dump is aborted.


And the funny part is that it does not just fail on this partition. It happened on another partition one but exactly at 12:40 am. Same thing on other machines too. My gut feeling says its some system cronjob that is somehow keeping the machine busy and the denying tape access at that time. Does anyone know or have seen such kind of a  problem. ?? If so please let me know and its possible solution,. I am busy pulling my hair out regarding this...](*,)

---

