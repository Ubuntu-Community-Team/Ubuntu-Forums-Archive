---
title: "Best way to backup mysql database?"
date: 2015-07-11
forum: Server Platforms
---

### Post by peter1897 on 2015-07-11
What are the best methods to backup my mysql database so whatever server crashes may occur i will be able to restore my database? Is it enough to use mysqldump to backup the database every day and then use rsync to create incremental backups on remote server? Or are there better methods?

---

### Post by SeijiSensei on 2015-07-11
[http://ubuntuforums.org/showthread.php?t=2285813](http://ubuntuforums.org/showthread.php?t=2285813)

---

### Post by peter1897 on 2015-07-12
So, do you recommend using full backup instead of incremental? Isn't that a less secure method? I mean if your database gets corrupt and your auto backup script create a backup of the corrupt database this will override the recent backup you have and then you will not have a good backup anymore from which to restore your database. And if you have incremental backups this can't happen because you will have other older backups from which to restore the database even if the most recent backup is corrupt.

Also, is it a good idea to use any of these backup tools: 
[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)
[https://wiki.zmanda.com/index.php/Main_Page  ]("https://wiki.zmanda.com/index.php/Main_Page")

---

### Post by SeijiSensei on 2015-07-12
I keep eight days worth of full plain-text backups using mysqldump and pg_dump, plus a monthly archival copy for good measure.  To be honest, I haven't had to restore any of my various PostgreSQL or MySQL databases in a very long time now.  Pretty much everything I have that matters runs on virtual machines at [Linode]("http://www.linode.com/").  If something seriously went awry with one of those, I'd restore the entire machine snapshot which is created each night.

I don't run web applications with lots of transactions like a shopping site, so my backup needs are pretty modest. 

I can't help with evaluating other backup programs.  I write my own scripts for these tasks.

---

### Post by peter1897 on 2015-07-13
I don't know if this backup strategy will be good for a big complex site but i guess i'll have to try and see what works best.

---

### Post by TheFu on 2015-07-13
Most SQL DBs run by folks here are relatively small. Mine are. A nightly (or hrly) dump with a timestamp, then compression is fine and fast. If the DB gets larger, you'll want to deploy LVM and use LVM snapshots in your backup techniques. This leaves the DB running, the applications running and still provides consistent backups (which is really critical for open files).


For dumping mysql DBs, here's the script I use.
```
#!/bin/bash -x
DB_NAME=redmine_default
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`cat ~root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/${DB_NAME}_`date +%Y%m%d`.gz
find  $BACKDIR -type f -name $DB_NAME\* -atime 60 -exec rm {} \;

```

Then just be certain to include the $BACKDIR in the normal backups for the system. For example, a small biz redmine DB I run is just 500KB when compressed per day. Keeping 60 days of backups is 30MB - a trivial amount of storage in the grand scheme.

Don't forget that the DB usually isn't the entire website and definitely is not the entire server.

---

### Post by peter1897 on 2015-07-13
Thanks, for the script. LVM can be deployed on dedicated server also, right?

---

### Post by TheFu on 2015-07-13
Actually, the only way I would deploy LVM is on dedicated hardware. That can be either a physical server or a virtual server with storage passthru.  For file-based VM storage, no way would I use LVM.

---

