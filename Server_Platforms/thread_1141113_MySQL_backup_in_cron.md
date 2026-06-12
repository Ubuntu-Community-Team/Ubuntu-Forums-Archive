---
title: "MySQL backup in cron"
date: 2009-04-28
forum: Server Platforms
---

### Post by Janjiss on 2009-04-28
Hello,
Im interested in creating backup for my mysql databases using cron - I would like mi databases to be saved like:
backup.mydomain.2009.04.04

How can this be done?

Thank you for any kind of information

---

### Post by terazen on 2009-04-28
This is what I use.

[http://www.howtoforge.com/creating-mysql-backups-with-automysqlbackup]("http://www.howtoforge.com/creating-mysql-backups-with-automysqlbackup")

---

### Post by tornadof3 on 2009-04-28
Create a shell script and save it somewhere like /root/mysqlbackup.sh, because it will contain your mysql password so needs to be kept safe.

```
#!/bin/sh

DAY=`/bin/date +%Y%m%d`
mysqldump DATABASE -u USERNAME -pPASSWORD > /path/mysql.yourdomain.$DAY.sql
```

and do

chown root:root /root/mysqlbackup.sh
chmod +x /root/mysqlbackup.sh

Then set this to be executable as a cron job. Job done!

---

### Post by Janjiss on 2009-04-29
Thank you very much :)

---

### Post by Cheesemill on 2009-04-29
I use the AutoMySQLBackup script from sourceforge:

[http://sourceforge.net/projects/automysqlbackup]("http://sourceforge.net/projects/automysqlbackup")

It takes care of backing up all your databases plus backup compression and rotation.

Cheesemill

---

### Post by pterosky on 2010-11-05
This cron job example will back up all localhost MySQL databases 11.34 every day, and a specific remote database at 11.38, to a folder you create (.mysql-backup) in your user directory. Next day gzip compresses all MySQL files found in the ~/.mysql-backup directory. The back ups are organized like this: .mysql-backup/2010/11

1. Create a new file, call it "mysql-cron-backup", and save it in the folder /home/USERNAME/cronjobs, substituting USERNAME, PASSWORD and DATABASENAME with your own:

30 11 * * * gzip -9 ~/.mysql-backup/`date +\%Y/\%m`/*.sql
32 11 * * * mkdir -p ~/.mysql-backup/`date +\%Y/\%m`/
34 11 * * * mysqldump -h localhost -u USERNAME '-pPASSWORD' --all-databases > ~/.mysql-backup/`date +\%Y/\%m`/allDB-localhost-`date +\%Y-\%m-\%d-\%H.\%M`.sql
38 11 * * * mysqldump -h mysql3.example.com -u USERNAME '-pPASSWORD' DATABASENAME > ~/.mysql-backup/`date +\%Y/\%m`/DATABASENAME-`date +\%Y-\%m-\%d-\%H.\%M`.sql

2. Go to the directory where you saved it and register the cron job from terminal:
# cd /home/USERNAME/cronjobs
# crontab mysql-cron-backup

3. You can install the program Scheduled tasks, which helps you see your cron jobs and test run them
# sudo apt-get install gnome-schedule

Note: The .mysql-backup folder is hidden, to prevent accidental deletion, so you have to press Ctrl+H to show it.

---

### Post by Vegan on 2010-11-05
I wrote a backup script with the help of a few people here. I posted it in my [developer forum under shell programming]("http://www.contract-developer.tk/phpBB3/viewtopic.php?f=16&t=18").

I am sure you can adapt it to your needs easily as its very clearly assembled and there are a few comments to help see what I did on my box.

---

