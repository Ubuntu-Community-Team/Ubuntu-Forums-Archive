---
title: "backup Ubuntu with large data"
date: 2012-06-28
forum: Server Platforms
---

### Post by curmudge1 on 2012-06-28
Does anyone have any recommendations for backup software/hardware for a server with a lot of data?  We want/need to backup Ubuntu  with (up to) 12TB of files & do file level, point-in-time recovery.   E.g., we need to be able to restore a file or directory as of a certain day, like 2 weeks ago Thursday.  Don't need CDP (continuous data protection).  

Because of the recovery as of a prior date, a simple rsync to another server with enough storage is not sufficient.

To complicate matters, this is a virtual host running on Vmware 5.0.  EMC Networker, for example, does not support Ubuntu for file level recovery with their Vmware API product.  I don't relish pushing 12TB over a 1GbE NIC when I do a full backup.

Appreciate any ideas, thanks.  I'm rather leaning to server running some form of Solaris server with ZFS and lots of disk, doing rsync daily and zfs snapshots.

---

### Post by wirelessmonkey on 2012-06-28
BackupPC [http://backuppc.sourceforge.net]("http://backuppc.sourceforge.net")
will do what you need. Some fast storage and there is a little learning curve as you set up your backups, but it is my favorite backup solution.

It is in the repos, and I highly recommend the repo version for ease of install.

---

### Post by SeijiSensei on 2012-06-28
If you want to try your hand at scripting a solution, I'll suggest a model where you use "find -mtime -1" to identify all the files that have changed in the past twenty-four hours, then an rsync job that copies those files to a date-denominated directory on the backup device.  You'll have a complete audit trail and at worst day-old backup copies.

You can make snapshot backups in Linux if you use [LVM]("http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html").

---

### Post by thnewguy on 2012-06-28
I would suggest setting up your backup server with ZFS. Tht way you could take a snapshot every day in a cronjob, which would allow you to go back and retrieve files at a given date/time. Just do a snapshot immediately prior to your latest rysnc.

---

### Post by Cheesemill on 2012-06-29
Other options would be [rsnapshot]("http://rsnapshot.org/") and [storeBackup]("http://storebackup.org/").

---

### Post by kgatan on 2012-06-29
I use rsnapshot in our office to store hourly, daily, weekly and monthly backups.
Versatile and easy to use.

If you go with zfs you can also send zfs snapshots to a different zfs backup machine using zfs commands.
Im not sure if thats supported in the linux version but i think it is in freebsd.

---

