---
title: "Ubuntu upgrade packages kept back"
date: 2018-08-03
forum: Server Platforms
---

### Post by thompsonavc on 2018-08-03
Ubuntu upgrade packages have been kept back  mariadb-client mariadb-client-10.1 mariadb-client-core-10.1 mariadb-server

Also why mariadb would stop randomly at 6:17 in the morning?

Any ideas?

---

### Post by LHammonds on 2018-08-03
Are your other issues resolved?  Would please update those threads and marked [Solved] if they are.  There are a lot of unanswered questions that future readers could benefit from.

Did you do an "apt-get upgrade" or "apt-get dist-upgrade"?

MariaDB does not just decide to randomly stop.  I have had DB servers up for years.  There is a problem it cannot resolve.  Maybe corrupt database/index due to the drive being full or whatnot.  The reason why it stopped is likely in the logs....around 6:16am

Make sure you are making backups:
```
mysqldump --all-databases > /tmp/all-db-after.sql
```

If the server and database software has been updating but the database administrator has not been upgrading the tables schemas, you might want to do that now.

```
mysql_upgrade
```

Reference: [mysql_upgrade](https://mariadb.com/kb/en/library/mysql_upgrade/)

LHammonds

---

### Post by thompsonavc on 2018-08-03
Somewhat, i'll update those posts.

Backing up databases using mysqldump now and moving forward.

Will try mysql_upgrade and see outcome.

---

### Post by thompsonavc on 2018-08-03
Backed up database via mysqldump. Ran sudo mysql_upgrade and got the below:

"This installation of MySQL is already upgraded t 10.1.34-MariaB, use --force if you still need to run mysql_upgrade"

---

### Post by LHammonds on 2018-08-03
Make sure you have an automated backup in place.  One that dumps those .sql files and then offloads them somewhere else in case the machine croaks.  Place those /tmp/*.sql files somewhere safe.  Anything in /tmp will be deleted upon next reboot.

Check the database log at the time near the shutdown at 6:16am.

**EDIT:** Also, did you do an "apt-get upgrade" or "apt-get dist-upgrade"?  I would recommend that you log each and every apt upgrade so you have an easy-to-find record of what was updated and when.  In my sig, I have a script on the Ubuntu Server tutorial that does the apt upgrades and logs the results.  You can run that manually or via root's crontab if you get comfortable with it.  For a long time, I did not automate updates because of bad experiences with grub updates going south back in the 10.04 days but it has been smooth sailing since then...especially when the partitions are designed to auto-expand in event of low disk space.

LHammonds

---

