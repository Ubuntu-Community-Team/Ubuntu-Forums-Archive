---
title: "Simple backup script for directory with rotation"
date: 2008-04-16
forum: Server Platforms
---

### Post by danielsbrewer on 2008-04-16
Does anyone know of a simple backup script that will do the following:

* It is run each day from cron
* Takes a directory and tar.bzs it
* Puts it in a daily folder
* If it on a particular day of the week copy it to the weekly folder
* If it is on a particular day of the month copy it to a monthly folder
* Keeps 7 daily backups
* Keeps 4 weekly backups
* Keeps all monthly backups

For mysql backups I use "automysqlbackup", but I can't find anything similar for a directory backup.

Any ideas?

---

### Post by twistedtwig on 2008-04-16
There are a lot of threads about backing up your data, one such is:

[http://ubuntuforums.org/showthread.php?t=457611](http://ubuntuforums.org/showthread.php?t=457611)

as I say there are lots there so just google / search for how to tar the files.

As for copying them create a bash file, again a few out there:

[http://ubuntuforums.org/showthread.php?t=506892](http://ubuntuforums.org/showthread.php?t=506892)

not sure how to check the day but I am sure a quick google will answer that.

put the bits together in a bash file and create a cron job to run them

---

### Post by FakeOutdoorsman on 2008-04-16
These might help:
rsync
[Easy Automated Snapshot-Style Backups with Linux and Rsync]("http://www.mikerubel.org/computers/rsync_snapshots/#Appendix")
[Creating Incremental Snapshot-style Backups With rSync And SSH]("http://www.howtoforge.com/rsync_incremental_snapshot_backups")

rdiff-backup
[Automated Backups With rdiff-backup]("http://www.howtoforge.com/linux_rdiff_backup")

rsnapshot
[Backups are a snap with rsnapshot]("http://www.technetra.com/writings/archive/2005/08/20/backups-are-a-snap-with-rsnapshot") (if you have perl installed)

---

