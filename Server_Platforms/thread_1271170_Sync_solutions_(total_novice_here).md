---
title: "Sync solutions? (total novice here)"
date: 2009-09-20
forum: Server Platforms
---

### Post by Icky_Ev on 2009-09-20
Running Jaunty on our samba box. 

I think what I'm looking for is a sync solution for server backups. We're at just about 1.2TB. I backup to external USB drives and to a 3rd slave drive within the server itself. Not an ideal set up, but it's a long story so just smile and nod. :popcorn: Go with me here.... 

I'm basically looking for a simple solution that will scan the samba drive for more recent files then on the backup drives and copy over just those files, instead of just doing raw dumps that take 8-10 hours. 

Directory structures can go 5-6 deep, there hundreds of thousands of files, and a number of the files are VERY large (20-30GB) 

I've looked at rsync and ChronoSync, and a handful of sync script examples. Is this what I'm looking for, and is there anything I need to be mindful of? 

Thank  you in advance. I keep telling my husband the first thing we're going to buy when this ship gets off the ground is a REAL network admin. :lolflag:

---

### Post by scorp123 on 2009-09-20
> **Icky_Ev said:**
> I've looked at rsync  Actually rsync is all you really need. It does what you want: Only copy stuff that really changed. So yes, the first backup will take bl**dy ages ... but all subsequent backups will finish quickly.

Maybe you'd be interested to read this:

"Easy Automated Snapshot-Style Backups with Linux and Rsync"
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

The web page is from 2004 ... but don't worry, it's all still valid.

---

### Post by Icky_Ev on 2009-09-20
Thank you! Much appreciated. :KS

---

### Post by KiLaHuRtZ on 2009-09-20
This is pretty much the code you need...

```
rsync -av --delete --delete-after /path/to/src-drive/ /path/to/dst-drive/ > /path/to/file.log
```

This will synchronize all your files on your primary drive to the backup drive.  The initial run will take some time, but after that, it will do incremental backups.  I've added the delete options which will delete anything off the backup drive that was deleted off the primary.  If this is not what you desire, just remove the two 'delete' lines from the command.

---

### Post by openfly on 2009-09-21
rdiff-backup might be worth looking into as well... it uses rsync.

---

### Post by nelmo on 2009-10-14
> **KiLaHuRtZ said:**
> This is pretty much the code you need...

```
rsync -av --delete --delete-after /path/to/src-drive/ /path/to/dst-drive/ > /path/to/file.log
```

This will synchronize all your files on your primary drive to the backup drive.  The initial run will take some time, but after that, it will do incremental backups.  I've added the delete options which will delete anything off the backup drive that was deleted off the primary.  If this is not what you desire, just remove the two 'delete' lines from the command.

Is there a way of getting this to work if I want to backup to a remote drive on a Windows (#-o yes, I know, I'm sorry) PC?

---

