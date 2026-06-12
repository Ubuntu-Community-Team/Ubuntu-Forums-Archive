---
title: "Suggestions for Backing Up Server"
date: 2007-01-09
forum: Server Platforms
---

### Post by kramerkeller on 2007-01-09
Other than just copying the files every once and a while.  I was wondering if there was a good script or program for backing up server files every so often and perhaps deleting old back ups every so often.

I am a newb so all suggestions are welcome

---

### Post by hal10000 on 2007-01-09
There are a lot of Backup tools, beginning by simple backup scripts using tar or cpio to backup solutions for desktop boxes (like dar, konserve or sbackup) and complete network-ready backup tools which can backup servers and/or all your clients (like afbackup, amanda,bacula or backuppc).
You can also backup comlete partitions including mbr e.g. with partimage.
There are lot more tools, e.g. for backup on cd/dvd.

Just search your packages and try them.

If you want backup scrpits, e.g. for incremental backups you may find solutions if you google them, there are a lot of examples, may be you have to adapt them to your needs.

---

### Post by kramerkeller on 2007-01-12
I looked at some of the suggestions.  It seems a simple script would be best.

Basically I only have to back up one folder that has the website in it and the sql database.  Which I am pretty sure can somehow be backed up through a folder or a simple export out of the database first.

Anyhow - if anyone knows of a script I could put in crontab for backing up a folder and/or backing up mySQL I would really appreciate it.

---

### Post by hal10000 on 2007-01-12
If your sql database is based on mysql then you can use mysqldump to backup your databases It's a part of the mysql server package

---

### Post by hal10000 on 2007-01-12
No, mysqldump is not part of the package, i was wrong. But I'm sure it somehow belongs to the mysql suite, because i used it many times some months ago.

It is very easy to use adn can be used in cron jobs too

Here's a link of how to use it: [http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html)

---

### Post by gg234 on 2007-01-13
try this [simple guide ]("http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html")how to take backup using dar and kar

---

### Post by chrisfay on 2007-01-13
> Anyhow - if anyone knows of a script I could put in crontab for backing up a folder and/or backing up mySQL I would really appreciate it.

Where do you want to your backups to be stored? Locally or network?

---

### Post by kramerkeller on 2007-01-15
locally, would be fine.  However, I suppose it would be nice if I could sent a backup file to another computer on the network.

---

### Post by kramerkeller on 2007-01-15
I have been using dar, but I can't get it to copy just a folder with subfolders and files.  I have tried a bunch of different command options.

I have a web folder that has folders and files within it.  I just want to back that up using dar.

Help Please!

---

### Post by hal10000 on 2007-01-15
you may use kdar (which is a KDE frontend of dar with a gui).
It can do dry runs to test your settings and if you wish to it can create a shell script which you can then run.
Of course restoring is possible, too.

You might run it with root permissions if the files to be backuped are belonging to other users than you just working with.

---

### Post by kramerkeller on 2007-01-17
I am using dar.  I wrote a little script that backs up and then I added the mysql dump script  It updates each day, thanks for the help

---

### Post by jtc on 2007-01-17
Personally I'd like to mention [rsnapshot]("http://www.rsnapshot.org/").

It's easy to customize and it does pretty much everything you nead it to.

---

