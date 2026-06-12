---
title: "Home Server Q's on BackupPC + Offsite Mirror, Remote Access, and other suggestions"
date: 2008-02-01
forum: Server Platforms
---

### Post by cfaust on 2008-02-01
I'm finally getting around to putting together a home server.

My immediate goal is to automate & centralize backups of multiple XP and ubuntu machines, and to have an offsite backup.


Looking for any feedback or suggestions before I get too far into the process.

Hardware:
Core2 Duo processor
1 GB DDR2
500GB Seagate ES.2 x3 (/var/storage) (+ from different vendors)
80GB Segate (/)

Done thus far:
- Ubuntu 7.10 desktop (prefer the GUI for some things)
- BackupPC to automate backup's of machines on local network
- Samba for file and printer sharing

Questions...

**RAID**
Plan to use Linux RAID 5 w/ my set of three 500GB drives.  I often see linux RAID mentioned in conjunction w/ LVM, but I'm not really sure why I would want that extra complexity.  With the gutsy kernal, I've been able to add a drive to an existing RAID array (have been testing this out to make sure I know how to add & remove degraded drives from the array...might as well practice before disaster strikes).  Am I making some mistake by skipping LVM?


**Offsite**
I'm fortunate to have Verizon FIOS service (10/20M) in my area.  I have family with a small business about 30 miles away that also has FIOS.  As a separate project, I've been asked to setup a similar (but lighter-weight) file &  backup server there (5 PC's, but even fewer users).  I would very much like to synchronize the backup sets between these two locations on some fixed schedule, but I'm not really sure the best way to go about it.

I like the easy-to-use web frontend of BackupPC, especially because I can pretty much trust my "users" to be able to navigate their backups and restore files without to many phone calls.  

While beneficial to keep incremental backups on the local networks, I don't really want to use the disk space (and transfer time) to synchronize all the incrementals between locations.  Would prefer to just keep the most current copies up to date every few days.  Also, I  do *not* want to be dependent on the BackupPC software to read what has been transferred.  Nothing too personal on the files being restored, but I still need the transfer encrypted via SSH.  Have the parts for both servers at home while I configure things...is there any way to simulate remote (via intERnet rather than intRAnet) transfer without actually driving server B to another location?


**Remote Access**
Because I travel alot for work(w/ an XP laptop), it would be really nice to have some way to access files remotely.  Ideally, both as a network share and also via a GUI.  Any recommendations here?  


**DNS**
I have extra domain names available.  Any recommendations on dynamic DNS services that a) are free b) allow my own domain name c) offer port redirect (i.e., if port 80 is blocked)?


**What else**
Any thing else I consider at this point?



Thanks in advance for any tips or suggestions.

- Chris

---

### Post by cfaust on 2008-02-01
I'm finally getting around to putting together a home server.

My immediate goal is to automate & centralize backups of multiple XP and ubuntu machines, and to have an offsite backup.


Looking for any feedback or suggestions before I get too far into the process.

Hardware:
Core2 Duo processor
1 GB DDR2
500GB Seagate ES.2 x3 (/var/storage) (+ from different vendors)
80GB Segate (/)
battery backup & line conditioner (but a switching battery, not online)

Done thus far:
- Ubuntu 7.10 desktop (prefer the GUI for some things)
- BackupPC to automate backup's of machines on local network
- Samba for file and printer sharing

Questions...

**RAID**
Plan to use Linux RAID 5 w/ my set of three 500GB drives.  I often see linux RAID mentioned in conjunction w/ LVM, but I'm not really sure why I would want that extra complexity.  With the gutsy kernal, I've been able to add a drive to an existing drive to the RAID array (have been testing this out to make sure I know how to add & remove degraded drives from the array...might as well practice before disaster strikes).  Am I making some mistake by skipping LVM?  

Generally internet consensus (FWIW) is that XFS or EXT3 are the preferred filesystems.  I know I loose some drive space by choosing EXT3, as I currently have, but I'd rather loose 5-7% and be sure my files are safe.  The popularity of EXT3 also means it should be easier to find help (tutorials, etc) in the event I need to recover.


**Offsite**
I'm fortunate to have Verizon FIOS service (10/20M) in my area.  I have family with a small business about 30 miles away that also has FIOS.  As a separate project, I've been asked to setup a similar (but lighter-weight) file &  backup server there (5 PC's, but even fewer users).  I would very much like to synchronize the backup sets between these two locations on some fixed schedule, but I'm not really sure the best way to go about it.

I like the easy-to-use web frontend of BackupPC, especially because I can pretty much trust my "users" to be able to navigate their backups and restore files without to many phone calls.  

While beneficial to keep incremental backups on the local networks, I don't really want to use the disk space (and transfer time) to synchronize all the incrementals between locations.  Would prefer to just keep the most current copies up to date every few days.  Also, I  do *not* want to be dependent on the BackupPC software to read what has been transferred.  Am I better off just running a separate rsync in CRON?

Nothing too personal on the files being mirrored, but I still need the transfer encrypted via SSH.  I have the parts for both servers at home while I configure things...is there any way to simulate remote (via intERnet rather than intRAnet) transfer without actually driving server B to another location?


**Remote Access**
Because I travel alot for work(w/ an XP laptop), it would be really nice to have some way to access files remotely.  Ideally, both as a network share and also via a GUI.  Any recommendations here?  Prefer to use public/private key encryption.  


**DNS**
I have extra domain names available.  Any recommendations on dynamic DNS services that a) are free b) allow my own domain name c) offer port redirect (i.e., if port 80 is blocked)?


**What else**
Any thing else I consider at this point?  Would be nice to have some kind of monitoring that would check drive status (SMART), system temperatures, backup job status, etc and send emails if anything starts going wrong.



Thanks in advance for any tips or suggestions.

- Chris

---

### Post by freebeer on 2008-02-02
I'm in the process of completing something similar to what you're trying to do.  I can't answer all of your questions, but here's the approach I took fwiw:

I have 6 Win2k machines which I use rsync to automatically backup to my Ubuntu server running Samba as a PDC.  (The PDC/Samba part isn't necessary for this to work.)  I run DeltaCopy on the Win2K machines (it's really a Windows wrapper around rsync).  I can't trust the users to do backups of any kind (I get the usual "excuses"), so I set it up to automatically run in the background.  That's working out very well so far. Incremental backups take seconds and the users never notice it.

The next thing I'll implement is an off-site backup to my Ubuntu 6.06 at home.  It's not a high speed connection like you're talking about, but it'll fast enough once the initial backups are done.  That I'll do with a one-time backup and transfer via external hard drive.  Once that's done, I'll use rsync over SSH to do the incremental changes.  I've tested the rsync over SSH connection and that seems to work well, so I'm confident it'll work well once it's fully implemented.

---

### Post by K.Mandla on 2008-02-02
Moved to Servers and Security.

---

### Post by p_quarles on 2008-02-02
And duplicate threads merged.

Do not cross-post. If you think you have posted in the wrong topic area, ask a staff member to move your thread.

---

