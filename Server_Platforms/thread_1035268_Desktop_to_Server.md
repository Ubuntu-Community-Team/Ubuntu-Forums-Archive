---
title: "Desktop to Server"
date: 2009-01-09
forum: Server Platforms
---

### Post by grossinm on 2009-01-09
I have just setup my first Linux box.  Started w/ Kubuntu 8.04 and installed KDE to help me get familiar with it.  

At this point, it is sitting headless in a closet.  I SSH into it to modify settings.  

Where I am at right now is that I want to minimize the processes running on the machine, and if it is advisable, upgrade it to a server installation (if that will benefit the performance / reliability).  And I want to do this w/o breaking anything!

So far, I have disabled the KDE GUI from starting on the box (rm /et/rc2.d/ S13kdm K87kdm) and I am fairly certain that KDM or KDE is not running, but I want to be sure.  I also want to know what other processes I can kill/remove.  I ran top, and this is what it gave me:

top - 12:09:02 up 49 min,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  87 total,   1 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.2%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514092k total,   173136k used,   340956k free,     7376k buffers
Swap:  1502036k total,        0k used,  1502036k free,   132940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                  
    1 root      20   0  2844 1688  544 S    0  0.3   0:01.70 init                                                                                                                                                      
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                  
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                                               
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0                                                                                                                                               
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                                               
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                                                                               
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                                                                  
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                                                                                  
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                   
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                                                                 
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                                                                 
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                                    
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                              
  124 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                                                   
  158 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                   
  159 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                   
  160 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                                                                   
  201 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                                     
  202 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                                     
 1384 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                             
 1385 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                                     
 1531 root      15  -5     0    0    0 S    0  0.0   0:00.02 ata/0                                                                                                                                                     
 1537 root      15  -5     0    0    0 S    0  0.0   0:00.02 ata/1                                                                                                                                                     
 1539 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                                   
 1553 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                                                                  
 1581 root      15  -5     0    0    0 S    0  0.0   0:00.10 scsi_eh_0                                                                                                                                                 
 1584 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                                                 
 2309 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                                                                                 
 2310 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                                                                                 
 2360 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                                                                               
 2589 root      15  -5     0    0    0 S    0  0.0   0:00.02 kjournald                                                                                                                                                 
 2658 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                                                                                                                 
 2659 root      15  -5     0    0    0 S    0  0.0   0:00.00 usb-storage                                                                                                                                               
 2663 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_7                                                                                                                                                 
 2664 root      15  -5     0    0    0 S    0  0.0   0:00.02 usb-storage                                                                                                                                               
 2821 root      16  -4  2420  968  380 S    0  0.2   0:00.40 udevd                                                                                                                                                     
 3202 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                                                                                 
 4417 root      15  -5     0    0    0 S    0  0.0   0:00.00 kjournald                                                                                                                                                 
 4693 root      20   0  1716  508  440 S    0  0.1   0:00.00 getty                                                                                                                                                     
 4694 root      20   0  1716  512  440 S    0  0.1   0:00.00 getty                                                                                                                                                     
 4696 root      20   0  1716  508  440 S    0  0.1   0:00.00 getty                                                                                                                                                     
 4698 root      20   0  1716  512  440 S    0  0.1   0:00.00 getty                                                                                                                                                     
 4700 root      20   0  1716  508  440 S    0  0.1   0:00.00 getty                                                                                                                                                     
 4880 syslog    20   0  1936  648  512 S    0  0.1   0:00.02 syslogd                                                                                                                                                   
 4886 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0                                                                                                                                               
 4891 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1                                                                                                                                               
 5034 root      20   0  2456 1352  692 S    0  0.3   0:00.00 acpid                                                                                                                                                     
 5066 root      20   0  1872  536  444 S    0  0.1   0:00.04 dd                                                                                                                                                        
 5068 klog      20   0  3300 2120  424 S    0  0.4   0:00.14 klogd                                                                                                                                                     
 5091 messageb  20   0  2700 1040  740 S    0  0.2   0:00.04 dbus-daemon                                                                                                                                               
 5107 root      20   0  4580 1952 1708 S    0  0.4   0:00.00 NetworkManager                                                                                                                                            
 5121 root      20   0  3388 1164 1004 S    0  0.2   0:00.00 NetworkManagerD                                                                                                                                           
 5144 root      20   0  5316 1012  664 S    0  0.2   0:00.00 sshd                                                                                                                                                      
 5166 avahi     20   0  2864 1440 1220 S    0  0.3   0:00.02 avahi-daemon                                                                                                                                                            

Lastly, if I should upgrade to a server install, what is the best path / most reliable path to do so?  Should I uninstall KDE, or just leave it sit there in case I need it?

Thanks,

Greg

---

### Post by albinootje on 2009-01-09
> **grossinm said:**
> I have just setup my first Linux box.  Started w/ Kubuntu 8.04 and installed KDE to help me get familiar with it.  

At this point, it is sitting headless in a closet.  I SSH into it to modify settings.  
-- cut --
Lastly, if I should upgrade to a server install, what is the best path / most reliable path to do so?  Should I uninstall KDE, or just leave it sit there in case I need it?


Difficult question to answer.
First of all there's no such thing as "upgrading to a server install" possible (right now), perhaps you meant to reinstall with the server installation cdrom ?

I don't know about how Kubuntu does this, but with Ubuntu uninstalling the "complete desktop" in order to end up with a minimal (server) installation, means also no network connection at boot up will fail, unless you start editing /etc/network/interfaces accordingly beforehand (assuming that that file was pretty empty after the desktop installation).

If your server is just running inside the LAN i would leave it like this for the moment.

If you feel confident enough at the command line already, back up your /etc/ and /home and do an install from the server installation cdrom.

Personally I prefer configuring server via the command line, with the idea that I have more control and overview about what is going on compared to a GUI, but then again I'm using the command line since years, so I might be a little prejudiced :D

---

### Post by matt79 on 2009-01-09
I would save any info from the computer and download and install ubuntu server edition 8.04.

---

### Post by tubezninja on 2009-01-09
For purity's sake, you *could* backup and install Ubuntu Server edition, then restore all of your files from the backup.   Or, you could just....

```
sudo apt-get update && sudo apt-get install linux-server
```

Then reboot, and get pretty much the same effect.

[From what is listed here]("https://help.ubuntu.com/community/ServerFaq"),  the only benefit you would glean from re-installing using the server edition would be that you'd be booting a server optimized kernel.  And the above command does exactly that.

What's different in the server kernel?  [The list is here]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel").

Other than this, based on your top output, there doesn't seem to be much else running on your server that would impair performance.  If it were me, I wouldn't go through the trouble of reinstalling.  I would just install the server kernel image and be done with it.

---

### Post by albinootje on 2009-01-09
> **scaredpoet said:**
> For purity's sake, you *could* backup and install Ubuntu Server edition, then restore all of your files from the backup.   Or, you could just....

```
sudo apt-get update && sudo apt-get install linux-server
```

Then reboot, and get pretty much the same effect.

The OP wanted to remove packages however.

The linux-server meta-package will in the setup of the OP only install the linux-image-server kernel, nothing more.

Easiest to remove packages from KDE is probably to remove all qt libraries.
Check them with :
```

dpkg -l |grep -i qt

```
Then remove them with for example :
```

apt-get remove --purge libqt4-* libqt3-* libqtcore4 libqtgui4

```
That will make some free space already :)

---

### Post by tubezninja on 2009-01-09
> **albinootje said:**
> The OP wanted to remove packages however.

From what I read, he just wanted to kill processes that were taking up resources.  Seems he's already done that.  But what you suggest is also good advice.

---

### Post by albinootje on 2009-01-09
> **scaredpoet said:**
> From what I read, he just wanted to kill processes that were taking up resources.  

You're right.
> 
Seems he's already done that.  But what you suggest is also good advice.
Hmmm. 
Perhaps the OP should clarify whether he wants to keep the GUI or not.
:|

---

### Post by grossinm on 2009-01-09
Great advice from everyone!  

My goal is to have a stable installation that does not need to be tweaked all of the time.  From what I have read, it seems right now that leaving the system alone, including the KDE files, is best.  If I ever want to StartX, I can do that, but for now it will just boot to the command line.

My biggest question from the post, was to look at the processes that are running, to ensure there weren't any unnecessary items running.  It sounds like there are not any.

As I am using this for a backup server only (actually backing up a Timecapsule, yes I'm a bit anal) it does not seem beneficial to install the server kernal.

Thanks Again!

---

### Post by albinootje on 2009-01-09
> **grossinm said:**
>  My biggest question from the post, was to look at the processes that are running, to ensure there weren't any unnecessary items running.  It sounds like there are not any.


Try instead of top this :
```

ps auwx

```
And if you are bored, try this :
```

watch -n1 ps S

```
:D

Or install htop
```

sudo apt-get install htop

```
and press F5 for a tree structure.

---

### Post by grossinm on 2009-01-09
Excellent, new toys!

Any advice on backing up?  I have mounted my Time Capsule drive, and want to back it up to my server once a week or so.

I'm looking at rsync now, but it looks a little daunting....

---

### Post by albinootje on 2009-01-09
> **grossinm said:**
> Excellent, new toys!

Any advice on backing up?  I have mounted my Time Capsule drive, and want to back it up to my server once a week or so.

I'm looking at rsync now, but it looks a little daunting....

I don't know about Time Capsules, but see here :
[http://tumblelog.slobodankovacevic.com/post/44456827/mount-time-capsule-in-ubuntu](http://tumblelog.slobodankovacevic.com/post/44456827/mount-time-capsule-in-ubuntu)
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

And about rsync, if you just want an up to date backup, then doing something like this is e.g. enough :

Example backup to usb disk :
```

sudo rsync -avzu /home/ /media/usb-disk-1/

```

Example making a backup from a remote machine :
```

sudo rsync -auvzC yourdomain.org:/var/www/ /usr/local/backups/www/

```

Example using rdiff-backup to make incremental backups from a remote machine :
```

sudo rdiff-backup yourdomain.org::/var/www/ /usr/local/backups/incremental-www/

```

See also this manual for example to run nightly backups :
```

man 5 crontab

```

---

### Post by grossinm on 2009-01-09
Here is the current status:

I have Kubuntu 8.04 running in shell only.  
The local USB drive (which will be the destination folder) is attached via UUID mount to /media (and there is a Samba shared folder inside of it called Wolverine, but I'm guessing that is not important).

The time capsule is mounted on the local system at /media/Capsule (done via FSTAB line //192.168.1.1/GMTC /media/Capsule cifs password=password,rw,iocharset=utf8,file_mode=0777,dir_mode=0777).  so this basically shows up as a local drive on the Kubuntu system.

So, I want to use rsync to copy the files from /media/Capsule/* to /media

The only requirements I have are that the backups be performed on a scheduled basis, and that the backups are incremental.

From my reading, it sounds like I need to edit the /etc/rsyncd.conf file and then create something called a cron file (no idea what this is.. other than a way of scheduling executions of jobs....)

That's where I'm at.

So, in your example, if I was to run rsync from the command line:

sudo rsync -avzu /media/Capsule/ /media/Backup

I would need to create the Backup folder (sudo mkdir ../media/Backup), and -avzu means archive, verbose, compress, skip files that are newer (or equal to?) on the reciever.  

My questions:  

compress, does this slow down or speed up the transfer?  I am on a direct line from Kubuntu machine to Time Capsule (it is a router and hub as well as storage device)?

archive:  Not sure what this means in this context?

Verbose, hopefully, when this is a scheduled job, it will report errors to a log file?

and -u, does this create an incremental backup?

Thanks (sorry for the long post)!

reading cron manual now!

---

### Post by albinootje on 2009-01-09
> **grossinm said:**
> 
sudo rsync -avzu /media/Capsule/ /media/Backup

You want incremental backups, so let's try rdiff-backup instead of rsync.

For using cronjobs I prefer to make a shell-script first, and add that to crontab.

Here's an example script called /usr/local/bin/backup.sh
(cron runs as root by default, no sudo needed) :

```

# example shell script /usr/local/bin/backup.sh
mkdir -p /usr/local/backup/
time rdiff-backup /media/Capsule/ /usr/local/backup/
chmod 750 /usr/local/backup/

```

Let's now add the cronjob for it :
```

sudo chmod 750 /usr/local/bin/backup.sh
export EDITOR=nano
sudo crontab -e

```
Add a line like this :
```

30 1 * * * /usr/local/bin/backup.sh

```
Save the file.
This should start the backup half past 1 at night.

> 
Verbose, hopefully, when this is a scheduled job, it will report errors to a log file?

By default cron will send you certain output by email, provided that you've set up a local mailserver (can be a very simple mailserver setup).

---

### Post by grossinm on 2009-01-09
I'm guessing that ensuring an accurate time on the system is important.  What is the best way to keep the system time current?

---

### Post by albinootje on 2009-01-09
> **grossinm said:**
> I'm guessing that ensuring an accurate time on the system is important.  What is the best way to keep the system time current?

There's ntpdate and rdate. 
Two little tools to set the time via the internet.

[http://www.debianadmin.com/keeping-your-system-clock-current-automatically-via-network-time-protocol-ntp.html#more-248](http://www.debianadmin.com/keeping-your-system-clock-current-automatically-via-network-time-protocol-ntp.html#more-248)

---

### Post by grossinm on 2009-01-10
Ok, so the backup ran last night (and is still running 400+ gb).

Let me ask a few questions:  How do I exclude certain kinds of files from the backup?  

How does RDiff handle files that are in use during the backup?

I will try the time server applications after the backup completes.

Thanks

---

### Post by albinootje on 2009-01-10
> **grossinm said:**
>  Let me ask a few questions:  How do I exclude certain kinds of files from the backup?  

Glance this through :
[http://www.nongnu.org/rdiff-backup/rdiff-backup.1.html](http://www.nongnu.org/rdiff-backup/rdiff-backup.1.html)
[http://www.nongnu.org/rdiff-backup/FAQ.html](http://www.nongnu.org/rdiff-backup/FAQ.html)

You can exclude device files and sockets, but that's perhaps not what you meant.

If you have a lot of sub directories, then you can use rdiff-backup per directory, and having multiple destination directories, and with that, leave out the ones you don't want to backup.

> 
How does RDiff handle files that are in use during the backup?

Not sure about that.

I recommend that you test restoring *some* files after the backup is complete, to make yourself familiar with rdiff-backup.

If you decide that you rather have a GUI based backup solution that can do incremental backups, then it's time to start a new thread.

For my uncle's laptop I've tested a few GUI backup solutions, and I found them either to feature-rich, or too simple, or too confusing.
But you might like them.
Again, make sure you test restoring (part of the) backups, with whatever backup software you decide to use.

---

### Post by grossinm on 2009-01-10
I was under the impression that RDiff was making 1:1 copies of the files?  Or are we compressing them into a TAR/GZ?

---

### Post by albinootje on 2009-01-10
> **grossinm said:**
> I was under the impression that RDiff was making 1:1 copies of the files?  Or are we compressing them into a TAR/GZ?

Not 1:1 
rdiff-backup uses a different approach. 

I'm using rdiff-backup since years for backups at work. 
Whenever I need to restore something I need to read the manual again.
It's not a matter of just browsing through files and find the file you need.
You will need the restore option.

If you prefer making incremental backups with rsync instead, it's possible.. but only with scripts.
There are several webpages and projects which provide those.
In that case you'll have the 1:1 copies, in different directories with data+timestamp in the name of the directories.

---

### Post by grossinm on 2009-01-15
So I am finally getting back to customizing the script.  

Can I enter a line into the backup.sh file for each location I want to backup to and its destination?

Here is the script as I have it now:

# example shell script /usr/local/bin/backup.sh
mkdir -p /media/Media/Backup/ITunes
mkdir -p /media/Media/Backup/Cabrera
mkdir -p /media/Media/Backup/Videos

time rdiff-backup /media/Capsule/ITunes /media/Media/Backup/ITunes
time rdiff-backup /media/Capsule/Cabrera /media/Media/Backup/Cabrera
time rdiff-backup /media/Capsule/Videos /media/Media/Backup/Videos

chmod 750 /media/Media/Backup/ITunes
chmod 750 /media/Media/Backup/Cabrera
chmod 750 /media/Media/Backup/Videos

Should consolidate each backup job?  Are there mulitple steps here that can be combined?

---

### Post by albinootje on 2009-01-15
> **grossinm said:**
>  Here is the script as I have it now:

# example shell script /usr/local/bin/backup.sh
mkdir -p /media/Media/Backup/ITunes
mkdir -p /media/Media/Backup/Cabrera
mkdir -p /media/Media/Backup/Videos

time rdiff-backup /media/Capsule/ITunes /media/Media/Backup/ITunes
time rdiff-backup /media/Capsule/Cabrera /media/Media/Backup/Cabrera
time rdiff-backup /media/Capsule/Videos /media/Media/Backup/Videos

chmod 750 /media/Media/Backup/ITunes
chmod 750 /media/Media/Backup/Cabrera
chmod 750 /media/Media/Backup/Videos



Looks good! Why don't you test it (including a restore test) ? :)

Instead of the last three lines this could be enough :
```

chmod 750 /media/Media/Backup/

```

---

