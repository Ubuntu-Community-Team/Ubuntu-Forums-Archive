---
title: "backup of all the users (4  users) data to an external hard disk &amp; back up of Ubuntu"
date: 2017-10-16
forum: Server Platforms
---

### Post by raghavkishan on 2017-10-16
Hi,

I have created an Ubuntu server with four users. I have a new external hard-disk (WD) formatted with "ext4" file system connected to the server.
What application do I use, to set up a scheduled backup of all users and the system OS Image weekly ?
Any help is appreciated.
Thank you. personal information, please choose what you would like to         share:

---

### Post by oldfred on 2017-10-16
I am a home single user and do not necessarily have good backups.
Moving thread to server sub-forum where those who know more can help.

 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) 

I do use rsync for my backup of /home to flash drives, but theFu suggests rdiff

 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)

---

### Post by raghavkishan on 2017-10-17
Thank you.

---

### Post by LHammonds on 2017-10-17
If you have the space, you could use fsarchiver to create exact copies of your partitions.  I do this once a month on all my servers.  I keep a local copy in /bak and at a remote location.

As for data, you could rsync folders to a backup location (your external disk)

If the data is not too large, you could even keep revisions by doing a tar command of the folder you rsyn'd to.  You could schedule the rsync script to run a sync every XX amount of time and another job to compress (tar/gunzip) the rsync'd folder into a saved archive.  You can even have another script scheduled to run once a day to purge the oldest archives to ensure it doesn't fill up your backup location.  For example, you could have it delete any files older than 1 week.  But that all depends on how big the files would be and how much space you have on your backup drive.

There is a section in my tutorial on installing Ubuntu Server that covers [fsarchiver backup and restore](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p453).

LHammonds

---

