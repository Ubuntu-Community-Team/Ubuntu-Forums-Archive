---
title: "System backups"
date: 2010-08-19
forum: System76 Support
---

### Post by bk7777` on 2010-08-19
Looking for how you all back up your systems.
 
What I am looking for is some way to make a gold image backup.
 
Is there something that would backup the current configuration to say to a CD or DVD and in the event of a crash do something like the following:
 
Install the system with base install media and get all updates.
Then put in a CD or DVD and have it get restore all the settings as they were and get the missing packages.
 
Another options would be:  How about a "Bare Metal Restore" (BMR) package?
 
How do you all back up?
 
I am open to your suggestions.  Please be as detailed as you can.
 
Thanks,
Brian

---

### Post by jml on 2010-08-19
Here is a link to a resource I found on this web site.  Hope it is of help to you.  

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Joe

---

### Post by Eldera on 2010-08-19
Up Front: I am very inexperienced, I have been using Ubuntu for only a year and a half; previous experience about 7 years using XP for word processing and the net. Recently I decided to learn more about back-ups and made up a preliminary list of links to go back and study in depth. 

You are welcome to it.

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

Clonezilla
[http://www.clonezilla.org/](http://www.clonezilla.org/) 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

Tar Files
[http://www.linux.org/lessons/beginner/l15/lesson15a.html](http://www.linux.org/lessons/beginner/l15/lesson15a.html)
[http://ubuntuforums.org/showthread.php?t=1399107](http://ubuntuforums.org/showthread.php?t=1399107) 

remastersys
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Names to Google: rsync, Back in Time

I have been backing up my data by copying and pasting to a set of USB sticks. If my settings got messed up, I just did a clean install of everything and let all the  setting files go to the defaults. You can laugh, but that's what I could handle at this point of the learning curve. 

I started my in depth study of backups with Clonezilla. Just this morning I made a perfect clone of my Panp4 to a Toshiba 320 GB external hard drive. I am making progress.

i am sure some of the software in my lists will do what you want. I just haven't worked with the lists enough to know which one.Sorry.

---

### Post by gamerchick02 on 2010-08-20
> **bk7777` said:**
> Looking for how you all back up your systems.
 
What I am looking for is some way to make a gold image backup.
 
Is there something that would backup the current configuration to say to a CD or DVD and in the event of a crash do something like the following:
 
Install the system with base install media and get all updates.
Then put in a CD or DVD and have it get restore all the settings as they were and get the missing packages.
 
Another options would be:  How about a "Bare Metal Restore" (BMR) package?
 
How do you all back up?
 
I am open to your suggestions.  Please be as detailed as you can.
 
Thanks,
Brian

I use a 250 gb external drive and BackInTime.  I run a snapshot weekly.  I don't have a ton of data, but I might have to increase my external capacity (to at least 500 gb) since I'm going to be upgrading my hard drive soon.

I'm super simple with backups. *shrug*  Oh, I just do my backup of the /home.  If I need to restore, I'll usually write down my minimum "needs" for programs on a piece of paper.  Like I said; super simple...  :)

Amy

---

### Post by greghk on 2010-08-20
I don't care too much about my system data because that can be recreated. I only do an aptitude search '~i' and pipe the results to a file on the backup external hard drive in the hope this would help if I had to recover the system. Haven't had to yet so no idea if this works. It would be nice to be able to quickly recover all my configuration changes to Linux but I haven't figured out how to do this.

My primary concern is my userdata. I back this up to an external hard drive with cp commands. I'm a bit reluctant to compress it or do delta backups as I think there is more chance of something going wrong at recovery time and I only have 1 - 2GB of user data.

Greg

---

### Post by PabloH on 2010-08-22
Here is what I do for backups:

1. I use git for versioning control. Git is the way to keep multiple versions of files around. I don't think backup tools should handle versioning of files, nor should they handle recovering accidentally deleted files. Both are better handled by an advanced snapshotting filesystem or with a proper tool like git.

2. To handle disaster recovery, I use rsync to backup data to encrypted usbdisks. Before I run rsync on a machine, I have the shell script do the following:

[LIST]
[*]Backup my MySQL database to a bzipped file under my home directory. This is done using mysqldump piped to bzip2.
[*]Write out a list of all installed packages to a text file under my home directory. This is done using dpkg.
[/LIST] 

I then rsync my home/username/, /etc, and /var/www/ directories to the encrypted usbdisk. The files on the usbdisk are saved in subdirectories matching the original, i.e.:

[LIST]
[*]/backups/hostnameofcomputer/home/username/*
[*]/backups/hostnameofcomputer/etc/*
[*]/backups/hostnameofcomputer/var/www/*
[/LIST]

For each computer I have, I will have a subdirectory under the "backups" directory on the usb disk that matches the hostname. 

That covers files I keep on the computers main disks. Then there are files that I share between computers, but don't have on any particular computer's hard disk. These are files like photos and media files. These are also archive data like old email. Furthermore, this includes sensitive documents. I don't keep sensitive documents on my computer's main disks as the hard drives installed in the computers are not encrypted.

For all of these files, I am currently keeping them on the same usbdisk as my backups. Eventually, they will live on a RAID file server (with sensitive stuff on an encrypted partition) that is accessible on the net. Until then, this disk goes everywhere my laptop goes.

For now, these files live on the usbdisk in a directory called /shared/*. These are not backups, but are the main copies.

3. After rsyncing all my machines to the main usbdisk, I still have to backup the shared data. I do this by rsync'ing the entire usbdisk to another encrypted usbdisk that I use as a mirror. I do this monthly. I keep the mirror in a static waterproof bag offsite (like a friends house or a safety deposit box).

Rsync is pretty quick if you do it every few days or so. The only downsides are that lots of disk space is required for backups, and the rsync process is not instantaneous like it is with an enterprise NAS system with a built-in snapshotting filesystem. 

I am exploring a way to solve the first issue (compression) by using a FUSECompress filesystem. This filesystem compresses the data going to the backup directories on the fly. I will just mount it on top of the ext based filesystem (which is mounted on top of LUCS). It will then compress and decompress files transparently on the fly, so I can continue using the files as normal-- i.e. using rsync to keep them synced.

The second downside (proper versioning integration) can only be solved with better designed file systems.

---

