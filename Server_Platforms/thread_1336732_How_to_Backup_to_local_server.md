---
title: "How to Backup to local server"
date: 2009-11-24
forum: Server Platforms
---

### Post by louisd11 on 2009-11-24
I would like to backup a server with many files on it to a local Ubuntu Server. I am going to follow the steps in this [tutorial]("http://ubuntuforums.org/showthread.php?t=81311"). But, how do I save it to my "network mounted" parttion.
Would it be: 
```
tar cvpzf /nfs/BACKUP/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

---

### Post by memilanuk on 2009-11-24
Well... assuming you have a NFS partition or drive mounted under /nfs, that looks like it should work.  You can always try backing up a smaller set of files for a test.

You might also try looking here:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

for ideas.

---

