---
title: "MySQL won't start"
date: 2013-05-26
forum: Server Platforms
---

### Post by itsonlybarney on 2013-05-26
Hey Everyone

For some unknown reason MySQL won't seem to start anymore.  The unusual case seems to have arisen without warning.

**Background:**
I ran an upgrade last weekend and the server has appeared to be running without any issues. However in the last hour or so when visiting the sites on my server, I have been getting "Error establishing a database connection" through WordPress.  When investigating I can't find a solution that has worked yet.

I have been running the command on the left, and I get the following immediately after:

```
  Command                      |    Result
sudo service mysql status      |  mysql stop/waiting
sudo service mysql start       |  start: Job failed to start
sudo service mysql stop        |  stop: Unknown instance:
```

Additionally I tried some of this without results - [http://ubuntuforums.org/showthread.php?t=2131362]("http://ubuntuforums.org/showthread.php?t=2131362&page=2")

Any advice you can share would be greatly appreciated. Also let me know what information would assist in a diagnosis.

---

### Post by DJ_Max on 2013-05-27
What do your logs say?

---

### Post by itsonlybarney on 2013-05-27
The files at:

/var/log/mysql.err
/var/log/mysql.log 

have 0 filesize

---

### Post by DJ_Max on 2013-05-28
Run it manually and see what errors you get

```
sudo -u mysql mysqld
```

and/or

```
sudo /etc/init.d/mysql restart
```

---

### Post by itsonlybarney on 2013-05-28
In the end I created a backup of my MySQL store (/var/lib/mysql) and re-installed MySQL.

I've had a look through the backup and it seems that some of the database files only have the .frm files, which I found it is only the table structure, and that the .myd are the data files.  I have no idea why the .myd files disappeared.  Luckily I had some backups from the last week for most of my sites, but have lost about 3 of them which I wasn't backing up.

---

### Post by DJ_Max on 2013-05-28
How were you executing backups?

---

### Post by itsonlybarney on 2013-05-28
The backups I had were through a WordPress plugin that was creating an SQL dump and emailing to me

---

### Post by DJ_Max on 2013-05-28
The SQL should have been all you needed. Assuming it dumped a sql file with DROP & CREATE tables

As for /var/lib/mysql, were you using InnoDB on all sites.

You can separate Data and Index Pages. This will cause any newly created InnoDB table to store data and index pages in an external .ibd file. But I doubt it would  be far.  I'm guessing the storage got moved somewhere along an update of some sort?

---

### Post by itsonlybarney on 2013-05-29
I don't recall setting them as InnoDB.

The thing that was annoying was that some of the DBs had .frm, .myi & .myd files while others only had the .frm files.  My understanding is that to recreate those tables you need at least the .frm & .myd files as the .myi can be created from those two.

I will just deal with it, luckily 2 of my 4 sites had SQL backups.  This will teach me to keep a proper backup.

---

