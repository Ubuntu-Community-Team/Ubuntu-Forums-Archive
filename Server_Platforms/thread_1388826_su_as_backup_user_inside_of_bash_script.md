---
title: "su as backup user inside of bash script"
date: 2010-01-23
forum: Server Platforms
---

### Post by bluethundr on 2010-01-23
Hello,

 I am attempting to write a backup script that will do the following:

 1) lock and flush tables on a mysql db
 2) dump the db to a file
 3) unlock the tables
 4) rsync the file to offsite storage

 It all seems to be going well. However, obviously I don't want to setup ssh to the storage server on another network as the root user without a password.

 so I am attempting to su as the backup user inside of the script
 but when I try to run the script everything happens as it should until I try to so.. then it jumps out of the script .. akss me to login as the backup user.. proceeds to rsync to the offsite storage

 it does all this and then resumes execiting the script.

 it is not going to be setup as a cron job. it will be executed manually. assuming that is the case, how can I get the script to run without prompting for a password?

 Here is what I've come up with so far...

assuming that the script is run as root and the identity of the backup user will need to be assumed inside the script without perstering the user to enter the backup user's password. 

```



echo ' '
echo "Database backup script is beginning"
echo ' '
/usr/bin/mysql -uroot -psecretPass -e 'USE the_db; FLUSH TABLES WITH READ LOCK;'
echo "Attempting to FLUSH TABLES on test_db with READ LOCK"
echo ' '
sleep 5
if [ $? == 0 ];
then
  echo "Flushing the tables on the_db with READ LOCK - SUCCESS"
else
  echo "Error on FLUSH TABLES with READ LOCK on the_db"
fi
echo ' '

echo "Attempting to dump the database the_db to file: backup-`date +%m-%d-%y`.sql"
echo ' '
/usr/bin/mysqldump -uroot -pseccretPass testdb > /home/test-bak/backupdb/backup-`date +%m-%d-%y`.sql
sleep 5
if [ $? == 0 ];
then
   echo "MySQL DUMP of the_db to backup-`date +%m-%d-%y`.sql SUCCESS"
else
   echo "MySQL DUMP of the_db FAIL"
fi
echo ' '

echo "Attempting UNLOCK TABLES on the_db"
echo ' '
/usr/bin/mysql -uroot -psecretPass -e 'UNLOCK TABLES'
if [ $? == 0 ];
then
 echo "UNLOCK TABLES on the_db SUCCESS"
else
  echo "UNLOCK TABLES on the_db FAIL"
fi
echo ' '

echo "Attempting to su as the backup user"
/bin/su test-bak
if [ $? == 0 ];
then
  echo "SU as backup user is GO!"
else
  echo "SU as backup user is FAIL"
fi
echo ' '


echo "Attempting to RSYNC the backup to offsite storage"
/usr/bin/rsync -avz -e ssh -i /home/test-bak/.ssh/id_rsa.pub /home/test-bak/backupdb/*  test-bak@backup:/home/test-bak/backupdb
if [ $? == 0 ];
then
  echo "RSYNC test_db backup file: backup-`date +%m-%d-%y`.sql to offsite storage SUCCESS"
else
  echo "RSYNC test+d backup file: backup-`date +%m-%d-%y`.sql to offsite storage FAIL"
fi
echo ' '


echo "*******"
echo ' '
echo "DONE and DONE"


```

---

### Post by lloyd_b on 2010-01-23
The problem is that you're executing the "su" without any special parameters, so it *thinks* you want to execute a shell as that user.

What you need to be doing is using the "-c" option of "su" to tell it to run a specific command as that user.  Using the info from your script, I think this is what you want:```
# switching to user "test-bak", and executing the 'rsync' command
/bin/su -c "/usr/bin/rsync -avz -e ssh -i /home/test-bak/.ssh/id_rsa.pub /home/test-bak/backupdb/*  test-bak@backup:/home/test-bak/backupdb" test-bak
```

Note: The return code you get from this will be the return code for the 'su', NOT the return code for the 'rsync' command.  

Lloyd B.

---

### Post by bluethundr on 2010-01-23
That did it!!! THANKS!!! Or as my wife would say 'Muito obrigado!' (actually it's Obrad-A for a girl, but I'm paraphrasing!) ;)

That did the trick. It could use a little polish and a little pizzaz but this is more or less the finished product...

:KS

```

#!/bin/bash



echo ' '
echo "Database backup script is beginning"
echo ' '
/usr/bin/mysql -uroot -psecretPass -e 'USE the_db; FLUSH TABLES WITH READ LOCK;'
echo "Attempting to FLUSH TABLES on the_db with READ LOCK"
echo ' '
sleep 5
if [ $? == 0 ];
then
  echo "Flushing the tables on the_db with READ LOCK - SUCCESS"
else
  echo "Error on FLUSH TABLES with READ LOCK on the_db"
fi
echo ' '

echo "Attempting to dump the database the_db to file: the_db-backup-`date +%m-%d-%y`.sql"
echo ' '
/usr/bin/mysqldump -uroot -psecretPass the_db > /home/test-bak/backupdb/the_db-backup-`date +%m-%d-%y`.sql
sleep 5
if [ $? == 0 ];
then
   echo "MySQL DUMP of the_db to the_db-backup-`date +%m-%d-%y`.sql SUCCESS"
else
   echo "MySQL DUMP of the_db FAIL"
fi
echo ' '

echo "Attempting UNLOCK TABLES on the_db"
echo ' '
/usr/bin/mysql -uroot -psecretPass -e 'UNLOCK TABLES'
if [ $? == 0 ];
then
 echo "UNLOCK TABLES on the_db SUCCESS"
else
  echo "UNLOCK TABLES on the_db FAIL"
fi
echo ' '



# switching to user "test-bak", and executing the 'rsync' command
echo "Attemtping to RSYNC the file the_db-backup-`date +%m-%d-%y`.sql"
echo ' '
/bin/su -c "/usr/bin/rsync -avz -e ssh -i /home/test-bak/.ssh/id_rsa.pub /home/test-bak/backupdb/*  test-bak@backup:/home/test-bak/backupdb" test-bak
if [ $? == 0 ];
then
  echo ' '
  echo "RSYNC the_db backup file: backup-`date +%m-%d-%y`.sql to offsite storage SUCCESS"
else
  echo ' '
  echo "RSYNC the_db backup file: backup-`date +%m-%d-%y`.sql to offsite storage FAIL"
fi
echo ' '


echo "Attempting to remove local copy of the_db backup"
echo ' '
sleep 5
/bin/rm /home/test-bak/backupdb/the_db-backup-`date +%m-%d-%y`.sql"
if [ $? == 0 ];
then
  echo "Remove local copy of the_db backup SUCCESS"
else 
  echo "Remove local copy of the_db backup FAIL"
fi
echo ' '
sleep 10
echo "Database backup script is finished"
echo "*******"
echo ' '
echo "DONE and DONE"


```

Love to give back when I can!!

:popcorn::popcorn::popcorn::popcorn:

---

### Post by bluethundr on 2010-01-24
Oh there's one final thing I need help with. This should be simple for you guys.



I need to set this script up as a cron job run by root.


Here is my crontab file:

```

[root@testbed test-bak]# crontab -e

45    3    *   *  *  root /home/test-bak/backupdb.bak

```

Now shouldn't this job run every day as the root user at 3:45 am? It doesn't and the cron daemon is definitely running. Also, how do I get the cron job to send me an email confirmation that the job was performed? I have postfix installed and running and can send mail from that machine via mutt.


Thanks!

---

### Post by bluethundr on 2010-01-24
This is a newer (better) version of my mysql database backup script I'd like to share. It's got environment variables at the top that you can change to make it useful in your environment. 

Also, I'd appreciate help on my cron job problem if there's any advice out there...

thanks

```

#!/bin/bash

#setting applictation variables
MYSQL=/usr/bin/mysql
MYSQLDUMP=/usr/bin/mysqldump
RSYNC=/usr/bin/rsync
GZIP=/bin/gzip
SU=/bin/su
SSH=/usr/bin/ssh 
RM=/bin/rm


#setting User / Password and File location / Host variables

MYSQLUSER=root
PASS=secretPass
USER=test-bak
KEY=/home/test-bak/.ssh/id_rsa.pub
DUMPFILE=dbs_beezag-backup-`date +%m-%d-%y`.sql
DPATH=/home/test-bak/backupdb
RHOST=backup
RPATH=/home/test-bak/backupdb 
LPATH=/home/test-bak/backupdb/*






echo ' '
echo "Database backup script is beginning"
echo ' '
sleep 5
$MYSQL -u$MYSQLUSER -p$PASS -e 'USE dbs_beezag; FLUSH TABLES WITH READ LOCK;'
echo "Attempting to FLUSH TABLES on dbs_beezag with READ LOCK"
echo ' '
sleep 5
if [ $? == 0 ];
then
  echo "Flushing the tables on dbs_beezag with READ LOCK - SUCCESS"
else
  echo "Error on FLUSH TABLES with READ LOCK on dbs_beezag"
fi
echo ' '

sleep 5
echo "Attempting to dump the database dbs_beezag to file: $DUMPFILE"
echo ' '
$MYSQLDUMP -u$MYSQLUSER -p$PASS dbs_beezag > $DPATH/$DUMPFILE
sleep 5
if [ $? == 0 ];
then
   echo "MySQL DUMP of dbs_beezag to $DUMPFILE SUCCESS"
else
   echo "MySQL DUMP of dbs_beezag to $DUMPFILE FAIL"
fi
echo ' '

sleep 5
echo "Attempting UNLOCK TABLES on dbs_beezag"
echo ' '
$MYSQL -u$MYSQLUSER -p$PASS -e 'UNLOCK TABLES'
if [ $? == 0 ];
then
 echo "UNLOCK TABLES on dbs_beezag SUCCESS"
else
  echo "UNLOCK TABLES on dbs_beezag FAIL"
fi
echo ' '

sleep 5
echo "Saving sapce with GZIP: creating $DUMPFILE.gz"
echo ' '
$GZIP $DPATH/$DUMPFILE
if [ $? == 0 ];
then
 echo "GZIP SUCCESS: $DUMPFILE.gz created"
else
  echo "GZIP on $DUMPFILE FAIL"
fi
echo '  '
    
sleep 5
# switching to user "test-bak", and executing the 'rsync' command
echo "Attemtping to RSYNC the file $DUMPFILE.gz to an offsite remote location"
echo ' '
$SU -c "$RSYNC -az -e $SSH -i $KEY $LPATH  $USER@$RHOST:$RPATH" $USER
echo ' '
if [ $? == 0 ];
then
  echo ' '
  echo "RSYNC dbs_beezag backup file: $DUMPFILE.gz to offsite storage SUCCESS"
else
  echo ' '
  echo "RSYNC dbs_beezag backup file: $DUMPTFILE to offsite storage FAIL"
fi
echo ' '


sleep 5
echo "Attempting to remove local copy of dbs_beezag backup"
echo ' '
$RM $DPATH/$DUMPFILE.gz
if [ $? == 0 ];
then
  echo "Remove local copy of $DUMPFILE.gz backup SUCCESS"
else 
  echo "Remove local copy of $DUMPFILE.gz backup FAIL"
fi
echo ' '
sleep 10
echo "Database backup script is finished"
echo "*******"
echo ' '
echo "DONE and DONE"

```

---

### Post by Windows95 on 2010-02-10
> **bluethundr said:**
> Oh there's one final thing I need help with. This should be simple for you guys.



I need to set this script up as a cron job run by root.


Here is my crontab file:

```

[root@testbed test-bak]# crontab -e

45    3    *   *  *  root /home/test-bak/backupdb.bak

```Now shouldn't this job run every day as the root user at 3:45 am? It doesn't and the cron daemon is definitely running. Also, how do I get the cron job to send me an email confirmation that the job was performed? I have postfix installed and running and can send mail from that machine via mutt.


Thanks!

I have the same problem as well.How can I make my cron code run as root?

```
@reboot /opt/liferay/liferay/tomcat/bin/startup.sh
```

thanks in advance

---

### Post by schwammkopf on 2011-02-07
I think, that the script is not working because the tables are not locked.
you can test this by opening a second shell. then connect to mysql via mysql -u root -p an try to UPDATE a table during your script is running on step "Flushing the tables on zabbix_proxy with READ LOCK - SUCCESS". then you will see that you can change your data.

---

### Post by RedScourge on 2011-05-03
I use mysqldump to do this, and transfer the file over SCP. I run ssh-keygen on all systems and put their public key into authorized_keys in the off-site backup system so that all backups can be done automatically of course. 

Mysqldump generates one large text file of sql commands, the advantage being that you can easily pick out exact data from the sql file later on and restore records individually if necessary, without needing to become an expert at point in time recovery with the MySQL binary log. 

I use subfolders within the /var/backup/ folder and a couple scripts which copy it from a daily folder to weekly rather than doing two backups on a weekly backup day, etc. What I find most important here is having some sort of failure notification built into the important stages, so I have done that too.

You can also add backup portions for important folders such as /etc or /var/www, though you might be better off using rsync over SSH for them, and then having the remote server zip up discrete copies of these repositories afterwards incase you want to revert to the state on a particular day, etc. To do that you would be well advised to launch a script that is on the off-site backup server script at the end of the script on the server you are backing up, this way you are certain that zipping does not begin until the transfer is complete.

My script looks something like this:

#!/bin/sh

BKDATE=`date +%Y`-`date +%m`-`date +%d`
YOUR_PASSWORD='your mysql root password here'
REMOTE_IP='10.0.0.0'

# only keep a few days of full backups on here because the hd fills up quickly
find /var/backup/daily/ -maxdepth 1 -name "*.tar.bz2" -mtime +5 -exec rm {} \;

# mysql db dump, skipping a table that has a huge amount of non-vital data in it
/usr/bin/mysqldump --add-locks --extended-insert --flush-privileges --no-autocommit \
        --user=root --password=${YOUR PASSWORD} --routines --single-transaction \
        --master-data=2 --flush-logs --quick --all-databases \
        --ignore-table=trans_records.Transactions
                > /var/backup/daily/mysql-${BKDATE}.sql

tar -cjf /var/backup/daily/mysql-${BKDATE}.tar.bz2 /var/backup/daily/mysql-${BKDATE}.sql > /dev/null \
        && rm -f /var/backup/daily/mysql-${BKDATE}.sql \
        || echo -e "\n\nWARNING: failed to tar mysqldump file and remove! \n"

chown bkpuser:bkpuser /var/backup/daily/*${BKDATE}*.tar.bz2
chmod 770 /var/backup/daily/*${BKDATE}*.tar.bz2

su bkpuser -c \
        "scp /var/backup/daily/*-${BKDATE}*.tar.bz2 ${REMOTE_IP}:/mnt/HD_a2/backup/daily" \
        || echo -e "\n\nWARNING: failed to transfer all files to backup device! \n"

---

### Post by kgatan on 2011-05-03
I dont know if its the correct way to run crontab as root but you can always "sudo crontab -e" to add root tabs.

---

