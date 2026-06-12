---
title: "Opinion - Backup Solution"
date: 2006-05-18
forum: Server Platforms
---

### Post by Useless on 2006-05-18
I am running a Ubuntu 5.10 machine here and i was wondering on peoples opinions for a backup solution.  At the moment the machine is a fairly old computer, seeing as how ubuntu doesnt need too much of a work horse to run all the process i want its fantastic.  The server is an apache server with a forum/message board on it, thats all it does. 

punbb - php (openldap) - mysql - apache

Its just a forum/knowledgebase we use here at work for our IT department.  

Now, at the moment, i create backups of the .sql database file regularly and have an image of the hard drive on a spare i keep just incase it fails.  Customizing the forum to how i wanted and adding all the libraries was a pain and i wouldnt want to lose it.  

My question, what other backup solutions could i be using?  Perhaps something that will automatically run every few days.  Or perhaps something with an incremental backup solution mixed with a full.  Also, this project may end up being scaled up to a much larger machine, so the imageing thing could be a problem when i move it to different hardware or even a different OS (Not likely, i have been using ubuntu for quite some time now and am VERY satisfied with it and its user base.)

Any ideas?  Thanks!

---

### Post by dragonfyre13 on 2006-05-18
Simple Backup. I've tried it, and I don't really like it, but everyone else does, so there you go. It was part of the last Summer Of Code.

---

### Post by Useless on 2006-05-18
i have tried it, its ok but every once in a while, it just doesnt seem to work.  Checking the processes it comes up as defunct.  Checking the FTP repository i send it to, it is empty.  Any other ideas?

---

### Post by dk_pa on 2006-05-18
You could give rsync a try.  It's easy to use and could be thrown in a cron job.  There are decent howto/tutorials around if you look.

---

### Post by linuxone on 2006-05-19
Hi,

[QUOTE=Useless]Its just a forum/knowledgebase we use here at work for our IT department.[/QUOTE]

if your company/IT department is doing a Network backup you can check if there is a Linux Agent for the used network backup software. Most commercial/professional backup software does have a Linux agent, ie. Veritas BackupExec, CA ArcServe/Brightstor, Legato ....

If not .... basicly the backup problem is a question of your need for security and how much you'll (be able to) pay for it. More security is more expensive.

Another solution is a backup from the Linux machine itself. To buy a streamer only for your Linux box is certainly to expensive but would be the very best solution. There were bundles (streamer hardware + backup software) available into the market - so check you get a Linux compatible software.

A less expensive solution is a second hard disc which can be used for a mirror raid (Raid-1) or a manual mirror copy (rsync or mirrordir) several times each day.

Or you create some shell scripts which will do the following:

-> export all MySQL databases to files (mysqldump)
-> create an tar.gz archive of all important files or the entire system
-> copy MySQL backup and tar.gz archives to an external system

My own very simple sample for the above mentioned script backup:
===== do_backup.sh =====================================
[color=green]#!/bin/sh
cd /usr/local/MYtools
**## prepare backup**
find /var/lib/mysql/* -type d | sort > /usr/local/MYtools/mysql.dirs
/usr/bin/replace -fs "/var/lib/mysql/" "" mysql.dirs
/bin/mv /backup/mysql/db_backups.tgz /backup/mysql/db_backups_old.tgz

**## write all DB tables to disc**
/usr/bin/mysqladmin flush-table

**## export all mysql databases**
for i in `cat mysql.dirs` ; do /usr/bin/mysqldump --all $i >> $i.sql ; sleep 2 ; done

mv -f  /usr/local/MYtools/*.sql /backup/mysql/
/bin/tar czf /backup/mysql/db_backups.tgz /backup/mysql/*.sql

**## create tar archive from specific directories**
/bin/tar czf /backup/linuxbackup.tgz /var/lib/mysql /var/www /etc

**## upload tar archives to an local ftp server**
/usr/bin/ncftpput -u username -p passwd serveraddress targetpath /backup/*tgz[/color]
=====================================================

Or use smbmount to copy the tgz archives to a network share.

Note: [**replace**](http://replace.richardlloyd.org.uk/) is a very usefull Linux tool which you need to install from the source archive.

Thomas

---

### Post by thematrix on 2006-05-20
I'm also looking for a backup solution for the moment... 
Definitely want to use rsync because of the efficiency and easy implementation/restore.
I'm considering the iomega REV... Anyone experience under linux with rev???

Thanks,

Frederic

---

### Post by Useless on 2006-05-22
[QUOTE=linuxone]Hi,


if your company/IT department is doing a Network backup you can check if there is a Linux Agent for the used network backup software. Most commercial/professional backup software does have a Linux agent, ie. Veritas BackupExec, CA ArcServe/Brightstor, Legato ....


Thomas[/QUOTE]


We do use CA Arcserve for our backups and we have Netware and Windows agents but that software is crap.  Always crashing, slow, constant problems....

I am gonna take some time to take a look at rsync and that script you have there.   Looks good, i'll post back with any results.

---

### Post by sgiunchi on 2006-05-23
[QUOTE=thematrix]I'm also looking for a backup solution for the moment... 
Definitely want to use rsync because of the efficiency and easy implementation/restore.
I'm considering the iomega REV... Anyone experience under linux with rev???

Thanks,

Frederic[/QUOTE]

I use REV on my server; it gets mounted, and it's seen as a normal disk. It's not speedy as it should be, but maybe it's a problem with processor speed (it's a celeron, and i .tar.gz on it).

Stefano

---

### Post by linuxone on 2006-05-23
Hi,

[QUOTE=Useless]We do use CA Arcserve for our backups and we have Netware and Windows agents but that software is crap.  Always crashing, slow, constant problems....[/QUOTE]

which version of ArcServe? Last version I bought for our IT department a few years ago was CA ArcServe 9, and I used their Linux agent on a kernel 2.4 based system. It runs perfect, no problems, no crashs, no speed problems. (the linux server and the dedicated backup server were connected via Gigabit Ethernet)

I've no experiences with newer releases of CA Brightstor/ArcServe.

> I am gonna take some time to take a look at rsync and that script you have there.   Looks good, i'll post back with any results.

rsync is ok. But basicly you can't compare tools like rsync with a professional backup software. It's really quite different.

rsync does synchronize directories. Which can be used to copy files from one to another disk.

ArcServe and any other backup software does a real backup on a specified backup drive (streamer). The (professional) backup software has a GUI and all jobs, any file, is stored into a database. You can select any file or directory or backup job from the database and restore the selected parts by a mouse click.
And you can do very different kind of backup, also a "GFS" backup (Grandfather - Father - Son) and more.

Backup is basicly part of your company (IT) security concept. Depending on your security concept a simple rsync copy may be perfect - or a professional backup may be required to fullfill your security needs.

Backup (means: data security) IS a VERY important. When nothing happens it may be a stupid and useless work, not worth a penny. But if the Raid-5 array of your main File or Database server crashes and everything seems to be lost, your security concept with a perfect backup (which can be restored within an hour) can save thousands of dollar or more .... :)

On my private Internet server I do use rsync **and** some bash scripts to export MySQL, create tar.gz archives from all important files and upload them to an external FTP server.

Into Office I use an SDLT streamer into an dedicated backup server with a Gigabit connection to a Layer-3 switch, CA ArcServe and ArcServe agents on all other servers. Backup jobs were done each night, 7 days a week, based on a "FS" (Father - Son) backup concept with 6 daily and 1 weekly streamer tape. 


Back to rsync. Because rsync is missing in my sample bash script below, here is another sample (it's a little bit more complex this time):

==== do_rsync.sh ===================
[color=green]#!/bin/sh
MOUNT=/bin/mount
UMOUNT=/bin/umount
MIRROR="/usr/bin/rsync -rulpogt --delete --stats -P"

## -------  prepare FS ---------------
$UMOUNT /media/sdb/var
$UMOUNT /media/sdb/home
$UMOUNT /media/sdb/boot
$UMOUNT /media/sdb
/sbin/fsck.ext3 -p /dev/sdb2
/sbin/fsck.ext3 -p /dev/sdb5
/sbin/fsck.ext3 -p /dev/sdb6
/sbin/fsck.ext3 -p /dev/sdb7
$MOUNT -t ext3 /dev/sdb5 /media/sdb
$MOUNT -t ext3 /dev/sdb2 /media/sdb/boot
$MOUNT -t ext3 /dev/sdb6 /media/sdb/home
$MOUNT -t ext3 /dev/sdb7 /media/sdb/var

DATE="`date +%d-%m-%Y_%H.%M`"
echo "--------> START $DATE <---------" >> /var/log/rsync.log

## -------  start rsync -----------
$MIRROR /boot /media/sdb  >> /var/log/rsync.log
$MIRROR /bin /media/sdb >> /var/log/rsync.log
$MIRROR /etc /media/sdb >> /var/log/rsync.log
$MIRROR /lib /media/sdb >> /var/log/rsync.log
$MIRROR /root /media/sdb >> /var/log/rsync.log
$MIRROR /sbin /media/sdb >> /var/log/rsync.log
$MIRROR /usr /media/sdb >> /var/log/rsync.log
$MIRROR /opt /media/sdb >> /var/log/rsync.log

## flush MySQL !!
/usr/bin/mysqladmin flush-tables flush-hosts flush-logs flush-status flush-threads

$MIRROR /var /media/sdb >> /var/log/rsync.log
$MIRROR /home /media/sdb >> /var/log/rsync.log

DATE="`date +%d-%m-%Y_%H.%M`"
echo "--------> END $DATE <---------" >> /var/log/rsync.log

sleep 2
/bin/sync
$UMOUNT -t ext3 /dev/sdb2 /media/sdb/boot
sleep 2
$UMOUNT -t ext3 /dev/sdb6 /media/sdb/home
$UMOUNT -t ext3 /dev/sdb7 /media/sdb/var
$UMOUNT -t ext3 /dev/sdb5 /media/sdb[/color]
=============================

Note: check the file size of rsync.log or add this log to logrotate. And if you plan to use this sample yourself ... of course you should check the rsync options if they match your needs.

This script takes care all partitions of the rsync target drive (sdb) were not mounted to be able a fsck could run. After re-mount all partitions to the right place current date and time will be stored to the log file. Then all root directories will be rsync'ed. Before rsync'ing /var all MySQL tables should be flushed to get a (mostly) clean database copy. Finally all partitions were umounted. End time stored into the log file.

Some maybe usefull parts are missing, ie. an e-mail with fsck status or/and rsync status ....

Thomas

---

### Post by nkr1ptd on 2006-05-23
Have you checked out Dirvish?  It is basically rsync, but with some additions.  It is in the repository but more info can be found at [www.dirvish.org](www.dirvish.org)

---

