---
title: "[SOLVED] How to get my Cron job to quit emailing me"
date: 2008-06-12
forum: Server Platforms
---

### Post by Titan8990 on 2008-06-12
I keep getting two email everyday which is a log of my cron job. I do not need this because my cron job saves a log file. How can I prevent cron to sending me these emails?

Also exim4 always freezes this email claiming "unroutable address". The cronjob is going to einstein.myworkgourp.local which is how it is in my /etc/hosts list. Here is a peak at my cron job and my /etc/hosts list.

```
127.0.1.1 einstein einstein.ssdllc.local
127.0.0.1 localhost MYTESTDOMAIN.COM
192.168.16.24 MYDOMAIN.COM
192.168.16.1 MYISASERVER
192.168.16.30 MYOTHEREMAILSERVER
```

```
#!/bin/sh

# Variable for the Program
BACKUPDIR=/
THEDATE=`date '+%Y%m%d-%s'`
LOGDIR=/var/log/backup
EXCLUDEFILE=/scripts/exclude
LOGFILE=/var/log/backup/rsync-$THEDATE.log
GZFILE=/var/log/backup/rsync-$THEDATE.gz
DESTINATION=/media/sda1/backup0
LAST=/media/sda1/backup5
MNTPOINT=/media/sda1/
BACKUPD=/dev/sda1

#Check to make sure that our backup drive is mounted - To be included later

umount /dev/sda1
mount /dev/sda1 /media/sda1


#If the log directory does not exist then create it

if [ ! -d $LOGDIR ]; then
    mkdir -p $LOGDIR
fi

#If the destination directory does not exist then create it

if [ ! -d $DESTINATION ]; then
        mkdir -p $DESTINATION
fi

#Rotate the backups

rm -rf $LAST
mv /media/sda1/backup4 $LAST
mv /media/sda1/backup3 /media/sda1/backup4
mv /media/sda1/backup2 /media/sda1/backup3
mv /media/sda1/backup1 /media/sda1/backup2
cp -al $DESTINATION /media/sda1/backup1

#Now run rsync to backup the filesystem

rsync -avr --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE $BACKUPDIR $DESTINATION

# gunzip the logfile
gzip -c $LOGFILE > $GZFILE

# delete the original, uncompressed logfile
rm $LOGFILE
```

I appreciate any insight anyone can provide.

---

### Post by erginemr on 2008-06-12
Hi, 

Please have a look at:
[http://res.mesonet.org/~billston/crontab/](http://res.mesonet.org/~billston/crontab/)

under the section "Why do I keep getting an email each time my Cron job runs?"

---

### Post by Titan8990 on 2008-06-12
Exactly what I was looking for, thanks.

---

### Post by erginemr on 2008-06-12
You are welcome. Take care. :)

---

