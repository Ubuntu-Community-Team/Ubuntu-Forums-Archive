---
title: "Ubuntu as a scheduled backup server?"
date: 2006-08-08
forum: Server Platforms
---

### Post by axiomata on 2006-08-08
My family has a bunch of computers.  We have desktops at home, laptops at home, a desktop with me at college and a laptop at college with my sister.  Windows is of course the flavor of choice with everyone except me, the family IT guy, who dual boots into Ubuntu.  In my basic computer safety and maintenance speech to my sister before she heads off to college I mentioned that it is important to back up your documents, photos etc. but I realized it's hard to preach when you don't do it yourself, (that would be a lot of CD-Rs in my case).

I know there are automatic external USB hard drive backup options from Iomega and the likes as well online backup server options but I'd be willing to put in a little work to go the cheap route.

Would there be some, relatively easy way for me to take one of our PCs that isn't used anymore, perhaps expand the hard drive, install Ubuntu as the primary OS on it, connect it to our always-on DSL connection, and use it as a backup server for the other computers in the family?

Is there any open-source programs that could be installed on various Windows machines that could be configured to automatically backup selected folders at 4AM to this backup Ubuntu server?

Basically I need direction as to whether this would be a possibility as well as some direction to any tutorials on how I would get this setup.

Thanks,

---

### Post by jordilin on 2006-08-09
Yes, you can use BackupPC. If I'm not wrong is in the repos.
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/). There are other possibilities such as rsync, rdiff-backup, etc.

---

### Post by tagra123 on 2006-08-09
You are wanting to backup from various external locations through the internet to your ubuntu machine.

If this is what you mean then try using windows built in backup to run at 4:00 am and set up a dos batch file to ftp the backup file to the server.

OR better yet use tar for windows which allows more control -- ftp wont start until backup is finished.

[http://gnuwin32.sourceforge.net/packages/tar.htm](http://gnuwin32.sourceforge.net/packages/tar.htm)
[http://www.cgi-interactive-uk.com/backup_data_windows.html](http://www.cgi-interactive-uk.com/backup_data_windows.html)


On the windows machine create a script named c:/backups/ftpupload.txt

open ftp.youripaddress
username
password
cd backupfiles
cd mysistersbackups
dir
put sistersbackups.tar
bye

save the file

Also on the windows machine create a batch file named c:\backups\uploadbackups.bat

c:
cd c:\backups
REM IF USING WINDOWS BACKUP --COMMENT OUT NEXT LINE
tar -cv --file=backup.tar c:\backups\sistersbackups.tar  
Rem (you can also turn on compression too - read about tar options)
ftp -s:c:/backups/ftpupload.txt


Save the file

Use the scheduler to execute the batch file (I think thats allowed)


Information about setting up a ftpserver can be found here:

[http://www.ubuntuforums.org/showthread.php?t=51611](http://www.ubuntuforums.org/showthread.php?t=51611)



Here is a good link on setting up an ftp script




[http://www.computerhope.com/software/ftp.htm](http://www.computerhope.com/software/ftp.htm)

---

### Post by MJN on 2006-08-09
Given the backups are to be done over the Internet I would seriously consider such matters as bandwidth and security to be of prime importance.
 
For the bandwidth issue you really need to be looking at a combination of compression and incremental strategies - there really is no point uploading a file if it hasn't changed since it was last backed up.
 
The security side of things is also important if you've got sensitive/personal data - particularly given the aggregation of all that data into one place.
 
As mentioned by someone above, I would recommend Rsync for the job. It's pretty straight forward to use, supports compression, performs incremental backups (it's even capable of only moving the *parts* of files that have changed), can be interuppted at any time and restarted at a later date if required, data verification at both ends, and runs happilly over SSH and runs nicely on Linux/Windows alike.
 
Google for a stack of HowTo's, RTFM and peruse the numerous posts on here that cover its use.
 
Mathew

---

### Post by tagra123 on 2006-08-09
I use a combination of rsync and tar for my backups.

I have hourly backups of my important files using rsync so that I can go back to any point of the day - in case I really mees up one of my coding projects.

At 3:00 AM I do a tar backup incrmental for the same files.

Once a week I do a backup of the the entire home and data directories.

All of the above are automatic -- cron jobs.

Once a month i fire up sysrescuecd and back up the root partition, the home partition and the data (my source code) partition using part image.  I then burn these images to cd -- actually I burn a weekly CD of the source code unless I've made major change to a program that I would not want to lose.

With tar you can compress a decent amount too.  My scripts that I use actually dates the file as part of the filename and rotates the files deleting the oldest.  

To be best over the internet you could have the script upload only once a week.

I may post the scripts later if any interest is shown.

---

### Post by JonM1827 on 2006-08-09
Hey tagra... I was wondering if you could help me out...

How do you make the backups work like that...

if you could post the scripts that would be great!!!

Thanks in advance,
-Jon

---

### Post by axiomata on 2006-08-09
I appreciate all the replies.  I'll read up on some of the options mentioned and let you know if I run into any problems or get it up and running.

Thanks again all.

---

### Post by tagra123 on 2006-08-09
I'll try to put together a how to with the copies of the scripts I use.

Its pretty straight forward and very nice. You still need to get a copy on CD or DVD manually once in a while but most of the chore is taken care of automatically.

Give me a day or two and I'll make it all presentable.

---

### Post by axiomata on 2006-08-10
OK, that'd be very much appreciated.

---

### Post by chrisfay on 2006-08-11
> I'll try to put together a how to with the copies of the scripts I use.

I currently have a basic bash script in cron.daily that tar's most of my hard drive to a mounted samba share on a networked pc. I am curious how you do your incrimentals to keep from doing an entire backup each time. Do you use resync for that? And what could I add to the script that would:

1. Stop cron from emailing the transcript to my inbox. (the email is HUGE as its a trascript of the backup of basically my entire hard drive) I know I have to add /dev/null to the script but where? I added it to the end and the script just ran in the background doing nothing until I canceled it. 

2. Add the date to the backup filename while rotating the oldest date based on an alloted time delay.

---

### Post by tagra123 on 2006-08-11
See the Private Message I just sent.  

I'll email you a copy of the scripts until I get the how to put together.

---

### Post by n8bounds on 2006-08-12
> **tagra123 said:**
> See the Private Message I just sent.  

I'll email you a copy of the scripts until I get the how to put together.

I would be interrested in seeing your scripts as well, Sir

---

### Post by junglepeanut on 2006-08-13
Anxiously awaiting the how-to..thanks in advance.

---

### Post by axiomata on 2006-08-17
I'm coming back to this thread as I am running into a problem.  As far as scheduling an automatic backup to a ftp server on the windows machines I have found quite a nice little program called syncback.  I have tested it on a hosted ftp server and it works like a charm.

The problem is that I am having great difficulty setting up a ftp server of my own on this ubuntu box.  I've tried some tutorials for proftpd and pure-ftpd from this forum to no avail.  I think much of the problem comes from being behind a linksys router.  I have tried forwarding the ports and all but I'm still not able to resolve the server, even from within the network.  I've tried setting up a dyndns.org domain but I really don't think I know what I'm doing.I'll take any pointers I can get.  Is there one ftp server software I should definitely use, and stick with until I get it to work?  Any really good tutorials out there?

---

### Post by dannyboy79 on 2006-08-18
Tagra123, it's been about a week since you stated that you would post your scripts and what not. I am interested in your backup solution for your ubuntu box. If you could please please write up a small tutorial and provide your scripts I am sure they would not go to waste!!! Thank you if you can do that.

---

### Post by lamego on 2006-08-18
rsync is a great tool if you need frequent incremental backups.
Here is a detailed description on how to implement:

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by tagra123 on 2006-08-20
How To Backup A Ubuntu System with hourly, daily, and weekly backups.

The How to is now at:

[http://www.ubuntuforums.org/showthread.php?p=1402091](http://www.ubuntuforums.org/showthread.php?p=1402091)

---

### Post by kdnoel on 2006-08-20
Awesome!
Thank you so much I will be doing this myself!

---

### Post by tagra123 on 2006-08-22
Followup note regarding cronjobs

I prefer to use crontab which is how it is done in my how-to example above.


If you prefer you can also directly edit /etc/crontab but you will need to add root as the user to each one of the entries list in the cron-root.txt file and then cut and paste the intry into the /etc/crontab file.  


I think Ubuntu allows the /etc/crontab file to be used to have all entries in one file, but I still prefer to use the crontab command instead of editing the /etc/crontab files directly.

To read crontab's documentation type "man crontab" from a terminal.

To read Ubuntu's /etc/crontab documentation, just open /etc/crontab with a text editor.

The how to here:

The How to is now at:

[http://www.ubuntuforums.org/showthread.php?p=1402091](http://www.ubuntuforums.org/showthread.php?p=1402091)

shows both ways of adding the backups as cronjobs.

---

