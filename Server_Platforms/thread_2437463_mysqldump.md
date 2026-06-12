---
title: "mysqldump"
date: 2020-02-24
forum: Server Platforms
---

### Post by paweltech on 2020-02-24
good morning,
with mysql I have to manage several databases and I want to do the scheduled backup with crontab
Using the backup command for all databases:
```
mysqldump -u root -p [password_user_root] --all-databases | gzip> /var/www/example.com/backupsql/wp_`date + \% F _ \% T`.sql.gz
```
I have no problems.
But if instead I wanted to backup the single database:
```
mysqldump -u root -p [password_user_root] --databases wp | gzip> /var/www/example.com/backupsql/wp_`date + \% F _ \% T`.sql.gz
```
I get the error

---

### Post by TheFu on 2020-02-24
[https://ubuntuforums.org/showthread.php?t=2401600&p=13802377#post13802377](https://ubuntuforums.org/showthread.php?t=2401600&p=13802377#post13802377)
is how I do it.  Notice that the password is read from a file, not in  the command options which any userid can see in the process table. Also, that the full path to any programs are spelled out. Never trust the PATH in any script, especially one started from cron.

There a many other solutions too.

---

### Post by LHammonds on 2020-02-24
Just want to +1 what TheFu said about placing the password in clear view as part of the command...which is exposed in your command history and the process list.  You can also store the password in my.cnf which will process the credentials automatically.

When scheduling in crontab, always specify the full path to everything (including the programs) and never use relative paths...unless you are explicitly specifying the path environment at the beginning.

You are probably just showing us the crux of the problem and what you are doing is more complicated than just scheduling that one command but in case it is not, I'd recommend calling a script from crontab and placing your commands inside that and including error-catching, logging and notifications so the backups can be more robust and let you know if things go sideways or maybe even self-correct if you plan ahead for certain scenarios (low disk space, write permissions, unmounted targets, etc.)

LHammonds

---

### Post by paweltech on 2020-02-25
> **LHammonds said:**
> 

You are probably just showing us the crux of the problem and what you are doing is more complicated than just scheduling that one command ...

LHammonds

Exact
Leaving aside security, I would like to understand why copying all the databases I have no problem, but if with the same command I copied only a single database, I get an error
So I ask you, what's wrong with mysqldump for single database?

I thank you for the precious support you are giving me!!!

---

### Post by EuclideanCoffee on 2020-02-25
Nothing is wrong for mysqldump single database. I do this routinely. Without the error message however, I cannot debug.

---

### Post by paweltech on 2020-02-25
> **EuclideanCoffee said:**
> Nothing is wrong for mysqldump single database. I do this routinely. Without the error message however, I cannot debug.

I try to explain myself better:
With the option for single databases I received the error:
```
root@linux:/home/paolo# mysqldump -u root -p [password_user_root] --databases wp | gzip > /var/www/example.com/backupsql/wp_`date +\%F_\%T`.sql.gz
Enter password:
mysqldump: Got error: 1049: Unknown database '[password_user_root]' when selecting the database
```



With the option for all databases the password is not required and the dump is performed correctly:
```
root@linux:/home/paolo# mysqldump -u root -p [password_user_root] --all-databases | gzip > /var/www/example.com/backupsql/wp_`date +\%F_\%T`.sql.gz
root@linux:/home/paolo#
```

---

### Post by SeijiSensei on 2020-02-25
I've never used the "--databases" switch, though I usually prefer to use --all-databases.  Try

```
mysqldump -u root -p [password_user_root] wp | gzip> /var/www/example.com/backupsql/wp_`date + \% F _ \% T`.sql.gz
```

---

### Post by paweltech on 2020-02-25
Using the --all-databases option, in case you want to restore a single db, how should I operate ?

---

### Post by spjackson on 2020-02-25
> **paweltech said:**
> I try to explain myself better:
With the option for single databases I received the error:
```
root@linux:/home/paolo# mysqldump -u root -p [password_user_root] --databases wp | gzip > /var/www/example.com/backupsql/wp_`date +\%F_\%T`.sql.gz
Enter password:
mysqldump: Got error: 1049: Unknown database '[password_user_root]' when selecting the database
```



With the option for all databases the password is not required and the dump is performed correctly:
```
root@linux:/home/paolo# mysqldump -u root -p [password_user_root] --all-databases | gzip > /var/www/example.com/backupsql/wp_`date +\%F_\%T`.sql.gz
root@linux:/home/paolo#
```

The correct syntax is "-p[password_user_root]" without a space. (As already said, it's not a good idea to do this, but if you are going to do it anyway you need the correct syntax.) This is also the case when using --all-databases, so I cannot explain how it works there. That format (with a space between -p and the password) does not work for me with --all-databases.

Also, the extra spaces in the date command arguments do not work either.
```

$ date + \% F _ \% T
date: extra operand &#8216;%&#8217;
Try 'date --help' for more information.
$ date +\%F_\%T
2020-02-25_13:54:21

```

---

### Post by SeijiSensei on 2020-02-25
> **paweltech said:**
> Using the --all-databases option, in case you want to restore a single db, how should I operate ?

Each database will begin with a "-- Current Database" comment and a CREATE DATABASE command like this:

```

--
-- Current Database: `anklaw`
--

CREATE DATABASE /*!32312 IF NOT EXISTS*/ `anklaw` /*!40100 DEFAULT CHARACTER SET latin1 */;

USE `anklaw`;


```

Find the one that corresponds to the database you're trying to recover. Copy from there to the next entry, paste it into a file, then run it from the command prompt using the mysql client.

---

### Post by TheFu on 2020-02-25
> **paweltech said:**
> Using the --all-databases option, in case you want to restore a single db, how should I operate ?

Back them up one at a time?  Then the backup file for each is separate already.  The link provide above is to a script that needs 1 line modified to handle each DB separately. 

Is there a specific reason to be tied to use either 
```
--all-databases
--databases
```
options?

Other solutions provided that work.

---

### Post by LHammonds on 2020-02-25
> **paweltech said:**
> I try to explain myself better:
With the option for single databases I received the error:
```
root@linux:/home/paolo# mysqldump -u root -p [password_user_root] --databases wp | gzip > /var/www/example.com/backupsql/wp_`date +\%F_\%T`.sql.gz
Enter password:
mysqldump: Got error: 1049: Unknown database '[password_user_root]' when selecting the database
```



With the option for all databases the password is not required and the dump is performed correctly:
```
root@linux:/home/paolo# mysqldump -u root -p [password_user_root] --all-databases | gzip > /var/www/example.com/backupsql/wp_`date +\%F_\%T`.sql.gz
root@linux:/home/paolo#
```

The "Unknown database" is telling me you are trying to backup a database that does not exist.

Go into mysql command-line and type:
```
show databases;
```

Make sure you see a database called "wp"

**EDIT:** When I run your command on my database server (with a database that actually exists) it works perfectly.

LHammonds

---

### Post by SeijiSensei on 2020-02-25
Simple script to iterate over the databases and create one backup file per database
```

#!/bin/bash

DATABASES=$(echo 'show databases;' | mysql -u root -p[password])
BACKUPDIR="/path/to/backups/$(date +%Y%m%d)"

mkdir -p $BACKUPDIR
cd $BACKUPDIR

for db in $DATABASES
do
     mysqldump -U root -p[password] $db > "$db.backup.mysql"
done

exit 0

```

---

### Post by paweltech on 2020-04-23
Hello everyone and thank you for your valuable support
Sorry if I return on the subject, but thanks to your advice I have improved the backup of my DB using a script.
I have given permissions to this script
If I run the script manually it works
From the cron, this doesn't work ... where am I wrong?

This is the root cron

```

* 2 * * * /var/www/examplecentos.com/bck_sql/backup.sh
* * * * * wget -q -O- wget -q -O- http://crm.examplecentos.com/cron/index

```

Thank you

---

### Post by spjackson on 2020-04-23
That first line asks for the script backup.sh to be run once every minute from 02:00 AM until 02:59 AM. That seems a bit odd... but if that's what you intend then ok.
Please elaborate on "this doesn't work". It could be the PATH or some other environment issue, depending on the content of backup.sh, but it's hard to guess unless some symptoms are known.

---

### Post by TheFu on 2020-04-23
[https://blog.jdpfu.com/2010/06/05/5-cron-tips](https://blog.jdpfu.com/2010/06/05/5-cron-tips) has some tips. Besides running every minute as  spjackson points out, it is likely that all the expected environment variables haven't been setup inside the backup script.  That is THE most common issue with crontabs, besides people trying to use GUI programs (GUI programs cannot be used in cron).

BTW, the wget line is wrong. Seems to have double commands "wget -q -O- wget -q -O-" 
should be 
```
/usr/bin/wget  -q -O-
```

I put this in every crontab, as a reminder:```

# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed
```
It doesn't work for /etc/crontab which has a slightly different format, but it does work for all crontabs that we edit using **crontab -e** under a specific username.

I wouldn't place a backup script under a place that can be accessed by a web-server, like /var/www/. That would be a security failure.  Keep the backup scripts either under the /root/bin/ directory or in the userid $HOME/bin/ for the account you have on the machine.

---

### Post by SeijiSensei on 2020-04-23
```
* 2 * * * /var/www/examplecentos.com/bck_sql/backup.sh
```

should probably be

```
1 2 * * * /var/www/examplecentos.com/bck_sql/backup.sh
```

which runs the script every day at 2:01 am.

The second command runs wget every minute throughout the day. Is this really what you want to do?

---

### Post by paweltech on 2020-04-23
> **TheFu said:**
> 

I wouldn't place a backup script under a place that can be accessed by a web-server, like /var/www/. That would be a security failure.  Keep the backup scripts either under the /root/bin/ directory or in the userid $HOME/bin/ for the account you have on the machine.

OOOK..Thank you...

Thanks to everyone for the support, it was actually a syntax error in the crontab

=d>=d>=d>=d>

---

