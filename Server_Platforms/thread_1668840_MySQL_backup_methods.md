---
title: "MySQL backup methods?"
date: 2011-01-16
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-16
Not sure if this is the best place to ask this, but you never know :).

I am relativly new to MySQL, I have a home server running MySQL with 2 databases, I would like to automate a backup for both of these to an external source. What is the best method?

Neither of these databases are any larrger than 5MB

---

### Post by Ryan Dwyer on 2011-01-17
Create a cron job to mysqldump the databases, gzip them and scp them to the remote host.

---

### Post by SeijiSensei on 2011-01-17
I've used this script in the past to create rotated daily backups with mysqldump:

/usr/local/sbin/mybackup

```

#!/bin/sh

# User-defined parameters
BACKUPDIR=/backup/mysql

DBUSER="root"
DBPASS="ROOT_PASSWORD"
DBLIST="db1 db2"  # names of all DB's to back up

ROTATE=8        # keep this many backups

#DBHOST=          # leave empty for local socket, else hostname
#DBPORT=3306

LOG="$BACKUPDIR/mybackup.log"

###########################################################################

### Here be monsters, cap'n! ###

echo -n `date -R` >> $LOG
echo " MySQL backup procedure starting" >> $LOG

TODAY=`date +%y%m%d`
STALE=`date +%y%m%d --date="$ROTATE days ago"`

for D in `echo $DBLIST`
do
        NEWFILE="$BACKUPDIR/dump-$D.$TODAY"
        OLDFILE="$BACKUPDIR/dump-$D.$STALE"

        echo "Creating backup file $NEWFILE" >> $LOG
        mysqldump --user=$DBUSER --password=$DBPASS $D > $NEWFILE 2>>$LOG 3>>$LOG

        echo "Deleting stale backup file $OLDFILE" >> $LOG
        rm -f $OLDFILE 2>>$LOG 3>>$LOG

done

echo -n `date -R` >> $LOG
echo " MySQL backup procedure completed" >> $LOG

```

It includes the root password insecurely, though you can limit the damage with root ownership and 0700 permissions.  

To have this process run nightly, add a symbolic link to the script in /etc/cron.daily like this:

```

cd /etc/cron.daily
sudo ln -s /usr/local/sbin/mybackup

```

---

### Post by ZenMasta on 2011-03-14
I tried this script and tried to run it manually but I get an error.
./mysqlbackup.sh: 10: ROTATE: not found

Aside from the error, it appears to work fine. I checked my folder and the dumps are there

[edit]
nevermind, I removed the spaces. Thanks for this script :)

---

### Post by BkkBonanza on 2011-03-14
Once you have your backup files and you want to store them off site I'd recommend Amazon S3. The first 1 GB storage is free and it's cheap after that anyway. The nice thing is it's easy to automate in your script.

I use the [TimKay]("http://timkay.com/aws/") cmd line tool (very easy to install) which then just means I can add a command like below to copy files to S3 (assuming you created a bucket on S3 to put stuff).

s3cp mylocalfile mybucket

It's proven to be very robust over the last few years of managing backups for my servers from various locations on the web. Plus you gain some working knowledge of Amazon AWS which is pretty interesting nowadays.

---

### Post by SeijiSensei on 2011-03-15
> **ZenMasta said:**
> 
./mysqlbackup.sh: 10: ROTATE: not found

nevermind, I removed the spaces. Thanks for this script :)

Thanks for finding that error!  I've edited the original posting above to correct it.

You may discover that you can't run a script called "mysqlbackup.sh" out of /etc/cron.daily.  It will work if you [remove the ".sh" extension]("http://ubuntuforums.org/showpost.php?p=9918251&postcount=10").  This is a Debian/Ubuntu thing arising from the way dpkg works.  RHEL/CentOS systems don't display this limitation.

---

### Post by ZenMasta on 2011-03-18
Bkk thanks for the tip I'll consider that.

Seiji, I renamed and removed the extension but cron is not running the file. Ive tried in the hourly and daily folder.

root@ve:/usr/local/sbin# ls -l
total 4
-rwxr-xr-x 1 root root 999 Mar 14 14:03 mysqlbackup
root@ve:/usr/local/sbin# cd /etc/cron.daily
[email]root@ve:/etc/cron.daily[/email]# ls -l
total 16
-rwxr-xr-x 1 root root  633 Nov 18 13:21 apache2
-rwxr-xr-x 1 root root   89 Sep 29 17:07 logrotate
lrwxrwxrwx 1 root root   27 Mar 15 17:23 mysqlbackup -> /usr/local/sbin/mysqlbackup
-rwxr-xr-x 1 root root 3285 Feb 15  2010 sendmail
-rwxr-xr-x 1 root root 1309 Sep 29 17:08 sysklogd
[email]root@ve:/etc/cron.daily[/email]#

---

### Post by BkkBonanza on 2011-03-18
Make sure cron is running (**ps afx**) and maybe check the **/var/log/cron** file to see if there's any indications of error.

---

### Post by SeijiSensei on 2011-03-18
> **ZenMasta said:**
> Bkk thanks for the tip I'll consider that.

Seiji, I renamed and removed the extension but cron is not running the file. Ive tried in the hourly and daily folder.

First, does the script run correctly from the command prompt?

Next, follow BKKBonanza's advice to make sure that the cron daemon is running.  Do you have a /var/log/cron?  Look for the entries that correspond to the backup script?  What does the log report?  What if you run 'sudo service cron restart'?

---

### Post by stmiller on 2011-03-18
You can use logrotate to automatically rotate mysql backups. (As well as perform the dump!).

```

sudo nano /etc/logrotate.d/mysql-bkup

```

```

/var/backups/db.sql.gz {
daily
rotate 8
nocompress
create 640 root adm
postrotate
mysqldump -u root -pPassword --all-databases > /var/backups/db.sql
gzip -9f /var/backups/db.sql
endscript
}

```


You then have to do this one time or it will complain:

```

sudo touch /var/backups/db.sql.gz

```


edit:

You could also add an rsync line into that logrotate config file as well to send a copy to another machine.

---

### Post by SlugSlug on 2012-07-10
What does a file based backup miss out? I have nightly file backups and have had to restore once and everything seemed ok

---

### Post by LHammonds on 2012-07-10
I also use mysqldump to create a full backup of all databases and then again with individual tables so I can restore selectively.
 
See [this thread]("http://ubuntuforums.org/showpost.php?p=11951852&postcount=8") for details on how I create automated backups as well as the scripts I use.
 
LHammonds

---

### Post by Cheesemill on 2012-07-10
Also take a look at [AutoMySQLBackup]("http://sourceforge.net/projects/automysqlbackup/").

> AutoMySQLBackup with a basic configuration will create Daily, Weekly and  Monthly backups of one or more of your MySQL databases from one or more  of your MySQL servers.

Other Features include:
- Email notification of backups
- Backup Compression and Encryption
- Configurable backup rotation
- Incremental database backups

---

### Post by compiledkernel on 2012-07-10
> **Cheesemill said:**
> Also take a look at [AutoMySQLBackup]("http://sourceforge.net/projects/automysqlbackup/").

Stmiller and seiji  both provide the better down and dirty method for achieving the desired result.  

If your going to go with automysqlbackup, may as well just use Amanda.  Its industry standard, and achieves better results.

---

