---
title: "Cron Job home backup"
date: 2013-07-31
forum: Server Platforms
---

### Post by Di0g0 on 2013-07-31
Hi

Can someone explain me how to setup a cron job to make a full backup of my home directory every 1 hour?

Thanks.

---

### Post by oldfred on 2013-08-01
You can create a rsync task to backup /home. You may want to exclude some temporary files & caches as they are not required and just take time & space.

# cron now has folders for daily, weekly etc which just need to have executable scripts added.
       gksu gedit /etc/cron.hourly/mybackup
sudo chmod +x /etc/cron.hourly/mybackup

      [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

This is my command & I have mybackup_excludes.lst as another file in the same location to exclude lots of temporary files & folders. Best to manually run it first time and maybe add the test parameter to see if it is copying what you want. You can also add a log file but then it may file log quickly?

rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

Simple script to use as a starting point.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

   Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by Di0g0 on 2013-08-01
Right now I use a simple way to backup (since I have little files on this machine)

tar czvf mybackup.tar.gz /home/servers

It is possible to create a simple cron job to execute this command every hour and save on the root directory?

---

### Post by Di0g0 on 2013-08-01
Ok, I have the script created to backup de home/Servers folder to the root folder on the cron.hourly.

Now I have 2 questions:

1º This will backup automatically without any user intervention every hour? Only with the script inside that folder?

2º It's there any way to compress the hole folder? 

Thanks.

---

### Post by oldfred on 2013-08-01
If the script is executable and in the hourly cron folder, it will run every hour. 
 
Since you are using tar is is compressed. Are you writing that back into /home? If so I think in just a few hours you may fill /home or if it overwrites, you really only have one current backup. Is that what you want? If you delete a file then it is gone after one hour. Often backups are a daily, weekly, monthly rotation. Or a grandfather, father, son rotation.

Many years ago I used compressed formats to save data. But then I could not read floppy drive and lost it all. So now with space a lot less expensive I prefer to write files separately. If drive fails it still is gone, but sometimes if one file cannot be read, others can be where one compressed file with corruption is all the data.

I do not run backups automatically but have trim running in daily and have it create a log file:

#!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

*** Sat, 27 Jul 2013 07:44:50 -0500 ***
/: 1856671744 bytes were trimmed
*** Sun, 28 Jul 2013 07:49:58 -0500 ***
/: 2529820672 bytes were trimmed

---

### Post by Di0g0 on 2013-08-01
I changed the things a bit.

I created the script on my root folder:

```
#!/bin/bash# backup script
echo "Starting"
rsync -avvP /home/servers /root
echo "Done"
exit 0

```

And then I created a cron tab job to execute the script every hour.

So this will rewrite the files that have been changed on the original folder to this copy, right?

I want to make and exact copy of the original folder to the root folder every hour,  and this way appears to be working

---

### Post by ian-weisser on 2013-08-01
You are on the right track.

A next step is to redirect those -v and echos to a logfile. Or stop using them.
When cron launches the job, there is no display.

---

### Post by SeijiSensei on 2013-08-02
> **Di0g0 said:**
> I want to make and exact copy of the original folder to the root folder every hour,  and this way appears to be working

The copy will not be "exact" since it will contain files that have been deleted on the source.  I think this is a good idea for backups, but if you want an exact copy, you'll need to use the --delete and maybe the --delete-excluded switch as well.  You don't need --delete-excluded if you don't exclude anything (with an --exclude or --exclude-from directive).

I recommend reading the rsync [man page]("http://www.samba.org/ftp/rsync/rsync.html").

---

### Post by nerdtron on 2013-08-02
[FONT=arial]```
rsync -avvP /home/servers /root 
```
Are you putting your backup in the same machine? I say it's not a good backup at all it is the case.

I think it should be more like this if you backup to a remote server.
```
rsync -ar --delete --delete-excluded /home/your/folder user@ipaddress:/path/on/the/server
```
Ditch the -v option and the echo lines since cron doesn't have any output. You should turn -r for recursive and --delete options to delete the files you already deleted on your home folder but was copied on the last backup.
[/FONT]

---

### Post by LHammonds on 2013-08-05
Keep in mind that wherever your target is, that it needs to be managed so that it does not fill up.  This is especially critical if your target is in the root partition of your machine.

Setup your backup job to purge old files to keep it from growing uncontrollably.  Or setup a separate job to trim old archives.  For example, if the backups become useless after becoming a week old, setup your purge script to delete anything older than a week and run it once a day.

When I configure my servers, the partitions are separated from root so that there is just about no chance my server's root system will ever get filled up and cause stability issues even if purge jobs are not working as originally conceived.  I also make backups at several different levels since you never know the level of destruction that might occur.  I use rsync to make copies of files to a backup partition on the same server.  Those are then compressed into an archive file and copied to a remote server...from there a purge script keeps the amount of archives in check.  I also have another backup that backs up the entire server at the partition level and then gets copied offsite as well as having a copy on the local server.

To see how I do all this, check my sig for setting up an Ubuntu Server.

LHammonds

---

