---
title: "Backup an entire webserver ubuntu 18.04"
date: 2019-03-24
forum: Server Platforms
---

### Post by tomdf on 2019-03-24
Hi guys,

i want to backup an entire webserver with ubuntu 18.04 and apache2 and i want to do that with rsync.
My question is which folders should i backup in case i need to recover the server?

Would you do the rsync directly in cronjob or would you prefer a script
does anyone has a script idea 

thanks in advance for your kind help

Tom

---

### Post by TheFu on 2019-03-24
"entire webserver" means you need to use an image-based backup, not rsync.

Which directories need to be backed up depends on how you run it.  The way you setup a webserver isn't the same as the way that I setup webservers. If you use ufw with manually entered rules to keep web-spam down, you might need to backup some areas that I don't.  I use ipset and iptables, which require backing up those files instead. If you use mysql, locations are likely different than my use of sqlite and postgresql.  I use nginx, not apache2 most of the time too.  Static files can be placed almost anywhere on a webserver - no way would anyone here know where you place them.  Those places need to be backed up.  

Getting a consistent DB backup is the hardest part. The DBMS needs to be quiesced. This can be accomplished a few different ways.  rsync cannot cause this. rsync is a poor backup tool, but almost all backup systems on Linux are based on librsync for efficiency reasons.

What are your goals with the backup AND the restore processes?
If it must be bit-for-bit, exactly the same, then you must, must, must, use image-based backups. These are inefficient, slow, and use tons of backup storage. Restores can be nearly bonehead, which shouldn't be underestimated at 3:30am.

If it must only be very similar to the original system with all the data being exact only, then you have many options that can be efficient on backup time, backup storage, and restoration time.  I use this method with **_*[SIZE=4]rdiff-backup[/SIZE]*_**. On all my servers that don't have TB of data, the restore process takes between 30 and 45 minutes.

In the professional world, backup requirements are determined by the RTO and RPO requirements and availability requirements, which are created by the people paying for all this work/hardware/systems.  [https://www.druva.com/blog/understanding-rpo-and-rto/](https://www.druva.com/blog/understanding-rpo-and-rto/)  

Most cat-video websites can have 2 minutes of downtime every day at 3am to perform backups.  Allowing a tiny big of downtime simplifies getting a consistent DB and the backup techniques.  OTOH, if zero downtime can be allowed, then some other techniques must be used.  The 2 main ones would be using LVM snapshots and backing up the snapshot data and the other would be dumping the complete DBMS to a text file and backing that up.  I prefer using LVM, but the storage involved must be setup using LVM at server-build time.  Snapshots are possible with other storage options like ZFS or if your server is really a VPS running inside a KVM environment with QCOW2 storage as the back end.  Other VM storage backends can support snapshots too.

Calling any backup tool directly via crontab usually isn't practical.  There are pre-backup and post-backup tasks necessary for any non-trivial server. Also, backups should always be "pulled" from a server, never pushed.  The backup server should initiate all backups, pre-backup and post-backup.  A script is needed. That script can be called from the crontab.

There are many examples of backups tools in these forums. Have you searched for all the prior advice?

Update: I know there are at least 50 responses, perhaps 100 to similar questions in these forums.

---

### Post by tomdf on 2019-03-24
HI,
thanks a lot for your answer.
Many information and very helpful as well.

I use ispconfig so i have backups of each website. So if an owner of the website wants to recover his data it is quite easy.

But:

if someone hacks my server then the problem start

Maybe to backup to entire webserver was not the right expression.

To setup a server with LAMP and ispconfig is made within short time. As well i will have every time a server as a backup so if one server get hacked i could backup the data to another server with a running LAMP and ispconfig.
So i think i have to backup the apache config files and sure the mysql data the data of the websites.
Which files you would recommend to backup?

As well an image base backup needs like you said a lot of backup space so i think its not the perfect solution.

My  goals with the backup and restore process are to be able to restore the server within lets say some hours. My plan is to make daily backups so if something happens i can restore the backup of the last day. I will put one backup on the server itself and another backup on a backup server.

I can allow some minutes downtime every day to perform backups thats not the problem. 

Thanks for the advise that backups should be pulled from a server, i didnt know that. What would be a good solution for pull the backup? as you said before rsync is not the best way for that. 

As well i was thinking about using bacula backup what do you think about that?

Finally i did not find the backup tools in this forum, maybe i should look in other forums to find about that. 

Thanks a lot for your help and maybe you can give me another idea how to proceed.

---

### Post by TheFu on 2019-03-24
I answered many of those questions in my reply above.
I don't do "LAMP" and have never used ISPconfig. Sorry.
I'm fairly certain that in other threads here, someone else provided a link to their exact backup scripts used to handle LAMP server backups.  I know that I've posted my MariaDB backup script and my rdiff-backup scripts over the years.

I've never used bacula. Did look at it a long time ago. Seemed like an overly complex tool for a linux-only shop like mine.

How to proceed? Find those other threads, read them. Follow the links they provide.  Server backups aren't 1 click and you are done.  Use the **advance search** feature.

```
my $backup_sources  = "--include /root
--include /etc
--include /var/www
--include /var/log/nginx
--include /var/lib/awstats
--include /usr/local
--include /home/typo
--include /home/thefu";
```
is for one of my servers.  Each backs up a few different places.  Sometimes I need more stuff in /var/.  What isn't in here is the pre-backup things I generate and place into /root/backups - system config stuff like storage, networking, crontabs, lvm, RAID ... if you are using shared hosting, that stuff might not be important.

Another server has this list:
```
my $backup_sources  = "--include /root
--include /etc
--include /usr/local
--include /var/www
--include /opt
--include /var/lib/mysql
--include /var/lib/znc
--include /home/thefu";

```

---

### Post by LHammonds on 2019-03-25
Regardless of what solution or how you create your backup, you need to test that backup and document the steps you take in order to restore the server.  Testing your restore process in a disaster event is NOT the time for testing.

If you are making an image-based backup of the entire server, try restoring it to another machine (or virtual machine).  If you are backing up specific files such as the web folders, web configuration, firewall rules, database, etc., try taking those files to a freshly installed server and see if you can restore those files and make an identical-working server.  Of course, if you are just backing up files, you need to install the OS, web server, database, etc. before trying to restore the files.

LHammonds

---

### Post by SeijiSensei on 2019-03-25
Whatever script you use, you should first create a plain-text dump of any MySQL, PostgreSQL or other DBMS you might be using.  Both [MySQL]("https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html") and [PostgreSQL]("https://www.postgresql.org/docs/9.3/app-pgdump.html") have handy programs for this purpose.  You could run them out of crontab to create the needed backup files before any scheduled transfer begins.

On remote systems I usually back up /etc, /home, and /var.  I have a server in my office that runs a script each night that goes around to the three remote servers I manage and sucks down those directories.  (I also back up /usr/local, since I put any scripts I've written in places like /usr/local/sbin.)  I put the database backups in a custom directory under /var.

Is this a physical system that you own or a virtual machine that you rent?  If the latter, I'd look to see if they do image-based backups like [Linode]("https://www.linode.com/backups") does. In the case of disaster, bringing back up a running image from a day or so earlier, then updating its files from your backup, is probably the safest bet. I've needed to do this at least once as I recall.

---

### Post by SeijiSensei on 2019-03-25
dup

---

### Post by TheFu on 2019-03-25
I was going through some old backup scripts ...

This dumps mysql.  Similar works for mariadb and postgressql.

```
#!/bin/bash
DB_NAME=redmine_sdf8232s2
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`cat ~root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/${DB_NAME}_`date +%Y%m%d`.gz
find  $BACKDIR -type f -name $DB_NAME\* -ctime 60 -delete \;

```

But if you can use snapshots from LVM or ZFS, all this goes away.  Also, note that the credentials are stored in a file, not passed in on the command line. Better for security, much better.

---

### Post by houstonbofh on 2019-03-27
OK, so this is driving a nail with a bullet, but...

The easiest way to do a full image backup is to start with a virtual machine.  Set up a server with KVM and install your web server there.  (And more)  And as long as you are using qcow, you can snapshot the image, and copy it with rsync or python scripts for S3 or B2, and then converge the disk image after.  Fairly fast with no down time at all.  And there are lots of reasons to be able to spin up a small server now and again.

---

