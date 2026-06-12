---
title: "Syncing"
date: 2005-09-08
forum: Server Platforms
---

### Post by billputer on 2005-09-08
I want my ubuntu server to sync with a smb share from another computer on a nightly basis.  I'd like it to be incremental so that it only copies the recently changed files.  

It seems like the easiest thing to do is to have crontab run a bash script that uses rsync.  Is that the best option, and what're the best resources for learning about using rsync?

---

### Post by swamytk on 2005-09-08
[http://aplawrence.com/Basics/rsync.html](http://aplawrence.com/Basics/rsync.html)

The best one is its man page in my experience!

---

### Post by relix42 on 2005-09-08
[QUOTE=billputer]I want my ubuntu server to sync with a smb share from another computer on a nightly basis.  I'd like it to be incremental so that it only copies the recently changed files.  

It seems like the easiest thing to do is to have crontab run a bash script that uses rsync.  Is that the best option, and what're the best resources for learning about using rsync?[/QUOTE]

I do this quite a bit and rsync via ssh is the easiest way to securely get this done.  A bit of scripting work around it and you can get dated backups, multiple versions of backup files, etc.

---

### Post by LordHunter317 on 2005-09-08
Or you can use rdiff-backup, which wraps around rsync and makes a reasonable general backup solution OOB.

---

