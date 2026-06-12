---
title: "Automatic backup"
date: 2013-08-21
forum: Server Platforms
---

### Post by cartaysm on 2013-08-21
I have been manually backing up my server using tar for years... >  unfortunately I ran into a server issue and had to reformat and  reinstall off one of my backups, the problem with this is that the  backup was a week old.

Does anyone know of a way to automatically run tar backup every night on Ubuntu 12.04 server?

---

### Post by cartaysm on 2013-08-21
Just found this online (after my post, of course)... What do you think?
 	You can acomplish this via a Scheduling Program specific to *Nix platforms named CRON.
  	You will put the following into a file called runBackups.sh and save it to /root/nightlybackup/runBackups.sh

 > 
#!/bin/bash
mkdir -p /root/nightlybackup/`date +"%m-%d-%y`/
tar -czf /root/nightlybackup/`date +"%m-%d-%y`/web.tar /var/www/habachat/web
tar -czf /root/nightlybackup/`date +"%m-%d-%y`/etc.tar /var/www/habachat/etc
tar -czf /root/nightlybackup/`date +"%m-%d-%y`/git.tar /home/git
  	Then modify the file "/etc/crontab" to add the line:

 > 00 3 * * * root /root/nightlybackup/runBackups.sh  	Finally, you will need to allow your Script to actually be executed as a  script so the following command should take care of that.
 > chmod u+x /root/nightlybackup/runBackups.sh
Now at 3 am, your backup will run, You will still need to copy the 
backups off the server but how you do that is dependent on what you are 
copying the data to.  	You don't need to wait till 3 am for the script to run for a test. If  you want to test it, then as root run the following from the Command  line:
 > ./root/nightlybackup/runBackups.sh

---

### Post by LHammonds on 2013-08-21
Letting it run via crontab is certainly the way to go.  Make sure you include a path variable in crontab so your scripts know where to find executables where you don't specify the entire path.  Also make sure you specify which shell is being used at the top of the script (like in your example).  I just posted an [example here]("http://ubuntuforums.org/showthread.php?t=2167224&p=12764339#post12764339").

However, you need to make sure your backup also has a purge system.  Either build it into your backup script or in a separate script that will purge old backups.  For example, you could have it delete anything older than 2 weeks old...completely depends on how big your backups are and how much space you have.  You could even get fancier and set it up to continue keeping backups until it reaches a certain amount of space free.

How you have your system also matters in how you configure this.  If you have your entire partition scheme all in the root, then you need to make absolutely sure it never fills up your root partition.  However, if you designed your partitions to be separate such as having a /bak partition, you can modify the backups to consume most of the space there.

For my servers, I have my partitions separate so that the root never fills up.  I also have multiple types of backups at different levels.  I use fsarchiver to backup at the partition level so I can restore to a new machine in the event of a disaster and not have to re-install and re-config the OS.  The partition-level backup happens less frequently and I force a backup if my system is updated in a major way.

I have data-level backups that happen more frequently using rsync.  I have my data synced to a backup partition on an hourly basis which means I keep a local copy of all my data for quick-n-easy restore if something goes sideways.  But I also archive these backup folder (tar+7zip) so that I can retain backups that can be restore from much farther back points in time.  These archives are moved to a separate server that is offsite.

For details on how I have my sever(s) setup, see my sig.
LHammonds

---

### Post by TheFu on 2013-08-21
It looks fine, but  LHammonds makes some excellent points.  Fully specifying the path to all commands in a script is a best practice. Trusting the PATH in scripts, especially crons is dangerous.

At the end of your backup processing, perhaps pushing / pulling the files to a different box (over 500mi away) would be possible with rsync over ssh too?  I'd name the files .tgz since you are compressing them too.

For a small amount of data, **tar** is fine. When you have more data, you'll want to consider a newer style backup solution.

---

### Post by LHammonds on 2013-08-21
It might be best practice to include full path to every executable in a  script but the programmer in me prefers to set the path outside the  script or in one place so it can be easily adapted to different servers  or if I use different programs.

If cartaysm's valuable data is  very small, tar may be perfect for his needs.  If his system crashes and  he can rebuild it with just those files and is fine with that, it is  great for his situation.  However, I recommend creating a new server (in  a virtual machine) and test your backup strategy to ensure it actually  works the way you think.

LHammonds

---

### Post by CharlesA on 2013-08-21
> **LHammonds said:**
> It might be best practice to include full path to every executable in a  script but the programmer in me prefers to set the path outside the  script or in one place so it can be easily adapted to different servers  or if I use different programs.

If cartaysm's valuable data is  very small, tar may be perfect for his needs.  If his system crashes and  he can rebuild it with just those files and is fine with that, it is  great for his situation.  However, I recommend creating a new server (in  a virtual machine) and test your backup strategy to ensure it actually  works the way you think.

LHammonds

I usually cheese it when I do my scripts and have a variable named - rsync or tar or whatever and put the full path in there. It's probably a lazy way to do it, but it saves me headaches if the path is different.

+1 to testing on a VM.

---

### Post by Roasted on 2013-08-22
I know you specified tar, but have you considered back in time? A buddy just talked me into it tonight... and so far I am really liking it... there's a CLI version (as far as I'm aware) so I may try to integrate that with my servers. I have a main server and I have a nettop that acts as a secondary server. My main server rsyncs certain bits of data to the nettop nightly so I have a greater degree of backups available. Looks snazzy.

---

### Post by cartaysm on 2013-08-23
I have 0 experience with crontab so bare with me..

So I am going to handle this like so;
> 
crontab -e
Option 2



> 
########################################
# Name: Crontab Schedule for root user
# Author: cartaysm
########### backup system ##############
# 2013-08-23 - car - Created schedule
########################################

SHELL=/bin/sh
PATH=/home/me/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin


# m h dom mon dow command
#
# backup system
#
00 3 * * * root /home/me/backupsystem.sh 

create Cron job.


> 
mkdir /home/me
nano backupsystem.sh

Create backup folder and backup bash

> 
#!/bin/bash
#############################################
## Name          : backupsystem.sh
## Version       : 1.1
## Date          : 2013-08-23
## Author        : cartaysm
## Purpose       : Keep system backedup
## Compatibility : Verified on Ubuntu Server 12.04.2 LTS
## Requirements  : run as root
## Run Frequency : Recommend once per day.
## Parameters    : None
## Exit Codes    :
##    0 = Success
##    1 = ERROR: Lock file detected.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2013-08-23 Car Created script.
#############################################

## Import standard variables and functions. ##

tar -czpvf /home/me/`date +"%m-%d-%y`/web.tar.gz --exclude='' .

I dont have my complete tar statement me with me right now, but would insert it there.

> 
chmod u+x /home/me/backupsystem.sh

Make sh executable

---

### Post by kpothi on 2013-08-24
I'd recommend an offline backup, since the cost of offline storage is coming down every year. Personally, I use Dropbox for small documents and Amazon S3 for larger backups. While Dropbox may need a UI, sending backups to Amazon S3 can be done via command line. I use a Ruby gem named [backup](https://github.com/meskyanichi/backup) to do automatic backups and automatic purging of old backups. It also offers [a lot more features](https://github.com/meskyanichi/backup/wiki).

---

### Post by SeijiSensei on 2013-08-24
Unless you need to specify the time when the backup must be run, the easiest way to schedule a script to be run each night is to put the script or a link to it in /etc/cron.daily/.  You don't need to create a separate crontab.  All the scripts in that directory are run each night.  The time is controlled by the entries in /etc/crontab.  On my 13.04 machine, the daily scripts are run at 6:25 am.  If you want to run them at 3:25, just change the "6" to a "3" in /etc/crontab; you'll need to edit that file as root with sudo, of course.

[Here's a post I wrote recently describing the process.](http://ubuntuforums.org/showthread.php?t=2169500&p=12765385&viewfull=1#post12765385)

---

