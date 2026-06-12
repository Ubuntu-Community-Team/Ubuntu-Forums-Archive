---
title: "Backing up Ubuntu severs"
date: 2020-10-19
forum: Server Platforms
---

### Post by dellboy on 2020-10-19
I have a few Ubuntu severs I set up some dedicated severs some VPS I move to a new datacenter that I like but one thing they don't offer is a back up function we where using a well know vps company that offed an snap shot option so that you could restore the sever to that point as we not using that company anymore we no longer have this option what is the best option to make a back up off our severs via SSH as we don't run a desktop GUI or it course a PHP system would be ok if it has an lot foot print 

Thank you for your help

---

### Post by LHammonds on 2020-10-19
I backup using both methods.  We have our own internal virtual environment and backup software (Veeam Backup & Replication as well as Dell EMC Backup) take snapshots of the entire VM on a regular basis.

However, I also backup smaller data sets within Linux itself.

I will tell you how I do things at my shop but don't copy/paste my scripts and expect them to work out of the box.  They were tailored for my systems.  They can work for you too but it is best if you understand what they are doing.  But my solution may not fit your needs so I'll describe the overall process.

I have an additional / separate Linux server that serves as a backup repository.  It has jobs that are scheduled to pick up 2 types of backups (which are encrypted) depending on what is needed. Sometimes I use partition backups which can be used to create a new VM just like it or restore a partition.  The other is a backup of the config files / data such as database exports or archives of web sites and their configurations.

Each app server is responsible for creating these partition backups and placing them in /bak/partitions.  Copies of data backups that expected to be moved to the backup server are placed in /bak/remote

The backup server will then connect to the application server and grab these files and place them on the backup server.  The backups are not mutli-terrabyte so if you have something absolutely massive, you might want a different approach to handle sending just delta changes over the wire.  For me, a copy of an encrypted archive works and that is what I implemented.

Each server also has a [purge script]("https://github.com/LHammonds/ubuntu-bash/blob/master/purge-files.sh") that will remove old archives depending on the retention policy.

This is my backup server how I have it configured: [Backup server]("https://hammondslegacy.com/forum/viewtopic.php?p=887#p887")

The app servers where I want to include partition backups will be setup [like this]("https://hammondslegacy.com/forum/viewtopic.php?p=833#p833") (but the github link has the latest version of [back-parts.sh]("https://github.com/LHammonds/ubuntu-bash/blob/master/back-parts.sh") includes the data being pulled from the server rather than pushing it on a Windows mount which is less secure than a pull because if the app server is compromised, it cannot see or have access to the backup server)

I have a script for creating a local encrypted backup for [web servers]("https://github.com/LHammonds/ubuntu-bash/blob/master/web-backup.sh") and [MariaDB]("https://github.com/LHammonds/ubuntu-bash/blob/master/db-backup.sh") databases that places archives in /bak/remote folder which is picked up by the backup server using the [transfer data]("https://github.com/LHammonds/ubuntu-bash/blob/master/transfer-data.sh") script.

Each data backup that encrypts the files also has a corresponding script to decrypt the archives:  [Decrypt MariaDB]("https://github.com/LHammonds/ubuntu-bash/blob/master/db-decrypt.sh") and [Decrypt Web server]("https://github.com/LHammonds/ubuntu-bash/blob/master/web-decrypt.sh")

**EDIT:** But no matter how you design your backup, make sure you have what you need in order to restore it to a new machine or restore specific parts to the original server.  For example, if you are only backing up web and database files, make darn sure you have the steps necessary to rebuild that server just like it was originally before it died...such as what version of the operating system it was running, how it was install (much like my documentation on how I install Ubuntu Server) and what IP address it used, the users, privileges, etc.  Take your backup and restore it to a fresh machine and see if you can get a 100% working system from just referencing your backup files.  If you cannot do that, modify what you are backing up or include documentation on how to restore it when the server (or the entire site) is offline.

LHammonds

---

### Post by SeijiSensei on 2020-10-20
I have one local server and three virtuals at Linode. Every night my local server runs a cron job that uses rsync to suck over copies of the important files.  (I also have Linode's snapshot backup service enabled.)  I keep five days worth of backups in dated directories (e.g., 201019) plus one backup per month for each of the past five months.  My backup device is a 4 TB external USB drive.  Perhaps this script will give you some useful ideas.

I connect to the remotes via an OpenVPN tunnel which uses the 10.1.1.0/24 subnet.

```

#!/bin/bash

LOGDIR=/var/log/backup
DESTDIR=/media/external/backup
DIRS='etc usr/local var home'
FILEDIR=/usr/local/etc/backup
EXCL=$FILEDIR/local_excludes
ROTATE=5        # keep this many consecutive days
MONTHS=5        # keep this many months

TODAY=$(date +%y%m%d)
STALE=$(date +%y%m%d --date="$ROTATE days ago")
SMONTH=$(date +%y%m* --date="$MONTHS months ago")
LOG="${LOGDIR}/${TODAY}.log"

echo "*** - $(date +%c) - Backup starting - ***" > $LOG

cd /

STALEDIR="${DESTDIR}/${STALE}"
STALEMDIR="${DESTDIR}/${SMONTH}"

# keep one backup and log each month
if [ "$(date +%d)" != "01" ]
then
        echo "Deleting stale backup $STALEDIR" >> $LOG
        rm -rf $STALEDIR

        echo "Deleting stale log $STALE" >> $LOG
        rm -f $LOGDIR.$STALE.log

        # keep $MONTHS of backups
        echo "Deleting stale monthly $STALEMDIR" >> $LOG
        rm -rf $STALEMDIR
fi

echo "Checking for backup device" >> $LOG
# check that backup device is mounted
TEST=$(df | grep "/media/external")
if [ "$TEST" = "" ]
then
    # not mounted try remounting
    umount /media/external
    sleep 4
    mount /media/external
    sleep 4

    TEST=$(mount | grep "/media/external")
    if [ "$TEST" = "" ]
    then
        echo "Cannot mount backup device!" >> $LOG
        echo 'Cannot mount backup device' | mail -s 'backup failure' admin
        exit 1
    fi
fi

echo "Creating new backup directory $DEST" >> $LOG
DEST="${DESTDIR}/${TODAY}"
mkdir -p $DEST/local $DEST/server1 $DEST/server2 $DEST/server3

echo "*** - $(date +%c) - Backing up local directories - ***" >> $LOG
for d in $DIRS
do
    echo "Backing up $d" >> $LOG
    rsync -av $d $DEST/local --exclude-from=$EXCL --delete-excluded >> $LOG 2>&1
 done

echo "*** - $(date +%c) - Backing up remote servers - ***" >> $LOG
echo "*** - $(date +%c) - Backing up server1 - ***" >> $LOG
rsync -avr 10.1.1.1:/  $DEST/server1  --files-from=$FILEDIR/server1_includes --exclude-from=$FILEDIR/server1_excludes --delete-excluded >> $LOG
   
echo "*** - $(date +%c) - Backing up server2 - ***" >> $LOG
rsync -avr 10.1.1.2:/  $DEST/server2  --files-from=$FILEDIR/server2_includes --exclude-from=$FILEDIR/server2_excludes --delete-excluded >> $LOG

echo "*** - $(date +%c) - Backing up server3 - ***" >> $LOG
rsync -avr 10.1.1.3:/  $DEST/server3  --files-from=$FILEDIR/server3_includes --exclude-from=$FILEDIR/server3_excludes --delete-excluded >> $LOG

# keep another copy of today's backup on a different local drive
rm -rf /home/local_server/backup/*
echo "*** - $(date +%c) - Making local reserve copy - ***" >> $LOG
rsync -avr $DEST /home/local_server/backup

echo "*** - $(date +%c) - Backup concluded - ***" >> $LOG

exit 0

```
I keep the lists of files and directories to backup on the remote servers in /usr/local/etc. See the documentation for the "--files-from" and "--exclude-from" switches to rsync:  [https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync)

---

