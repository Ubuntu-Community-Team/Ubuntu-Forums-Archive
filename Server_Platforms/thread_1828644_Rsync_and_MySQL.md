---
title: "Rsync and MySQL"
date: 2011-08-19
forum: Server Platforms
---

### Post by Medan on 2011-08-19
Hi

I am intending to backup my MySQL server using rsync. I know if the mysql server is shut down, and I rsync the entire /var/lib/mysql, I don't get any problems.  The problem is my database file itsself.

Rsync does not copy the changed data, it copies the entire database file, so rather than copying a few hundred MB, I end up copying an entire 37GB file, which is not efficient.

Is there anyway that rsync can be configured to only copy the changed data rather than an entire database file?
I have looked at rdiff-backup as it will work, but I've been instructed to use rsync only.

Thanks

---

### Post by collisionystm on 2011-08-19
Well the database file is constantly changed with MySQL. I would assume that rsync copies the entire file because the system assumes the entire file is being changed?

How do you know its actually copying 37gb at a time? Maybe the file is just being listed as 37gb because that is the actual size.

---

### Post by SeijiSensei on 2011-08-19
Rather than transferring the binary image, why not [dump the file]("http://ubuntuforums.org/showthread.php?t=1668840") to text with mysqldump, then compress that with gzip or bzip2 and copy the compressed file to backup?  It'll be a lot smaller than 37 GB is my guess.

rsync always copies only changes whenever possible.  This is much harder for binary files.  Any change to the database will create a binary blob that differs from the backup copy.  I have the same issue with VirtualBox VM images in my home directory.  Launching the image almost guarantees the entire big file will need to be backed up again.

---

### Post by kgatan on 2011-08-19
Im no expert but isnt taking a filesystem backup of a database like pulling the plug?
 
You have no idee what the database engine has stored in memory or is writing to the filesystem.
 
Use dumps instead to make sure you dont get a corrupt backup.
 
You can do incremental backups of Mysql using binary logfiles.
Link below might be of help,
 
[http://www.crnatural.net/mysql-backup](http://www.crnatural.net/mysql-backup)

---

### Post by memilanuk on 2011-08-19
> **kgatan said:**
> Im no expert but isnt taking a filesystem backup of a database like pulling the plug?
 
You have no idee what the database engine has stored in memory or is writing to the filesystem.

Read the first post again...

> *...mysql server is shut down...*

Pretty sure if the mysql server is shut down, it's done written everything to disk.

---

### Post by kgatan on 2011-08-19
Ah, sorry. Missed that part :)

---

### Post by Medan on 2011-08-20
> **kgatan said:**
> You can do incremental backups of Mysql using binary logfiles.
Link below might be of help,
 
[http://www.crnatural.net/mysql-backup](http://www.crnatural.net/mysql-backup)

Thank you, this looks like it might do the trick. A major reason for not going near mysqldump is the speed to reinsert all the data, and I needed a solution that could provide minimal downtime. I only need this for backup in my current configuration: master <=> master => slave.

---

