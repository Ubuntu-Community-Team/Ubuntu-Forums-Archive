---
title: "Find mySQL database data from live CD"
date: 2014-04-21
forum: Server Platforms
---

### Post by liste on 2014-04-21
Hello!

I installed Ubuntu Server July of last year, and (bad, bad), haven't made any backups of my Wordpress site since then.  Today my server ran into a database error, so I restarted it.  However on restart, I got a whole lot of errors in the GRUB[SUP]1[/SUP], and it won't boot.  Before I try fixing GRUB, I'd like to backup everything first in case something goes wrong, so I booted in live CD.

First, I rescued my files (HTML, PHP, etc.) and set up another computer with Ubuntu server.  Everything there seems to be intact.  Then I went to rescue my databases.  I understand that mysql data is supposed to be in /var/lib/mysql/ and indeed, there are all my database names listed as folders.  When I follow the steps from this post: [http://piyushparkash.blogspot.ca/2012/04/recovering-mysql-database-from-mysql.html](http://piyushparkash.blogspot.ca/2012/04/recovering-mysql-database-from-mysql.html), specifically: stopping mysql and copying the database folders from the old server, I can see them in phpMyAdmin, and I can also see the table names.

However when I click on the table names in phpmyadmin I get "#1146 Table 'wordpress.wp_commentmeta' doesn't exist.  I don't know whether the method prescribed in that post should really work, but it seems logical.  If it should, I'm assuming that I must have been hacked and all my databases were cleanly wiped out?  Since I have no backup, is there any other way that I can try restoring my databases from the old server?  Or have I likely lost nothing as soon as I can get my GRUB working?  Is it possible to backup and restore databases from LiveCD?  I have done a lot of Googling, but have found very little beyond that one post.

Thanks!

[SUP]1[/SUP]GRUB error:
error: unknown command '['.
error: unknown command '['.
error: unknown command 'save_env'.
error: unknown command 'search'.
error: unknown command 'linux'.
error: unknown command 'initrd'.
Similar, but not quite the same as this thread because GRUB does load: [http://ubuntuforums.org/showthread.php?t=1809562](http://ubuntuforums.org/showthread.php?t=1809562)

---

### Post by liste on 2014-04-22
Sorry - after spending several hours tonight searching for the answer, I wouldn't have guessed that I'd find the answer just minutes after posting the question.  :(

Anyway, in case anyone finds this using Google at a later time, the answer is that you have to also copy over "ibdata1", which can be found in /var/lib/mysql/ibdata1.

Have a great evening!  I'm just going to have to try to solve the GRUB loading issue now.  So if anyone has any ideas there, please share!  Thanks!

---

### Post by LHammonds on 2014-04-22
Sorry about your woes.  But once you get up and running again, please take a look at my How-To thread and look at how to backup your partitions on a regular basis using FSArchiver and rsync.

[Ubuntu Server 12.04]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191")

[Ubuntu Server 14.04]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=200") (in progress of documenting at the moment)

EDIT: I also have install/setup notes on MySQL in my sig which includes additional backups related to databases.

---

### Post by SeijiSensei on 2014-04-22
I also suggest using mysqldump to create a portable text-only backup of your databases.  Here's the script I run nightly to do that:
```

#!/bin/bash

BACKUPDIR=/home/me/mysql-backup
ROTATE=8
USER=root

LOG="$BACKUPDIR/mysql.`date +%y%m%d`.log"
STALELOG="$BACKUPDIR/mysql.`date +%y%m%d --date="$ROTATE days ago"`.log"

echo -n `date -R` >> $LOG
echo " MySQL backup procedure starting" >> $LOG

# run the backup and compress the result
CURRENT="$BACKUPDIR/mybackup.`date +%y%m%d`.mysql"
echo "Creating current backup file $CURRENT" >> $LOG
/usr/bin/mysqldump -u $USER --all-databases > $CURRENT 2>/dev/null
gzip $CURRENT

# retain monthly copy on 15th
if [ "`date +%d`" != "15" ] 
then
    STALE="$BACKUPDIR/mybackup.`date +%y%m%d --date="$ROTATE days ago"`.*"
    echo "Deleting stale backup files $STALE" >> $LOG
    rm -f $STALE 
    rm -f $STALELOG
fi    

# protect the privacy of the data
chmod 0600 $BACKUPDIR/*

echo -n `date -R` >> $LOG
echo " MySQL backup procedure completed" >> $LOG

exit 0

```
Note that I don't have a password for the root account.  If you do, then you'll need to add "--password=the-password" in the mysqldump line.  You would run this script as root from crontab.  If you include the password, I'd give the script 700 permissions so only root can read it. Create the backup directory before running the script, and make sure it is writable by the root user.

---

