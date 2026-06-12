---
title: "How to create a backup of everything like in NT?"
date: 2008-01-06
forum: Server Platforms
---

### Post by johnwillis on 2008-01-06
Here's a question for you.

I want to backup up all my ciritical data on my system.

Currently my server at home is running Ubuntu 7.10 (Studio Edition)

The files I need backing up are:

Apache Folder + Conf Files
PHP Configuration
MySQL Databases Version 5
Samba Network Shares located on root drive under /shares/Public

I am running my two drives as a Linux RAID 1 - I'm not too sure if this makes any differences.

What I am really after is a way I can create a nicely compressed file scheduled every other day (or maybe every night depending how compressed it is) and keep up to five, once I get to 5 overwrite the oldest.

It's what I've been doing in Windows for years. But now I want to get my automated backups sorted.

I don't mind editing files, etc. But if there is any app out there that people know of and love then please let me know!

:)

Thanks in advance for all your help

John

---

### Post by UbuWu on 2008-01-06
For general hints:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[rdiff-backup]("http://www.nongnu.org/rdiff-backup/") might be helpful

---

### Post by k_grdn on 2008-01-06
Hi John,

The simplest choice would be tar & rysnc.

Try man tar, man rysnc.

Amanda is a good solution for automated/scheduled backups.

Regards,

k_grdn

---

### Post by johnwillis on 2008-01-06
cheers for the suggestions guys. now i know where to look i'll have a mess about! (In VM of course!)

Cheers

J

---

### Post by invar9 on 2008-01-06
I back my system up using rsync to a backup server
rsync -avS /directories/to/backup root@backupserver:/backup/directory

IT works really well and extremily quickly. enen doing a off site backup. 

Hope ot helps

---

