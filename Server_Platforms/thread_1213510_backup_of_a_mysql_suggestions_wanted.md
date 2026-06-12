---
title: "backup of a mysql suggestions wanted"
date: 2009-07-14
forum: Server Platforms
---

### Post by mjfroggy on 2009-07-14
Hello all,

I have a ubuntu basic lamp server setup. The server runs a mysql database that has aabout 300,000 plus rows of data in it and I want some suggestions for doing mysql backups. 

I am looking for an open source (free) solution that would run via cron and daily and would only backupthe newest rows of data instead of backing up the entire database everyday I only want to back what is new in various tables.

I have looked at a few .sh scripts and also php scripts althougn php times out when trying to create this sized sql dump. Even using the export feature in phpmyadmin is getting to be really slow and almost impossibly to keep itgoing.

If someone knows of any open source software I have looked at zmanda and a few others that claim to be open source but charge. 
So any suggestions?

thanks all

---

### Post by druhboruch on 2009-07-14
This works for me.

[http://www.howtoforge.com/how-to-back-up-mysql-databases-with-mylvmbackup-on-ubuntu-8.10](http://www.howtoforge.com/how-to-back-up-mysql-databases-with-mylvmbackup-on-ubuntu-8.10)

---

### Post by FakeOutdoorsman on 2009-07-15
I use the [automysqlbackup](http://sourceforge.net/projects/automysqlbackup/) script.  This allows me to have incremental daily, weekly, and monthly backups both on the local production server and a remote backup.  I made a new mySQL user for the script that has only SELECT and LOCK permissions.  The script runs on the production server via cron.  An ancient 400 MHz backup server then automatically turns on (using a BIOS feature, but wake-on-lan could be used also) and then with cron runs:
```
rsync -av --delete -e 'ssh -p 5913' backup@domain.com:/productionserver/mysqlbackups /backupserver/mysqlbackups && sudo shutdown -h 30
```
Since rsync is used it will only download changes since the last backup and the connection is encrypted with ssh.  Public/private ssh keys are used for authentication so a password doesn't have to be typed.  After the backup is complete the backup machine shuts down.  I added the shutdown command to the sudoers file to keep from typing a password to shutdown.  Everything is now done automatically with no input from me.  Secondary remote backups are made to my desktop machine with anacron.

---

### Post by mjfroggy on 2009-07-15
Thanks for your replies

FakeOutdoorsman I downloaded and tried using the automysqlbackup.sh.2.5 script I edited it with my database user/pass and chmoded 755 but it does not seem to run? 

I get a 
[php]
-bash: automysqlbackup.sh.2.5: command not found
[/php]

when I type in
sadmin@lidevbox: /var/www/backups$ automysqlbackup.sh.2.5 

I then was thinking maybe the sh file should not go in the www directory so I moved it to just /var/ but still same error
Any suggestions for what I might of missed? again I uploaded to the server edited the file to have my database user/pass and database name and of course the server is localhost after changing and saving the file I then sudo chmod 755 the file

Suggestions??
thanks all

---

### Post by Raymond Day on 2009-07-15
You should install Webmin. It can backup the data base super easy and then can restore it just the same with Webmin. Very easy.

-Raymond Day

---

### Post by FakeOutdoorsman on 2009-07-15
> **mjfroggy said:**
> Thanks for your replies

FakeOutdoorsman I downloaded and tried using the automysqlbackup.sh.2.5 script I edited it with my database user/pass and chmoded 755 but it does not seem to run? 
...
If you want to run the script from the command-line you can do it like this:
```
./automysqlbackup.sh.2.5
```
With cron, you can either make a new cron job like so:
```
55 3 * * * /pathtoscript/automysqlbackup #Rotational mySQL backups
```
A good introduction to crontab: [How-to for crontab](http://ubuntuforums.org/showthread.php?t=102626) [ubuntuforums.org]. Or simply place the script in */etc/cron.daily*.  The script instructions recommends renaming the script to automysqlbackup if using cron on a Debian type system, but I'm not sure if that is applicable anymore.

---

