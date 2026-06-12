---
title: "Rsync server...Backup from WIN to Ubuntu"
date: 2006-07-17
forum: Server Platforms
---

### Post by olemadsen82 on 2006-07-17
Hey.

I have somwhat of a problem.

I have been trying for a couple of days now. 

My problem is i want to use Rsync to backup my customers servers. They are all windows servers.
I installed cygwin on my laptop, and running the rsync server from there. It was somewhat easy to get the backup script to run, and make an incremental backup to the server. But my problem is i cant make it rotate so that it would save the last 7 backups or more. And then delete the old ones. I found som guides to this on the forum and through google. But i must be to stupid to make this work. 

Would someone please help me, i need to know what to write in the windows batch file on the client to make it do the rotating backups.

Thanks a lot

P.S. Sorry for all the spelling and gramma errors

---

### Post by fdamstra on 2006-07-17
Have you thought about using something like [BackupPC]("http://backuppc.sourceforge.net/")?  It will handle the rotating of backups and will also use the server space efficiently (duplicate files are only stored once).

It appears to be in the repository.

---

### Post by datakid on 2006-07-18
Yes, I use backup pc as well, and it's fabulous - you can even have it save the last 7 days of backups, and the last x weekly or monthly backups (ie, I have it saving last 7 days, plus the friday backup from the week before).

Add on to that the fact that there's a special cygwin built for it, and that many of the problems sent to the email list are answered by the developers on the same day, means that it's one easy piece of software to use.

---

### Post by datakid on 2006-07-18
hmmm, the edit/delete button at the bottom actually only allows you to edit. Interesting. Anything smaller than 1 char is not allowed, and there's no "blow it away" button....

---

### Post by olemadsen82 on 2006-07-18
Thanks... it looks pretty good. Ill give it a try.

---

### Post by hagen00 on 2006-07-18
I followed this article

[http://servers.linux.com/article.pl?sid=04/11/04/0346256&tid=119&tid=47&pagenum=1]("http://servers.linux.com/article.pl?sid=04/11/04/0346256&tid=119&tid=47&pagenum=1")

There's a script there that does incremental backups and also one that lets you keep snapshots...the script is very good and worked out of the box for me.

---

