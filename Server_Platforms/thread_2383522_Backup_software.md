---
title: "Backup software"
date: 2018-01-26
forum: Server Platforms
---

### Post by markeworth on 2018-01-26
Hey guys!
A little bit about the structure of my network. ESXi server with two virtual machines. One of them is the Windows-based server with read-only DC. Second I want to install ubuntu server. Her role will be backup Windows Server. 

I'm looking for some software that has a web interface, it will be nice, and which works with the schedule. And it will be awesome if it's can write a backup file to the ext4 file system.

Any recommendations? Thanks
(and maybe sorry for my English ;))

---

### Post by TheFu on 2018-01-26
Welcome to the forums.

There are commercial backup tools for ESX and ESXi.

Or you can use tools that ignore the hypervisor completely. None of them are perfect or trivial to setup, unfortunately.
[https://en.wikipedia.org/wiki/List_of_backup_software](https://en.wikipedia.org/wiki/List_of_backup_software) is a list, but the columns don't have whether there is a web interface or not. Sorry.

All backup software works on a schedule, but that would likely be controlled by crontab entries, not some GUI.

I use rdiff-backup, but it doesn't meet your requirements. No GUI. No web interface.

---

### Post by volkswagner on 2018-01-28
I'm really liking [Duplicati]("https://www.duplicati.com/")

---

### Post by TheFu on 2018-01-28
> **volkswagner said:**
> I'm really liking [Duplicati]("https://www.duplicati.com/")

I looked at Duplicati v1.2b on Windows many years ago. It was slow.  Like 8.5 hrs for 100Gb of data, slow.  It hadn't finished, so I killed the backup job.  Has it improved?  

Duplicity is the core engine for dejaDup, duplicati and a few others. That means those tools all have similar capabilities which check all the boxes for "best practices" for backups.  Very nice sets of features.  They are also more like 1970s backups which follow the old-school weekly-fulls, daily diffs backup schedules.  Every week, doing another full, long-running, backup is expected.  To restore, you start with the most recent "full" and add on the daily diffs to get to the date you want.  I've seen people using monthly full backups, which means you might have 31 days of "diffs" to apply during a restore.

Other backup tools become reverse diff based.  So the most recent backup is a mirror, like rsync would create, then older backups are diffs from that point.  90% of the time a restore is needed, you want the one from last night.  That means a simple cp is needed to restore in the newer systems.  rdiff-backup is like that.

Anyway, this is a great time to need a backup solution because there are many great choices to select from, at least for Unix/Linux systems. ;)

I'm ashamed to admit this, but on Windows, I do monthly images and don't leave any data on the Windows machines. All that data is stored on Linux-backed storage, so it gets backed-up by rdiff-backup.  I know that data is safe.  OTOH, the last time I installed any new program/patch on Windows was about 6 months ago, so the systems are very stable and don't get modified much.  We don't use Windows on the internet here.  It is part of our risk management strategy.

---

### Post by volkswagner on 2018-01-28
Although Duplicati 2.0 is still listed as Beta, it's been stable and reliable for me.

I only started using it about six months ago, so I don't have vast historical usage stats.
One small instance I'm running on a Windows VM to backup the shared files as follows.

Backup 1:
Source directory size = 6.6 Gig, ~16,300 files and 777 directories
Duplicati backup destination size = 4.82 Gig (with 12 versions of history, dedup and compression)
Backups take 1min 23 seconds to run. This is really a combination of diff and full
backups with deduplication. I can pic one of 12 historical versions
or restore entire directory from yesterday's backup (it only runs once per day)
this is running on Windows VM inside KVM

backup 2:
Source directory size = 1.5Gig, ~29,900 files and 8,667 directories
Duplicati backup destination size = 1.07Gig with 15 versions
Backups take 2min 25 seconds to complete
This is also on same Windows 10 VM
As you can see larger number of files takes longer even with much lower
total disk size.

Backup targets are smb shares on same hypervisor host.
Destination vDisk is on single 7200 RPM SATA while source vDisk is on MDADM RAID 10 7200RPM 4disk array

I wish I had large data set to show you :(

Perhaps we can extrapolate... if your data scaled like my slower backup, 100 gigs
should only take less than 3hrs, no?

---

