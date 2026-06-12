---
title: "Need help: simple cron job won't work"
date: 2010-06-30
forum: Server Platforms
---

### Post by Saorex on 2010-06-30
Hi guys. I've been using Ubuntu for a couple of years now, but it's the first time I have to deal with Cron jobs. I'm on Ubuntu Server 10.04. I simply wan't to backup a MySQL database to a Windows shared drive on another server.

Here's my Bash script:

```
#!/bin/sh
SQL_FILE=/home/leclerc/mysql_backup/leclerc_portail_backup-$(date +%Y%m%d).sql
mysqldump --opt -u ****** --password=********** leclerc_portail > $SQL_FILE

# Tar compress all sql files into a single tgz file with the date in its name
cd /home/leclerc/mysql_backup/
TAR_FILENAME=sqldata-$(date +%Y%m%d).tgz
tar -zcvf $TAR_FILENAME *.sql

# Move the tar file to a Windows shared drive
mv $TAR_FILENAME /media/windows_shares/backup/
```

When I run this script as root, it works like a charm. But the job won't work correctly. I don't know what the problem is and the output log is empty.

Here's my entry in the root crontab:

```
0 10 * * * /home/leclerc/backup_scripts/mysqlbackup > /home/leclerc/backup_scripts/cronlog
```

Thanks a lot for your help!

---

### Post by arrrghhh on 2010-06-30
Did you put it into crontab using your user or sudo?  Perhaps it would work if you did ```
sudo crontab -e
```

---

### Post by Saorex on 2010-06-30
Yes I did:

```
sudo su -
crontab -e
```

---

### Post by arrrghhh on 2010-06-30
I don't think that works in Ubuntu, why can't you use the command I provided?

---

### Post by Saorex on 2010-06-30
I confirm that

```
sudo su -
crontab -e
```

and

```
sudo crontab -e
```

gives the same result.

Could it be that Cron doesn't know where the Bash executable is?

---

### Post by arrrghhh on 2010-06-30
Well root may not have permissions to your /home.  You're probably not truly running the script as root if you're running it by hand...

Have you tried moving the script to somewhere root would have access?

---

### Post by Saorex on 2010-06-30
Thanks a lot for your help. I just realized I didn't give the execute permission on the script. Sometimes you just start looking too deep when the problem is so simple. And like I said, it's my first time dealing with Cron...

Thanks again. I guess there are no stupid questions...

---

### Post by arrrghhh on 2010-06-30
Der, I didn't even think of that!  Ah well, glad you figured it out.  Please mark this thread [SOLVED] with the thread tools drop down!

---

