---
title: "Professional Backup Software"
date: 2009-04-15
forum: Server Platforms
---

### Post by Harry Muscle on 2009-04-15
I'm looking for suggestions for some professional (and hopefully not ridiculously expensive) backup software.  Currently I'm running a Windows 2007 Server and am using Acronis True Image Echo Server to perform my backups.  I don't need all the features it provides, but here's what I'm looking for:

- ability to restore files from past dates (ie: if the file was backed up on January 22 and then it changed and was backed up on February 1, I want the ability to restore either version of the file)
- ability to schedule incremental backups
- backups stored in some sort of compressed format
- easy to use graphical interface, preferably web based
- most other features are extras that are nice but not required

I'm fairly new to Ubuntu and so far I haven't been able to find a backup application that would do these things.  The main things I'm having a hard time finding is the easy to use GUI and the restoring of files from multiple dates.  Most of the backup software I've found simply replicated data from one location to another.  I'm hoping for something a bit more than that.

If anyone can offer some suggestions, etc. that would be highly appreciated.

Thanks,
Harry

P.S.  These backups will be done from one hard drive to another hard drive.

---

### Post by Titan8990 on 2009-04-15
Acronis makes a Linux version although all the features you need are already available in command line tools such as rsync. You should weigh the price of a $500 backup application against a few hours it could take to learn rsync and write a script to implement your needs. 


Also, in general, "I need a program that can do said function." is a Windows mindset of administration. A UNIX way of thinking is "I need to write a script that can do said function." Not from a desktop user perspective but from the perspective of a UNIX administrator. Why pay $100s for a pretty interface for a script that you could have wrote in < a hour?


You will find many tutorials and pre-written scripts for rsync here on the forums. Good luck.

---

### Post by ktrnka on 2009-04-15
Backuppc is my absolute favorite. [http://backuppc.sourceforge.net/]("http://backuppc.sourceforge.net/") It is extremely reliable and makes restoring files a breeze! It's open source, free and not too difficult to setup. It is a wonderful program.

---

### Post by jowilkin on 2009-04-15
Popular (free) backup programs on Linux are Amanda ([http://www.amanda.org/](http://www.amanda.org/)), Bacula ([http://www.bacula.org/en/](http://www.bacula.org/en/)), and rsnapshot ([http://rsnapshot.org/](http://rsnapshot.org/)).

I think rsnapshot is the easiest to use but least powerful.  Bacula is more powerful and still not to hard to use.  Amanda is also powerful and I found it to be the hardest to set up.

---

### Post by hictio on 2009-04-15
I use rsnapshot on every single server I put my hands on.
It is amazingly easy to install and to setup, it takes, literally, minutes.

And, it might be crude, as jowilkin says, but it is really powerful to combine onto multiple backups, the crude part might be if you want your users to have a GUI or webfront to pull their own backlogs from a backup server.

---

### Post by Harry Muscle on 2009-04-15
Thank you for all the suggestions so far, I'm looking into them as I type this, however, it seems I will have to add another requirement to my list, something that I took for granted, but it seems neither BackupPC or RSnapShot support (the two that I've looked in depth at).

- the ability to backup to different locations

For example, I would like the ability to backup all the data from a certain location to hard disk A but all the data from another location to hard disk B of the server.  I know I could use some sort of RAID to make all the disks in the server act like one location and therefore not require backups to different locations, but the server disks are all different sizes so a RAID solution wouldn't work too well and I don't want to use JBOD cause if I lose one drive I don't wanna loose all my backups, just the backups stored on the drive that dies.

Thanks again for all the suggestions so far,
Harry

---

### Post by Mister.Vash on 2009-04-16
Have you looked at bacula? [http://www.bacula.org/en/](http://www.bacula.org/en/)

I didn't notice anything that you listed as wanting to do that bacula doesn't do - it even has a gui front end [http://wiki.bacula.org/doku.php?id=bat_new](http://wiki.bacula.org/doku.php?id=bat_new)

I'm using it to back up a few different machines running different operating systems, and breaking them out in to different data sets.  If it does look like something you might try, I would recommend reading their manuals first, and they also used to have some example walkthroughs that were helpfull

---

### Post by ktrnka on 2009-04-16
What you should use is Backuppc and setup a linux lvm (Logical Volume Manager). It pools all your data together and allows you the ability to dynamically shrink and expand your data pool. You should heavily investigate using an LVM. That also allows you to eject a drive from the pool, remove it, and add a larger one down the road without having to move the data off the lvm to another location and create a new lvm. It's perfect for what you are asking.   

Here's a how to:
[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

Here's some more information:

[http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html")

---

### Post by Harry Muscle on 2009-04-16
> **ktrnka said:**
> What you should use is Backuppc and setup a linux lvm (Logical Volume Manager). It pools all your data together and allows you the ability to dynamically shrink and expand your data pool. You should heavily investigate using an LVM. That also allows you to eject a drive from the pool, remove it, and add a larger one down the road without having to move the data off the lvm to another location and create a new lvm. It's perfect for what you are asking.   

Here's a how to:
[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

Here's some more information:

[http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html")

Thanks for those links, I'm gonna start reading them today.  One quick question for you though (since I've done some high level looks into LVM).  If one of the hard drives that's part of a Logical Volume were to die, would I loose the whole volume?  This is assuming no RAID is being used.  Cause my assumption is yes I would loose the whole volume, which is the reason why I've been trying to stay away from using LVM.  If one of my hard drives goes dead, I'd really prefer to only loose the data backed up onto that drive and not all the backups that span several drives (if the whole logical volume goes dead based on one hard disk dying).

Thanks,
Harry

---

### Post by Harry Muscle on 2009-04-16
Just a quick follow up on my current decision process :)

So far I'm liking rsnapshot (for it's simplicity) and BackupPC (for it's Web GUI) the most from all the options presented.  The two biggest drawbacks as already mentioned is their inability to backup to multiple locations.  So what I was thinking of doing is running multiple instances of the backup software.  I'm not sure if it would be possible to do so on a single machine, but I could have several virtual machine inside VMWare Server running.  Each one configured to backup a certain location to a certain server hard drive.  Somewhat of a waste of RAM on the server, but it doesn't do much else.  Now, I'm just curious to know what the bare minimum RAM requirements would be for RSnapshot and/or BackupPC.  Any guesses?  Btw, I would be using a stripped down "server" install on the virtual image, so let's assume the OS inside the virtual machine would take 64MB of RAM.

Thanks,
Harry

---

### Post by hictio on 2009-04-16
I'm sorry, what do you mean by "multiple locations", or "to multiple locations"?
Not sure if this what you are after, but, what I usually do with my rsnapshot setups is that I made a local one on the given server, and then issue a script that simply rsyncs the most resent (r)snapshot to another server.

Something like this:

```

#!/bin/sh

WORK_DIR="/var/backups/hourly.0/my.server.01/"
REMOTE_DIR="/home/some.username/backups/xxxx/XXXX/my.server.01/"
RSYNC='/usr/bin/rsync -e ssh -avzr --delete --bwlimit=10'
USER="some.username"
HOST="my.backup.server"
LOGFILE="/tmp/_rsync.my.server.01.log"
DEST="someemailaddress@somedomain"

/bin/echo `/bin/date`: Start rsync -my.server.01- > ${LOGFILE}

cd ${WORK_DIR}

${RSYNC} * ${USER}@${HOST}:${REMOTE_DIR} >> ${LOGFILE}

/bin/echo `/bin/date`: Finish rsync >> ${LOGFILE}
/bin/cat ${LOGFILE} | /bin/mail -s "Rsync my.server.01" ${DEST}

# EoF #

```

Coming from 'my.server.01' , the user "some.username" can login to "my.backup.server" via public key, and that's it.
Depending on the ammount of data, I usually comment the '/bin/cat ${LOGFILE} | mail -s "Rsync my.server.01" ${DEST}' line so I don't a multi MB email the first time I execute the script; but for the subsequent runs, at least on my case, the changes are not that huge, so I can get an email reporting what happens between snapshots.

Needless to say, on "my.backup.server" you can have another instance of rsnapshot installed, making snapshots of the "/home/some.username/backups/xxxx/XXXX/my.server.01/" directory, so you can have backlogs as well, just in case.

---

### Post by wirelessmonkey on 2009-04-17
I absolutely agree with backuppc... I use it to back up 10 linux servers, 22 Windows 2k3 servers, and a dozen or so laptops.  Never had any problems, and it has a robust and friendly community.

---

### Post by Harry Muscle on 2009-04-17
> **hictio said:**
> I'm sorry, what do you mean by "multiple locations", or "to multiple locations"?


For example, let's say I want to backup Directory1 and Directory2, however, I want to have the backup of Directory1 located on ServerDisk1 and the backup of Directory2 located on ServerDisk2.  That's what I mean when I mentioned multiple locations.  From what I gather though, RSnapShot and BackupPC get configured to backup things to only one location (ie: ServerDisk1 for example).  There's no way to tell it to backup certain things to another location.

Hope that clarifies things.

As a side note though, I might have found something similar to RSnapShot that does allow backing up to multiple locations and it even has a Web GUI available for it.  RDiff-Backup and RDiffWeb.  So I'm gonna do a bit of research on those two.

Thanks,
Harry

---

### Post by ktrnka on 2009-04-17
Rdiff is ridiculously slow. Believe me.... I tried it several months ago ( trying to move 2TB of data) and its transfer rates were absolutely unacceptable. I use backuppc to backup 75 different systems and it has been the most reliable system I have used. I'll get to your other questions later tonight.

---

### Post by ktrnka on 2009-04-17
Harry, if you want to stay away from RAID and LVM, you can easily just make symlinks to any location you wish. The hostnames are created by default in /var/lib/backuppc so if I have a computer called COMPUTER1 and I have a different Harddrive that is mounted on bootup @ /Backup I can create a symlink from /var/lib/backuppc/pc/COMPUTER1 >>>>>>> That points to /Backup



All that needs to be done is make sure that user backuppc has write access to /Backup. Backuppc will still think it's writing to /var/lib/backuppc/pc/COMPUTER1 but it's actually @ another location. It's that simple!


(Let me know if you don't quite understand what I mean)

Good Luck!


To create a symlink:
```
ln -s <destination> <symlink name>
```

Little info on symlinks:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?ln]("http://unixhelp.ed.ac.uk/CGI/man-cgi?ln")

[http://ubuntuforums.org/showthread.php?t=73096]("http://ubuntuforums.org/showthread.php?t=73096")

---

### Post by mangaman on 2009-04-20
Try this tutorial [http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)  .

It was written in '07 but it should help you setup as server if you haven't already.

---

### Post by Harry Muscle on 2009-04-23
> **ktrnka said:**
> Harry, if you want to stay away from RAID and LVM, you can easily just make symlinks to any location you wish. The hostnames are created by default in /var/lib/backuppc so if I have a computer called COMPUTER1 and I have a different Harddrive that is mounted on bootup @ /Backup I can create a symlink from /var/lib/backuppc/pc/COMPUTER1 >>>>>>> That points to /Backup



All that needs to be done is make sure that user backuppc has write access to /Backup. Backuppc will still think it's writing to /var/lib/backuppc/pc/COMPUTER1 but it's actually @ another location. It's that simple!


(Let me know if you don't quite understand what I mean)

Good Luck!


To create a symlink:
```
ln -s <destination> <symlink name>
```

Little info on symlinks:

[http://unixhelp.ed.ac.uk/CGI/man-cgi?ln]("http://unixhelp.ed.ac.uk/CGI/man-cgi?ln")

[http://ubuntuforums.org/showthread.php?t=73096]("http://ubuntuforums.org/showthread.php?t=73096")

Thanks for the answer, but I'm guessing I didn't explain things well enough.  It's not that I'm trying to point to another location.  I would like to point to two locations (at the same time).  So the software would backup DATA1 to LOCATION1 and DATA2 to LOCATION2.  I guess you could technically change the symlink between backups, but I think that would get quite messy and most likely confuse the software if it runs as a daemon.

Thanks,
Harry

---

### Post by ktrnka on 2009-04-23
I guess I still don't fully understand. You want to backup different directories from the SAME machine to different locations? If that's the case then you can configure Backuppc to use 2 hostnames for your one computer and specify one to backup directory one and the other to backup directory 2. Then you will see 2 different hosts under /var/lib/backuppc/pc/ called host1 and host2. You can then symlink host1 (that is backing up Directory1) to a separate drive and do the same for host2(that is backing up Directory 2). 

Another Way of putting it: 1 Computer sharing 2 directories, 1 backuppc server running with 2 other hard drives.

backuppc configured for 2 hostnames. One can be the hostname and the other, it's IP address. Configure the first to backup directory 1. Configure the second to backup directory 2. both the SERVER'S Name and IP address will be in /var/lib/backuppc/pc directory and appear as 2 separate hosts. Those can then be independently symlinked to other locations. 

Am I getting anywhere close to what you are asking?

---

### Post by Harry Muscle on 2009-04-24
> **ktrnka said:**
> I guess I still don't fully understand. You want to backup different directories from the SAME machine to different locations? If that's the case then you can configure Backuppc to use 2 hostnames for your one computer and specify one to backup directory one and the other to backup directory 2. Then you will see 2 different hosts under /var/lib/backuppc/pc/ called host1 and host2. You can then symlink host1 (that is backing up Directory1) to a separate drive and do the same for host2(that is backing up Directory 2). 

Another Way of putting it: 1 Computer sharing 2 directories, 1 backuppc server running with 2 other hard drives.

backuppc configured for 2 hostnames. One can be the hostname and the other, it's IP address. Configure the first to backup directory 1. Configure the second to backup directory 2. both the SERVER'S Name and IP address will be in /var/lib/backuppc/pc directory and appear as 2 separate hosts. Those can then be independently symlinked to other locations. 

Am I getting anywhere close to what you are asking?

Yup, that's what I'm trying to do.  However, I'm not sure if your suggestion would work, cause according to the BackupPC documentation one cannot use symbolic links to split up the "data store".  Here's the part I'm referring to:

BackupPC uses hardlinks to pool files common to different backups. Therefore BackupPC's data store (__TOPDIR__) must point to a single file system that supports hardlinks. You cannot split this file system with multiple mount points or using symbolic links to point a sub-directory to a different file system (it is ok to use a single symbolic link at the top-level directory (__TOPDIR__) to point the entire data store somewhere else).

Thanks,
Harry

P.S.  In my case the second location is on a second drive, so it would be on a different file system.

---

### Post by ktrnka on 2009-04-24
Hmm, well I guess I was mistaken. But you should still consider a Linux Soft-Raid and LVM. It's the best combination. Hope you find the solution that works best for you!

---

### Post by ktrnka on 2009-04-24
I just came across something interesting that might interest you (specifically for your situation with different sized drives). 

It uses FUSE and is called mddfs

[http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/]("http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/")

I think this would be perfect for your situation.

---

