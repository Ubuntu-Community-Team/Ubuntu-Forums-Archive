---
title: "Postgres Backup using Cron"
date: 2008-09-18
forum: Server Platforms
---

### Post by dinkoarun on 2008-09-18
I have Postgres 8.2 running on my Ubuntu Server. 

Every night I manually Issue this command to backup my database:

*PGPASSWORD=xyz pg_dump -i -h localhost -p 5432 -U postgres -F c -b -v -f “/usr/local/backup/120.backup” databasename*

I need to create a backup script to issue this command and make full backups every night. The name of the backup file should be based on the date it was backed up.

I want the this script to be executed at 12 am every day.

I am a novice with scripts and cron, and I have read every guide regarding this but I am unable to make this to work. Can anyone help me out on this?

---

### Post by leef on 2008-09-18
I would try something like this;

script at /opt/backup-port
```

#!/bin/bash

time=(date +%y%m%d); # date in reverse so that lastest date appears last in the list of backup files.
PGPASSWORD=xyz pg_dump -i -h localhost -p 5432 -U postgres -F c -b -v -f "/usr/local/backup/$time.backup" databasename

```

chmod 777 /opt/backup-port add this line to /etc/crontab ;

```

1 0     * * *   root    /opt/backup-port

```

---

### Post by dinkoarun on 2008-09-18
> **leef said:**
> I would try something like this;

script at /opt/backup-port
```

#!/bin/bash

time=(date +%y%m%d); # date in reverse so that lastest date appears last in the list of backup files.
PGPASSWORD=xyz pg_dump -i -h localhost -p 5432 -U postgres -F c -b -v -f "/usr/local/backup/$time.backup" databasename

```

chmod 777 /opt/backup-port add this line to /etc/crontab ;

```

1 0     * * *   root    /opt/backup-port

```

I did this, but I am getting a zero size backup file with the output name "date.backup"

```
-rw-r--r-- 1 root root       0 2008-09-18 12:17 date.backup
```

The file permissions for /opt/backup-port is:

```
-rwxrwxrwx 1 root root  241 2008-09-18 12:04 backup-port
```

Is there something else I am missing?

---

### Post by leef on 2008-09-18
Try replacing "time=(date +%y%m%d);" with "time=`date +%y%m%d`" maybe bash is different on the server version try executing the "date +%y%m%d" command manually to check that that is working correctly.? I'm not sure why you are getting the zero size backups, I just copied your command and added the date information so make sure the command you stated was definately the one you have been using.

---

### Post by dinkoarun on 2008-09-18
> **leef said:**
> Try replacing "time=(date +%y%m%d);" with "time=`date +%y%m%d`" maybe bash is different on the server version try executing the "date +%y%m%d" command manually to check that that is working correctly.? I'm not sure why you are getting the zero size backups, I just copied your command and added the date information so make sure the command you stated was definitely the one you have been using.

The Date file seems to work fine now. But still I am getting zero file size. When I enter the command separately on the terminal I am able to get full output. There must be something wrong with the script. Any suggestions?

---

### Post by leef on 2008-09-18
Like I said I copied the command that you said you had to execute every night;

> 
PGPASSWORD=xyz pg_dump -i -h localhost -p 5432 -U postgres -F c -b -v -f "/usr/local/backup/120.backup" databasename


Now from looking at this command I can see several things that look like they could cause you a problem (given the fact that I don't use Postgres i can't be very specific). The first problem is that you have assigned a password to the variable "PGPASSWORD" and yet that variable / password is not passed to the command, which seems odd also it looks like you might need to change "databasename" to an actual database you want to backup. In other words don't just copy and paste it.

Now assuming you have done that, the only other thing that could go wrong is that you perhaps need to execute this command as a specific user (postgres for example?), if thats the case, you will have to edit /etc/crontab to execute the command as that user, rather than executing the command as root which is the current action. If you could give more information on the backup command perhaps we could help but it all looks rather vague at the moment. goodluck.

---

### Post by nickaceph on 2012-01-05
Hi sorry everyone to bring this thread back to life.
Im new to linux and Postgres but Iam getting there.
I kind a reach my limit on this one.

I would like to create a cron job my script is working when you manualy excute it.

```

#!/bin/bash
logfile="/dbbackup/pgsql.log"
backup_dir="/dbbackup"

touch $logfile

dateinfo=`date '+%Y-%m-%d %H:%M:%S'`

echo "Starting backup of database on $dateinfo " >> $logfile

dateinfo=`date '+%Y-%m-%d %H:%M:%S'`
timeslot=`date '+%Y%m%d%H%M'`

#pg_dump mydb | gzip -c > $backup_dir/mydb-$timeslot.sql.gz
/usr/bin/pg_dump mydb > $backup_dir/mydb-$timeslot.sql

echo "Database backup complete on    $dateinfo " >> $logfile


```

as you can see I have I line remarks (#pg_dump mydb | gzip -c > ....)
accutualy both line are working they generate the file when manually excuted but on the cronjob when executed the generated file is 0 and 4 bytes

all permission is ok. 
- pgsql.log = 777
- /dbbackup folder = 777


Thanks in Advance.:)

Nick Ace

---

### Post by nickaceph on 2012-01-06
Up Please...

Iam Using Ubuntu 8.04
PostgreSQL 8.3.16

Thanks...

---

### Post by gerrybrown on 2012-04-14
I use the following script in my ubuntu server. Though it is 10.04, it should work pretty much in 8.04 also. 

#!/bin/sh
date=`date -I`
pg_dump db_name > /var/lib/postgresql/8.4/backup/db_name-$date.sql

Note: pg_dump command can be run only by postgres user 
       and postgres user can write only inside /var/lib/postgresql/8.4 
       So when you create a cron job, create it as postgres user,
       and create a directory and give permission to postgres user and 
       give that folder as target for writing the backup file.  

Hope this helps..

---

