---
title: "Is there software to backup the system?"
date: 2019-09-14
forum: Security
---

### Post by dagmann on 2019-09-14
Either copy everything to a bunch of dvds or create an iso of the system.   Is either possible?
Has anyone used any software successfully to restore a Kubuntu system?

---

### Post by TheFu on 2019-09-14
Every system is a little different.  There are at least 30 different programs to do backups and how those are used depends on your specific needs - there are thousands of different answers.

Making ISOs isn't really the way that Unix system backups are done the last 20+ yrs.  A used $15 USB 250G disk is all most people really need for backup storage.  Backup tools that work best are automatic, daily, versioned, encrypted, and able to be stored offsite.  Kubuntu isn't important.  Any Debian-based system would have very similar requirements.  Some software, off the top of my head:
[LIST]
[*]rdiff-backup
[*]duplicity
[*]duplicati
[*]Deja Dup
[*]Back In Time
[*]fsarchiver
[*]rbackup
[*]rsnapshot
[*]AptTik
[*]ddrescue
[*]dd
[/LIST]
Those are the main ones, but there are others. Which of them meets your needs really depends on the specific requirements. This question gets asked here every few weeks and the answers the last 4+ yrs are the same as they are today.  

A good backup solution should need only 2-8 minutes daily to finish with a new backup set.
Restores should be 30-45 minutes, minus any huge media files, but the system should be exactly like it was at the time of the backup.  Then media files can be restored.

60 days of versioned backups need about 1.2x - 1.3x the total amount of storage being backed up, so it can be very efficient.  So, if you backup 10G of stuff, then the backup for 60 daily versions would be about 13G. Of course, it would depend on the rate of change of files, so there aren't any 100% accurate answers until you do it yourself.  I have systems with 60, 90, 180 days of versioned backups based on the needed risk mitigation each system needs.

Whatever you end up choosing, please, please test the restores before they are needed.  These forums have lots of people who believed they had backups only to discover that they didn't and didn't know because no test restore happened.

And whatever you do, please don't use tar or gnutar for backups. Those tools were designed when backups were 200 MB, not GB and TB sized.

About once a year, I need to use backups to restore something.  Most of the time it is because I've been stupid, but every few years, a HDD fails.

---

