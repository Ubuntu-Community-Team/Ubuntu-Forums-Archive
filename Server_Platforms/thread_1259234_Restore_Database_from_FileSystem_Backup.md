---
title: "Restore Database from FileSystem Backup"
date: 2009-09-06
forum: Server Platforms
---

### Post by talsemgeest on 2009-09-06
Hey all, I recently had to reinstall Ubuntu Server Edition 9.04 on my server. My one problem is my wordpress blog that I was hosting. I have restored the wordpress files from a .tar.gz full filesystem backup, but the actual blog content was stored in a MySQL database. Is there any way to restore my databases from the .tar.gz filesystem backup?

Also, sorry for the duplicate post [here](http://ubuntuforums.org/showthread.php?t=1258227), but I think this forum is more appropriate. Any mod can feel free to delete that thread.

---

### Post by hessiess on 2009-09-06
If you dident backup the mysql db, then no, the database is independent of the filesystem, you have to back it up with mysqldump.

---

### Post by DaithiF on 2009-09-06
does your backup include the /var/lib/mysql directory?  if so then you should be able to restore the database.  Each database is contained in a separate subdirectory off /var/lib/mysql, so look for one named with the name of your wordpress database.  To restore it, shutdown the mysql server first
```
sudo /etc/init.d/mysql stop
```
before copying the backup-ed directory into the same location on your new server, then restart mysql server
```
sudo /etc/init.d/mysql start
```

note that its much better to take actual database dumps using the mysqldump command than to rely on this method.  so for the future, you should schedule something like this:
```
mysqldump -h host -u user -ppassword --databases database1 database2 > myfile.dump
```
as part of your system backup.

---

### Post by talsemgeest on 2009-09-10
> **DaithiF said:**
> does your backup include the /var/lib/mysql directory?  if so then you should be able to restore the database.  Each database is contained in a separate subdirectory off /var/lib/mysql, so look for one named with the name of your wordpress database.  To restore it, shutdown the mysql server first
```
sudo /etc/init.d/mysql stop
```
before copying the backup-ed directory into the same location on your new server, then restart mysql server
```
sudo /etc/init.d/mysql start
```

note that its much better to take actual database dumps using the mysqldump command than to rely on this method.  so for the future, you should schedule something like this:
```
mysqldump -h host -u user -ppassword --databases database1 database2 > myfile.dump
```
as part of your system backup.
Brilliant, worked like a charm. I am very grateful to you :)

---

### Post by terazen on 2009-09-10
I use this from sourceforge to backup my databases.  It rotates backup files and everything.

[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

Just make another script to copy the files to a seperate server every night and no worries.

---

### Post by talsemgeest on 2009-09-10
> **terazen said:**
> I use this from sourceforge to backup my databases.  It rotates backup files and everything.

[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

Just make another script to copy the files to a seperate server every night and no worries.
Thanks for that, I will look into it. :)

---

