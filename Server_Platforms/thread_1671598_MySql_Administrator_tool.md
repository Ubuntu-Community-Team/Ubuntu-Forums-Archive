---
title: "MySql Administrator tool"
date: 2011-01-20
forum: Server Platforms
---

### Post by Nerflander on 2011-01-20
Hey there fellow ubuntu'rs,

I got this database running with valuable information. Now to automaticly back this up i can use this script... wich seems to be failing for me when i put it in the crontab.

Now i found this wonderfull MySql administrator tool and it works like a charm exept for the part it doesnt does its job when you schedule the job.

For exaple:
If you manual press start backup you get a very nice .sql file with everything innit. Now if you use the schedule system you do not.... Just a blue line of comment and thats it!

Anyone has experience in this program or has advice on this procces? 

Thnx in advance.:KS

---

### Post by Nerflander on 2011-01-20
bump

---

### Post by Thirtysixway on 2011-01-20
How were you scheduling it? and how were you putting it in cron?

---

### Post by mdlueck on 2011-01-21
What do you mean by "administrator tool"? PHPMyAdmin?

Personally I script my database backups in Bash scripts, and issue mysqldump to do so. I then check for bad return codes, and all sorts of nice padding on the script.

Each individual DB has a one line script to trigger its backup - calling the worker backup script with a series of arguments being passed in.

```
#!/bin/bash

/srv/www/bin/mysql-backup.sh.sh localhost UID PW DB /srv/www/sites/domain.org/db_backup BKFILE.sql

```

The worker script uses the args passed to it to backup the correct database, the directory / name target of the backup, ID/pw to access the DB, etc... (There actually is two script files, the outer one being a wrapper to capture all console output of the inner one.)

```
#!/bin/bash

umask 002
DATE=`/bin/date +%Y%m%d`
/srv/www/bin/mysql-backup.sh $1 $2 $3 $4 $5 $6 2>&1 | /usr/bin/tee -a /srv/www/reports/$DATE.mysql-backup.sh.log

```

```
#!/bin/bash -x

umask 002
DATETIME=`/bin/date +%Y%m%d-%H%M%S`
echo "mysql-backup.sh starting $DATETIME"

DATE=`/bin/date +%Y%m%d`
BKFILE=${5}/$DATE.${6}
/usr/bin/mysqldump -h $1 --default-character-set=utf8 -u $2 --password=$3 --opt --single-transaction $4 > $BKFILE
RC="$?"
[ "$RC" != "0" ] && /usr/bin/tail $BKFILE | /usr/bin/mailx -s "$DATE.$6 $4" ADMINUSERID

DATETIME=`/bin/date +%Y%m%d-%H%M%S`
echo "mysql-backup.sh complete! $DATETIME"

exit $RC

```

---

### Post by SeijiSensei on 2011-01-22
[http://ubuntuforums.org/showpost.php?p=10368151&postcount=3](http://ubuntuforums.org/showpost.php?p=10368151&postcount=3)

---

### Post by Nerflander on 2011-02-02
Il work this trough and report back when im done with it. Thx already for all the tips.

---

