---
title: "Server RAID Advice"
date: 2014-01-28
forum: Server Platforms
---

### Post by Harp on 2014-01-28
I wasn't sure of the appropriate category for this. Move it if you like.

--

I have a 2-bay HD enclosure that currently contains two identical drives, each formatted in NTFS. I have been using the two drives independently but now I'm thinking I would like to set them up in a RAID 1 in order to prevent data loss.

My main problem, as I understand it (and correct me if I'm wrong), is that the RAID will be OS-specific. Meaning, like, if I set up the RAID in OSX it won't hold for Linux or Windows. This is a problem for me because I often boot into different operating systems and I need the RAID to maintain its structure across all of them.

Perhaps my saving grace here is that I will predominantly be accessing the RAID via my home network. So, my idea is that I can take this old netbook I have and install on it a Linux server distro, set up a software RAID on the drives to be operable via Linux (mdadm), and then access the RAID through this server on my network. 

Like this: [http://postimg.org/image/negr7y2ux/](http://postimg.org/image/negr7y2ux/)

If I ever need to directly plug the drive into my computer (which doesn't happen often), I can boot into Linux without much effort. And if I ever need to share the drive with computers outside of my network, ftp should suffice (it's too big to lug around anyway).

One possible problem might be that my old netbook does not have USB 3.0 capability and the drive enclosure does, which would create a bottleck of, what, 480 Mbps at the server? Would a better option be to build an NAS with USB 3.0 capabilities running FreeNAS and connect the RAID that way?

Or is there a way I can set up a software RAID to work across OSes? That doesn't sound very stable. Maybe I should just give up and make manual backups.

---

### Post by TheFu on 2014-01-28
RAID is for high availability.  Backups are for everything else.  Backups are 1000x more important than RAID, especially at home.

Building a NAS is a good idea. 

Using USB2/USB3 for a RAID is a bad idea. RAID needs SATA/eSATA connectivity.
USB3 is fine for NAS use, provided only a few processes are using the HDDs concurrently. Many people have seen queuing issues with USB3 devices under Linux.  In my situation, when the 3rd or 4th process makes a request (read or write), access to the HDD appears to lock up for about 20-30 seconds - nothing gets transferred.

USB2 claims 480Mbps - never seen that.  The fastest USB2 transfers I've ever seen is about 240Mbps for spinning disks. Don't forget about the network bottleneck too. Are your systems GigE connected?  If not, then don't expect much over 11MB/s transfers. For a server, that just sucks.

When setting up RAID, don't expect to move the RAID devices between systems easily.  Sure, you can physically move the RAID array to a new server, but that is not something to be done more than once a year at most, IMHO. I've done it a few times. [http://blog.jdpfu.com/2010/02/12/software-raid-migration](http://blog.jdpfu.com/2010/02/12/software-raid-migration) - with software RAID, it is not too bad.

So, based on what you are saying, I'd strongly recommend **setting up backups between the two HDDs**. If you have split the media (audio/video) from everything else, then use rsync to _mirror_ those files and use a real, versioned, backup tool for the other files.  A mirrored, yet corrupted, document, isn't really very useful. However, if you have 30 days of backups, then the different versions of the file over that time will be available and you'll be able to get a non-corrupted version back.

---

### Post by CharlesA on 2014-01-28
> **Harp said:**
> 
I have a 2-bay HD enclosure that currently contains two identical drives, each formatted in NTFS. I have been using the two drives independently but now I'm thinking I would like to set them up in a RAID 1 in order to prevent data loss.

RAID isn't a way to prevent data loss, it is a way to prevent downtime. Even if you have a RAID, you still need to be doing (and testing) backups.

> My main problem, as I understand it (and correct me if I'm wrong), is that the RAID will be OS-specific. Meaning, like, if I set up the RAID in OSX it won't hold for Linux or Windows. This is a problem for me because I often boot into different operating systems and I need the RAID to maintain its structure across all of them.

That is usually true. I have my NAS set up on a hardware controller (LSI 9260-8i) with 5 x 3TB WD SE drives running RAID 6. For a two drive NAS, I would go with RAID1, but also keep backups of the data on the drives.

My setup at home is currently set so everything on the array (minus the VMs and my movie library) is synced to an external hard drive daily with incremental backups using hard links for "version control." I also have the entire array (mins VMs) set to sync offsite with CrashPlan.

> Perhaps my saving grace here is that I will predominantly be accessing the RAID via my home network. So, my idea is that I can take this old netbook I have and install on it a Linux server distro, set up a software RAID on the drives to be operable via Linux (mdadm), and then access the RAID through this server on my network. 

If you have a dedicated server, you should be fine.

> If I ever need to directly plug the drive into my computer (which doesn't happen often), I can boot into Linux without much effort. And if I ever need to share the drive with computers outside of my network, ftp should suffice (it's too big to lug around anyway).

If you really need outside access, you could run something like ownCloud or just using SFTP. I use SFTP at home and ownCloud on one of my VPSes.

> One possible problem might be that my old netbook does not have USB 3.0 capability and the drive enclosure does, which would create a bottleck of, what, 480 Mbps at the server? Would a better option be to build an NAS with USB 3.0 capabilities running FreeNAS and connect the RAID that way?

It will bottleneck with USB2 just like TheFu said. I use internal SATA drives on my server, but at work, they are using a 4 bay Buffalo NAS box connected via USB3.

> Or is there a way I can set up a software RAID to work across OSes? That doesn't sound very stable. Maybe I should just give up and make manual backups.

Backup, backup, backup.

> **TheFu said:**
> USB2 claims 480Mbps - never seen that.  The fastest USB2 transfers I've ever seen is about 240Mbps for spinning disks. Don't forget about the network bottleneck too. Are your systems GigE connected?  If not, then don't expect much over 11MB/s transfers. For a server, that just sucks.

+1. I've been running Gigabit for a long time now but I remember how long it took to transfer files when I was still running 10/100 and serving stuff off USB2 drive on an XP box. :lolflag:

> When setting up RAID, don't expect to move the RAID devices between systems easily.  Sure, you can physically move the RAID array to a new server, but that is not something to be done more than once a year at most, IMHO. I've done it a few times. [http://blog.jdpfu.com/2010/02/12/software-raid-migration](http://blog.jdpfu.com/2010/02/12/software-raid-migration) - with software RAID, it is not too bad.

This is more for hardware cards than mdadm, but it is totally true. I had to rebuild my array from scratch after migrating it to a new card (with the old drives), which is why backups are very, very important. So far I haven't had the need to migrate the array I have running via mdadm on my backup server, but it should be easy enough since the configuration should be stored in the superblocks of each drive.

> So, based on what you are saying, I'd strongly recommend **setting up backups between the two HDDs**. If you have split the media (audio/video) from everything else, then use rsync to _mirror_ those files and use a real, versioned, backup tool for the other files.  A mirrored, yet corrupted, document, isn't really very useful. However, if you have 30 days of backups, then the different versions of the file over that time will be available and you'll be able to get a non-corrupted version back.

Huge +1. Set setup isn't true version control like git or svn, but it works for me. With the currently setup, it would be a good idea to use one drive for storage and the other for backups.

Otherwise you would be looking into getting a whole new machine just for the NAS.

---

### Post by Harp on 2014-01-28
> **TheFu said:**
> Don't forget about the network bottleneck too. Are your systems GigE connected?  If not, then don't expect much over 11MB/s transfers. For a server, that just sucks.

Well, the drives themselves are each 3.5" connected by USB 3, which should yield a transfer rate of, let's say, 100MB/s. The wireless router I have is 802.11ac with a USB 3 port. 802.11ac should yield realistic transfer speeds of about 250MB/s, so if I connected the drives directly to the router there shouldn't be much of a bottleneck to worry about there. I could live with 100MB/s.

The netbook server with USB 2, however, would slow this down considerably. 

> **CharlesA said:**
> RAID isn't a way to prevent data loss, it is a way to prevent downtime. Even if you have a RAID, you still need to be doing (and testing) backups.

My main concern here is drive failure, a nightmare that I [recently experienced]("http://ubuntuforums.org/showthread.php?t=2201948") and am still cleaning up after. Backups, essentially, achieve the same goal. I was just thinking of RAID 1 as a way to streamline the process, to keep 2 drives in sync in the event of failure rather than to resort to scheduling backups and then restoring backups that may be a few days old. Not a big problem vs. complete data loss, I was just trying to better automate the process. 

There comes a certain point, though, when creating convenience becomes very inconvenient. The limitations of software RAID, it seems, would be more of a hindrance to my system than a help. Somewhere in the not-too-distant future, I will probably build a NAS for these drives. In the mean time, I think I will just resort to scheduling backups of one drive to its twin.

> **TheFu said:**
> So, based on what you are saying, I'd strongly recommend setting up backups between the two HDDs. If you have split the media (audio/video) from everything else, then use rsync to _mirror_ those files and use a real, versioned, backup tool for the other files. A mirrored, yet corrupted, document, isn't really very useful. However, if you have 30 days of backups, then the different versions of the file over that time will be available and you'll be able to get a non-corrupted version back. 

I'm looking at either [LuckyBackup]("http://luckybackup.sourceforge.net/index.html") or [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/index.html") to handle rsync. Both have versions for OSX/Win/Linux. Does rsync work well from one network drive to another? I assume it wouldn't be much of a problem if they are both mounted to local folders (ie, /media/drivex). I'm not TOO worried about having versioned backups of documents (though I say that with a grimace). I have a good habit of using the "save as" button incrementally to create my own versions in the event of file corruption. That being said, I would consider a versioned backup tool if you have any suggestions.

Thanks for all the help. I really appreciate it!

---

### Post by CharlesA on 2014-01-28
> **Harp said:**
> Well, the drives themselves are each 3.5" connected by USB 3, which should yield a transfer rate of, let's say, 100MB/s. The wireless router I have is 802.11ac with a USB 3 port. 802.11ac should yield realistic transfer speeds of about 250MB/s, so if I connected the drives directly to the router there shouldn't be much of a bottleneck to worry about there. I could live with 100MB/s.

The netbook server with USB 2, however, would slow this down considerably. 

I haven't tried that, even though my (new) router has USB 2 ports on it. I suspect you would still bottleneck at the drive itself, even at USB3 speeds.



> My main concern here is drive failure, a nightmare that I [recently experienced]("http://ubuntuforums.org/showthread.php?t=2201948") and am still cleaning up after. Backups, essentially, achieve the same goal. I was just thinking of RAID 1 as a way to streamline the process, to keep 2 drives in sync in the event of failure rather than to resort to scheduling backups and then restoring backups that may be a few days old. Not a big problem vs. complete data loss, I was just trying to better automate the process. 

If that's the case, you should probably just stick with RAID1 so you have a mirror, but keep in mind this will only mirror the day and if a file is changed or corrupted, the array will mirror it the same as if it was a good file. That is why versioned backups are so important.

> There comes a certain point, though, when creating convenience becomes very inconvenient. The limitations of software RAID, it seems, would be more of a hindrance to my system than a help. Somewhere in the not-too-distant future, I will probably build a NAS for these drives. In the mean time, I think I will just resort to scheduling backups of one drive to its twin.

How do you mean it creating a convenience can becoming inconvenient? Once you get the array set up, it should do its thing without any user intervention. The issue is getting is set up and everything. Here's a good tutorial on creating an array with mdadm: [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

Granted it is for RAID5, but it should give you a good idea as far as what needs to be done.

> I'm looking at either [LuckyBackup]("http://luckybackup.sourceforge.net/index.html") or [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/index.html") to handle rsync. Both have versions for OSX/Win/Linux. Does rsync work well from one network drive to another? I assume it wouldn't be much of a problem if they are both mounted to local folders (ie, /media/drivex). I'm not TOO worried about having versioned backups of documents (though I say that with a grimace). I have a good habit of using the "save as" button incrementally to create my own versions in the event of file corruption. That being said, I would consider a versioned backup tool if you have any suggestions.

What OSes are you going to be syncing to the NAS? I have used robocopy on Windows 7 for ages now and I just have it set to run the batch script as a scheduled task at like midnight every day. It syncs to my server and then my server does an incremental backup at 2am in the morning.

---

### Post by Harp on 2014-01-28
> **CharlesA said:**
> What OSes are you going to be syncing to the NAS?

At this time, I primarily boot up in either OSX Lion, Windows 8, or Ubuntu 13.10

> **CharlesA said:**
> How do you mean it creating a convenience can becoming inconvenient? Once you get the array set up, it should do its thing without any user intervention. The issue is getting is set up and everything.

Exactly. I mean that the effort it takes to set up a RAID1 (in my case) outweighs the end benefits. If a RAID won't work the way I need it to (across multiple OSes) then it's not really a viable option and setting it up would just be wasted effort. It would be nice to be able to connect the drives and have them show up as one device that automatically mirrors itself to an internal twin in the background. But a RAID1 won't hold across OSes, so that's probably not my best option. Creating backups from one drive to its twin with something like LuckyBackup will probably work but they will still show up as two separate drives when I connect them.

Do you see what I mean? Since the two drives share a single enclosure, I would like to have only one of the drives mount when connected and have the second drive remain hidden, storing automatic backups of the first. Is there another way to achieve this?

---

### Post by CharlesA on 2014-01-28
> **Harp said:**
> Exactly. I mean that the effort it takes to set up a RAID1 (in my case) outweighs the end benefits. If a RAID won't work the way I need it to (across multiple OSes) then it's not really a viable option and setting it up would just be wasted effort. It would be nice to be able to connect the drives and have them show up as one device that automatically mirrors itself to an internal twin in the background. But a RAID1 won't hold across OSes, so that's probably not my best option. Creating backups from one drive to its twin with something like LuckyBackup will probably work but they will still show up as two separate drives when I connect them.

Do you see what I mean? Since the two drives share a single enclosure, I would like to have only one of the drives mount when connected and have the second drive remain hidden, storing automatic backups of the first. Is there another way to achieve this?

It can be seen from any OS as long as you have a machine to use as a server. I used Samba for the most part for my file sharing needs. I was speaking more along the lines of moving the enclosure between machines, which would not work if you want to run RAID of it and the enclosure itself doesn't support "transparent" RAID - where the enclosure shows up as a single drive and does everything in the background, unseen to the OS.

You could check out the user guide and see if your NAS box is capable of that, otherwise you'd need a server to connect the NAS to.

---

### Post by SeijiSensei on 2014-01-29
Isn't the only solution that would work with multiple operating systems a dedicated hardware RAID card with drivers for all three operating systems the OP uses?  Something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124028)?

BTW, don't be concerned that Ubuntu isn't in the list of Linux distributions.  These cards use kernel-level drivers that work with all distributions.

---

### Post by TheFu on 2014-01-29
> **SeijiSensei said:**
> Isn't the only solution that would work with multiple operating systems a dedicated hardware RAID card with drivers for all three operating systems the OP uses?  Something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124028)?

BTW, don't be concerned that Ubuntu isn't in the list of Linux distributions.  These cards use kernel-level drivers that work with all distributions.

No that won't work.  1 OS, 1 RAID install.  Even if it did happen to work (which I'm 99.999% certain it will not), the first kernel patch from any of the OSes will likely break the storage.  Plus, you'd be stuck with RAID and NTFS which is just  WRONG-WRONG-WRONG for OSX or Linux operating systems.

Other computing devices need to access the storage over the network.

---

### Post by Harp on 2014-01-29
> **CharlesA said:**
> You could check out the user guide and see if your NAS box is capable of that, otherwise you'd need a server to connect the NAS to.

Actually, the enclosure I have is not a NAS box, just a simple HD enclosure, so I would have to build a NAS if I want to go that route (which I probably will do at some point).

I've settled on **rsnapshot **to do the backups from one drive to its twin:

```
sudo apt-get install rsnapshot
sudo gedit /etc/rsnapshot.conf
```

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://www.deb-admin.com/using-rsnapshot-for-securely-backing-up-your-data/](http://www.deb-admin.com/using-rsnapshot-for-securely-backing-up-your-data/)

It's pretty simple to use with a decent configuration file. It uses rsync and versioning with hard links. It also is supposedly available for OSX/Win/Linux but I've only used it in Ubuntu so far (which is my main OS anyway). 

**My idea is to set up both of the drives in fstab with only the main drive to automount. Then I set up cron to, at the designated time, mount the backup drive, run rsnapshot, then umount the backup drive when rsnapshot completes.** How does that sound?

I ran a test backup with no trouble locally but right now my router is giving me trouble setting up ssh, which rsync requires to run the backup over the network.

---

### Post by CharlesA on 2014-01-29
Oh. I was under the impression it was actual NAS box, which most multi-bay enclosures are.

You don't need to add the backup drive to fstab if you are going to mount it manually.

Depending on what the router supports, you could just mount the backup drive as a NFS or Samba share and rsync to it that way.

---

### Post by Harp on 2014-01-29
> **CharlesA said:**
> You don't need to add the backup drive to fstab if you are going to mount it manually.

True. I usually do anyway because it's simpler to just set it up once and do a manual "$ sudo mount /media/drivex" rather than a string of mount variables.

> **CharlesA said:**
> Depending on what the router supports, you could just mount the backup drive as a NFS or Samba share and rsync to it that way.

Traditionally, I have used cifs-utils to allow me to mount all my network drives as generic cifs. I have a drive or two that are hfs+ and mounting them as cifs seems to work the best so I just use it for everything. 

Since these drives would be mounted to local directories this way (/media/drive1, /media/drive2) I can run rsnapshot and it **will **create the backup files to the second drive over the network but it does not have the right permissions to chmod, chgrp, etc., the files it creates and so returns an error. So I need to figure out my ssh so I can set rsnapshot up with an rsa keypair for password-less logins to the remote host.

phew.

---

### Post by CharlesA on 2014-01-29
> **Harp said:**
> True. I usually do anyway because it's simpler to just set it up once and do a manual "$ sudo mount /media/drivex" rather than a string of mount variables.

What variables?

I mount my drives via UUID, but I think the only variable use is -t ext4, and that is a "just in case" because I think it should mount the drive fine even without specifying the file system.

> Traditionally, I have used cifs-utils to allow me to mount all my network drives as generic cifs. I have a drive or two that are hfs+ and mounting them as cifs seems to work the best so I just use it for everything. 

Since these drives would be mounted to local directories this way (/media/drive1, /media/drive2) I can run rsnapshot and it **will **create the backup files to the second drive over the network but it does not have the right permissions to chmod, chgrp, etc., the files it creates and so returns an error. So I need to figure out my ssh so I can set rsnapshot up with an rsa keypair for password-less logins to the remote host.

phew.

Oh ok, I see what you want to do. FWIW, I currently have a similar setup on my backup server - rsync via SSH with a passphrase-less key syncing to a mdadm array on that server from my main server. That would probably work best but you will also run into slow transfer speeds due to the encryption, and the possibility of maxing out the network too.

---

### Post by Harp on 2014-01-29
> **CharlesA said:**
> Oh ok, I see what you want to do. FWIW, I currently have a similar setup on my backup server - rsync via SSH with a passphrase-less key syncing to a mdadm array on that server from my main server. That would probably work best but you will also run into slow transfer speeds due to the encryption, and the possibility of maxing out the network too.

Maxing out the network is something I hadn't really thought about. I had assumed that since the drives are together in the same enclosure they would just transfer files between one-another. But I guess then they would need a processor. What would be the actual data transfer route between two drives broadcast over a wireless network? Would the data be first transmitted to my cpu and then sent back out to the other drive? That's a lot of wasted bandwidth.

If I had the drives connected to a server, then that's where I would initiate the backup from, doing the transfers there rather than over the network. I would want to build a server because my old netbook doesn't have USB3 capabilities. That would cost, what, about $200 in parts? What kind of processor/how much memory would be required for something like that?

---

### Post by CharlesA on 2014-01-29
Depends on how you want to set it up. In my setup, I am transferring files across the network from one machine to the other. If both drives are connected to the router and it supports rsync, you should be able to sync them locally, but that would also put strain on the router at the same time.

---

### Post by TheFu on 2014-01-30
Looks like you are now seeing some of the concerns we raised near the beginning of this thread?

I've never been happy with CIFS mounts for backups, unless it was just data (like video or audio files).  For programs and user files, the lack of permissions control is a complete failure under Linux. I run multi-user systems, so having the exact, correct, permissions in a backup AND being able to easily restore those is critical.

+1 for using a storage server that supports rsync.  Rsync will use ssh by default, but that is not mandatory. It can be disabled in the rsync command. Hopefully, you are scripting this stuff. Scripts do 3 things - make a record of what the options are, make the process 100% repeatable, and makes invoking the process from cron easier.

Mounting ... for every storage location I mount, a tiny script is created. Here are a few examples:
```
$ ls mnt[_-]*
mnt_algo.sh*  mnt-lap-movies.sh*  mnt_romulus.sh*
mnt-regulus.sh*   mnt_mediagate.sh*   mnt-rec_tv.sh*
mnt-qbe.sh*    mnt-mybook.sh*	  mnt-wdtv.sh*
```

Don't worry about the "*" at the end.  I've aliased **ls='ls -F'** - find that extremely useful to quickly see what is what in a directory.

Let's see, what other questions have I missed .... 
When just starting out with network storage, might be easiest to use a simple NAS device. Seagate made a dock for $20-$30 a few years ago with a GigE port that supported NFS, CIFS, Linux file systems and rsync. Haven't seen this in awhile.  I know that Addonics has a eSATA-to-GigE NAS [http://www.addonics.com/products/nas40esu.php](http://www.addonics.com/products/nas40esu.php), but they want $90 for it. It supports EXT4 (and a few other Linux-specific file systems), which is critical for our needs. Avoid the USB2 ports and use eSATA. Last year, dual eSATA docks were $40 here on clearance - I'm staring at a BlacX dual dock now with 4TB (2x2TB) of storage connected via eSATA. eSATA is a better choice than USB3 since it doesn't go through a translation layer and supports native SATA commands. Performance is identical to internal HDD performance and HDD tools work that will not work over USB3 connections.  Spinning HDDs will never need the 6Gb/s of SATA-II or USB3 specs. Real world transfers peak around 80MB/s over a GigE network anyway. I think the HDDs do about 120MB/s native, so 1.5Gb/s SATA is fine.  Of course, with SSDs, the higher spec protocols can help, but not for spinning HDDs.

The downside is that eSATA doesn't allow 16 HDDs connected like USB hubs can. That is mucho expansion, at a performance price.

BTW, my external disk array is addonics - purchased directly from them. Never had any issues and I'd buy stuff from them again. I've looked at the NAS 4.x devices before, but decided to go with a different solution.

If you want/need to build a storage server ... check out the freeNAS server-build lists to get some ideas.  Often going with a quality server-class Supermicro motherboard will save add-in cards and costs since it will have dual gige NICs, 8-sata ports built-in and lots of room for PCIe cards that desktops just do not have, even on a microATX MB.  Plus seeing which SATA and SAS cards work best is a good thing too.  8-port SAS can support many more SATA drives than I would have imagined ... I think 32 HDDs? Something like that.

As you are learning, storage design and deployment can be complicated.

---

### Post by Harp on 2014-01-30
> **TheFu said:**
> I've never been happy with CIFS mounts for backups, unless it was just data (like video or audio files).  For programs and user files, the lack of permissions control is a complete failure under Linux. I run multi-user systems, so having the exact, correct, permissions in a backup AND being able to easily restore those is critical.

Preach it, brother.

> Hopefully, you are scripting this stuff. Scripts do 3 things - make a record of what the options are, make the process 100% repeatable, and makes invoking the process from cron easier.

Mounting ... for every storage location I mount, a tiny script is created.

What exactly is in your mount scripts? I just amend /etc/fstab with:
```
# sudo apt-get install cifs-utils
# Mount with $ sudo mount /media/*
# 1TB
//192.168.1.1/1TB /media/1TB cifs sec=ntlm,credentials=/PATH/TO/creds,rw,uid=1000 0 0
```

Which is pretty easy to replicate and also allows the network drive to be mounted automatically at startup without having to add scripts to the startup applications. What's the perk of using mount scripts over just fstab? I don't know much about cron.

> If you want/need to build a storage server ... check out the freeNAS server-build lists to get some ideas.  Often going with a quality server-class Supermicro motherboard will save add-in cards and costs since it will have dual gige NICs, 8-sata ports built-in and lots of room for PCIe cards that desktops just do not have, even on a microATX MB.  Plus seeing which SATA and SAS cards work best is a good thing too.  8-port SAS can support many more SATA drives than I would have imagined ... I think 32 HDDs? Something like that.

Right now I'm looking at these for a server case/mobo:
[http://www.in-win.com.tw/Corporate/en/goods.php?act=view&id=BQ656](http://www.in-win.com.tw/Corporate/en/goods.php?act=view&id=BQ656)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130735](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130735)

Trying to find the right balance between compactness and capability. It's a very small case but I know someone who's offering to sell it to me cheap, and it takes only one 2.5" HD, which I happen to have laying around. The mini-itx motherboard has USB3, which is how I would be connecting drives. Not quite SATA's 6Gb/s, but close. Like you said, the drives probably won't use it anyway.

Throw in 8GB RAM and a Haswell and install Ubuntu Server. It's probably more than I need for what I'm trying to do but I think it will last me a while.

The question this brings up is: if I'm going to be attaching these drives to a dedicated server, should I do away with NTFS completely and reformat the drives with something like ext4 instead? With ntfs-3g installed on my mac and ubuntu systems, NTFS drives are very accessible across platforms. It's the only filesystem type I've found with this sort of portability while still being capable of storing large size files. Connected to a dedicated linux server and mounted over the network, maybe ext4 would be better than NTFS mounted as CIFS (especially if I set up a software RAID), but I would lose that portability completely if I ever need to connect to a drive directly from a non-linux system.

---

### Post by CharlesA on 2014-01-30
This is how I mount my backup drive on my server:

```
# Check if Array is mounted and exit it if is not.
if $mountpoint -q $arraypath
# If Array is mounted, then mount daily backup drive
  then
    { $mount -t ext4 $uuid $dailypath; } 2> $error || { echo "Mounting of backup drives failed" | $mail -s "Backup failed for $longdate" $email $cell; exit; }
# If not, email me that the array isn't mounted and that the backup failed
  else
    { echo "Raid Array not mounted!" | $mail -s "RAID Array not mounted! Backup Failed for $longdate" $email $cell; exit; }
fi

```

UUID is defined earlier:

```
# UUID Variable
uuid="UUID=bunchanumbers"

```

Spaghetti code!

That case and mobo should work fine. I've got my current server housed in one of [these]("http://www.lian-li.com/en/dt_portfolio/pc-9f/") and it's running an i7, but I am also using it as a  NAS and VM host, so I needed the horsepower.

> **Harp said:**
> The question this brings up is: if I'm going to be attaching these drives to a dedicated server, should I do away with NTFS completely and reformat the drives with something like ext4 instead? With ntfs-3g installed on my mac and ubuntu systems, NTFS drives are very accessible across platforms. It's the only filesystem type I've found with this sort of portability while still being capable of storing large size files. Connected to a dedicated linux server and mounted over the network, maybe ext4 would be better than NTFS mounted as CIFS (especially if I set up a software RAID), but I would lose that portability completely if I ever need to connect to a drive directly from a non-linux system.

I would say yes. You will only be accessing those drives over the network, so let the server dot he file sharing/authentication. All the drives I use on my server are running ext4.

---

### Post by Harp on 2014-01-30
> **CharlesA said:**
> I would say yes. You will only be accessing those drives over the network, so let the server dot he file sharing/authentication. All the drives I use on my server are running ext4.

Do you ever have to connect them directly to Windows or Mac machines? This is sort of a hypothetical (I keep a copy of Windows around almost as a novelty incase I need to run a keygen or some windows-specific application - same goes for OSX) but say that I needed to mount an ext4 drive directly into Windows/OSX in order to speed up the transfer of some large file. What would be the best way of going about this?

After a quick search, I found [Paragon ExtFS]("http://www.paragon-software.com/home/extfs-mac/") for Mac and [Ext2Read]("http://sourceforge.net/projects/ext2read/") for Windows but are there any better options that you (or anyone eavesdropping) may be aware of?

> That case and mobo should work fine. I've got my current server housed in one of these and it's running an i7, but I am also using it as a NAS and VM host, so I needed the horsepower.

I went back and forth trying to decide between building a small, individual server that external storage devices would connect through or building a bigger server box that would mount the drives internally. As a general rule of thumb, I like to keep hardware elements separated as much as possible to make them easier to upgrade or replace in the future.

> This is how I mount my backup drive on my server:

```
# Check if Array is mounted and exit it if is not.
if $mountpoint -q $arraypath
# If Array is mounted, then mount daily backup drive
  then
    { $mount -t ext4 $uuid $dailypath; } 2> $error || { echo "Mounting of backup drives failed" | $mail -s "Backup failed for $longdate" $email $cell; exit; }
# If not, email me that the array isn't mounted and that the backup failed
  else
    { echo "Raid Array not mounted!" | $mail -s "RAID Array not mounted! Backup Failed for $longdate" $email $cell; exit; }
fi
```

I'll try to work on a script to automate the mount > backup > umount tasks. Thanks for the headstart.

---

### Post by CharlesA on 2014-01-30
> **Harp said:**
> Do you ever have to connect them directly to Windows or Mac machines? This is sort of a hypothetical (I keep a copy of Windows around almost as a novelty incase I need to run a keygen or some windows-specific application - same goes for OSX) but say that I needed to mount an ext4 drive directly into Windows/OSX in order to speed up the transfer of some large file. What would be the best way of going about this?

So far I haven't had to do that. The drives are sitting on my LSI raid card:

```
Adapter 0 -- Virtual Drive Information:
Virtual Drive: 0 (Target Id: 0)
Name                :
RAID Level          : Primary-6, Secondary-0, RAID Level Qualifier-3
Size                : 8.185 TB
Sector Size         : 512
Is VD emulated      : Yes
Parity Size         : 5.457 TB
State               : Optimal
Strip Size          : 256 KB
Number Of Drives    : 5
Span Depth          : 1
Default Cache Policy: WriteBack, ReadAdaptive, Cached, Write Cache OK if Bad BBU
Current Cache Policy: WriteBack, ReadAdaptive, Cached, Write Cache OK if Bad BBU
Default Access Policy: Read/Write
Current Access Policy: Read/Write
Disk Cache Policy   : Enabled
Encryption Type     : None
Bad Blocks Exist: No
Is VD Cached: No

```

So it would be a bit difficult for me to hook it up to a Windows box. :p Now, the backup drive, I could access with a Linux VM because it is ext4.

> I went back and forth trying to decide between building a small, individual server that external storage devices would connect through or building a bigger server box that would mount the drives internally. As a general rule of thumb, I like to keep hardware elements separated as much as possible to make them easier to upgrade or replace in the future.

Do whatever you think is best. Sometimes getting an external enclosure and running it off eSATA or USB3 works wonders as far as keeping the server itself small.

---

### Post by TheFu on 2014-01-31
> **Harp said:**
> Do you ever have to connect them directly to Windows or Mac machines? This is sort of a hypothetical (I keep a copy of Windows around almost as a novelty incase I need to run a keygen or some windows-specific appl

Nope. That never crossed my mind - mainly because **network storage completely rocks** and getting 80MB/s transfers is fast enough here vs the hassle of moving HDDs around.

Plus non-Linux OSes are a 2nd-class choice around here.

---

### Post by Harp on 2014-01-31
While I'm waiting for the parts to arrive for my new server build, I thought I would take that old netbook I have on a dry-run as a temporary server. It's not running Ubuntu Server, just regular Ubuntu Desktop. I've never used Ubuntu Server yet, so please let me know if there will be differences in my methods.

Here's what I did: connected the drives to the netbook via USB and then attached the netbook to the router via ethernet. I then set up a static IP and set the port-forwarding in my router to forward ssh and ftp requests to the netbook's static IP and set the netbook firewall to accept in/out ssh & ftp connections on ports 22 & 21, respectively. Then, I installed openssh-server on the netbook.

The SSH works beautifully, and I can use SFTP just as well in Nautilus' "Connect to Server" option, or in Firefox, Filezilla, etc.

But I have a few questions/problems:

1) **I seem to be unable to use ftp to access the netbook.** I'm not sure exactly what I'm doing wrong (as I said, I set my router to forward ftp requests to the netbook's static IP and opened up the port in the netbook's firewall). This is something I would like to resolve so that I could share files with people outside of my network using FTP in a browser so that they don't have to use the command line or install additional software (SFTP is possible on a mac through the Terminal only, I believe, or Filezilla).

2) **How do I go about setting up a guest account for FTP or SFTP?** For example, I have some directories on the drive which I will want to allow guests read-only access to and other directories I would like to deny them access to altogether. I could do this quite easily before in my router firmware but I'm not sure how to do it from a server. Create a separate user account? Would Ubuntu Server have more obvious solutions to this?

3) **How do I set the top-level access point for FTP or SFTP?** For example, if I were to allow a guest remote access to my server with [ftp://guest@server.example.com](ftp://guest@server.example.com), I would want them to connect directly to a drive mounted at /media/Drive1, rather than at the / or /home level.

Thanks for all the help, I'm a noob at these things and I hope this thread isn't getting too digressive.

---

### Post by SeijiSensei on 2014-02-01
I'd start here: [https://help.ubuntu.com/12.04/serverguide/ftp-server.html](https://help.ubuntu.com/12.04/serverguide/ftp-server.html)

---

### Post by TheFu on 2014-02-01
I'm a huge believer that plain FTP shouldn't be used by 99.9999% of the systems out there.
[Here is why.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")

Related to sftp/ssh/scp - I love those tools, provided the [connections are secured.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures") Using fail2ban or denyhosts is pretty easy, but definitely only allow key-based connections from the internet.

---

### Post by CharlesA on 2014-02-01
> **TheFu said:**
> I'm a huge believer that plain FTP shouldn't be used by 99.9999% of the systems out there.
[Here is why.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")

Related to sftp/ssh/scp - I love those tools, provided the [connections are secured.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures") Using fail2ban or denyhosts is pretty easy, but definitely only allow key-based connections from the internet.

+1 to not using FTP and using SFTP instead.

I've been running [CSF]("http://www.configserver.com/cp/csf.html") on my servers, but it might be overkill for a home server.

---

### Post by Harp on 2014-02-01
What I would basically like to do (for myself, as an admin on the network) is to have the server-attached drives automount as local drives on my client computers. Basically to simulate as if they were attached to the clients themselves. I'm trying out sshfs but I keep getting errors saying "read: Connection reset by peer." I'm still trying to figure out what's going on.

For guests accessing my network, I would like a way for them to easily read/download files (certain files, not all) from the server-attached drives only (deny access to the root directory). Is this something that can be done with sshfs? Perhaps by creating a guest user account and including them in a group with access rights limited to these certain directories?

> I'm a huge believer that plain FTP shouldn't be used by 99.9999% of the systems out there.

I agree that SFTP is better and more secure than FTP (hence the "S" in the front), but FTP is the easiest way for someone like one of my noob friends to just open Safari or IE *shudder* and access the files, rather than having to use Filezilla. I would like to have it working as a sort of backup plan but it's not a huge deal if they need to use Filezilla. I guess if they can't figure Filezilla out then they don't deserve access to my data anyway.

---

### Post by CharlesA on 2014-02-01
Tbh, I would use something like ownCloud instead of FTP if all they want to do is access them via web browser.

---

### Post by TheFu on 2014-02-02
> **Harp said:**
> What I would basically like to do (for myself, as an admin on the network) is to have the server-attached drives automount as local drives on my client computers. Basically to simulate as if they were attached to the clients themselves. I'm trying out sshfs but I keep getting errors saying "read: Connection reset by peer." I'm still trying to figure out what's going on.

Not certain I recall all the parameters of this thread anymore. So many threads here.  For trusted networks (think LAN only), use NFS.  sshfs completely rocks when the network cannot be trusted, but it has some important limitations - like it doesn't fully support hardlinks and there are issues with softlinks. Also, sshfs uses per-person authentication - can't be shared with other users, I believe. Please check if that is true yourself. sshfs has the overhead of TCP, FUSE and encryption too. All these things make it a little slower.

> **Harp said:**
> For guests accessing my network, I would like a way for them to easily read/download files (certain files, not all) from the server-attached drives only (deny access to the root directory). Is this something that can be done with sshfs? Perhaps by creating a guest user account and including them in a group with access rights limited to these certain directories?

sshfs allows access to any directory that ssh allows access for the specific userid. Using nromal file permissions, it is possible to block access to specific areas of the file system, but NOT to /. That isn't the way UNIX/Linux was designed.  Ok ... you could setup a chroot for the sshd to run inside and extremely limit the available directories there, but I've never considered that necessary - just as secure to properly lock down a server to begin.  It is possible to break out of chroot jails for skilled people.  If you don't trust these folks enough to view your /etc/ directory, then don't give them system access at all. It isn't like any directories on the system that aren't locked down shouldn't be fine for the entire world to see anyway.  If you think that isn't the situation, then perhaps file permissions need to be locked down a little more on the box?

> **Harp said:**
> I agree that SFTP is better and more secure than FTP (hence the "S" in the front), but FTP is the easiest way for someone like one of my noob friends to just open Safari or IE *shudder* and access the files, rather than having to use Filezilla. I would like to have it working as a sort of backup plan but it's not a huge deal if they need to use Filezilla. I guess if they can't figure Filezilla out then they don't deserve access to my data anyway.

**WinSCP** is easy to use for sftp by Windoze people as well.  I can't help OSX users.
Most Linux file managers support sftp:// URLs.

We are way off-topic. Might be good to start another thread to get other people with different ideas involved too.

---

### Post by Harp on 2014-02-04
> **TheFu said:**
> We are way off-topic. Might be good to start another thread to get other people with different ideas involved too.

I know, I'm getting a bit off-topic. Just trying to organize some of the logistics leading toward my original goal. To bring things back around, I received the last of my new server's hardware in the mail this morning and went ahead and built it: ([picture]("http://imgur.com/0agJgYW"))

Main Specs:
MSI mini-ITX LGA 1150 motherboard (with lots of USB3 ports)
Intel Haswell i5 CPU
8GB RAM
350GB 2.5" HDD
24x DVD Burner

The box measures 8.5" x 3" x 8.5", which fits conveniently in a cabinet with my drive enclosures.

I installed Ubuntu Server 13.10 (64 bit) and set up the SSH keys and whatnot, getting it all set up on my network. Then I connected the two drives in question via USB3 (I've been calling the twin drives "R2" and "D2"). R2 contains all of the data and is currently formatted in NTFS. D2 is blank and has been reformatted to ext4. The server is currently running rsync, copying all the data from R2 to D2. Once that is finished, I will reformat R2 to ext4 and RAID them together in probably a RAID 1 (?).

What would be the best way to do this? Mdadm?

I'm thinking maybe I could control guest access by creating a separate user account on the server. So I would have two users on the server, let's call them "admin" and "leech." Then I would create a group with leech as a member and and then change the group permissions of the directories I would like to grant them access to. Basically locking the guest out on the user side and granting them permissions a la carte. That way, when someone accesses my sftp in a browser, for example, they will be prompted to enter a username and password. If they enter the guest username, they will be granted access to only the files with those group permissions. Then the question becomes how I would automatically redirect them on login.

> **CharlesA said:**
> Tbh, I would use something like ownCloud instead of FTP if all they want to do is access them via web browser.

I hadn't thought about OwnCloud but it looks like it could possibly be a very decent solution to sharing data with people outside of my network. When I get some time I will experiment with it some, but for now I'll probably just stick to SFTP.

So I'm on the home stretch now. I have my server and, once my file transfers complete, I will set up the RAID and have that connected to it. Now I just need to work out a few particulars concerning the automounting of the RAID to the server (tried usbmount, looking for something better) and subsequently to any client pcs, as well as the creation of guest access. For now, I have "bookmarked" the sftp location of the drive in Nautilus and it connects with a single click. Not bad in the interim.

Thanks for all the help, guys.

---

### Post by CharlesA on 2014-02-04
mdadm would work, but I would not create a RAID with a drive with data on it.

Another option might be SnapRAID: [http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04](http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04)

---

### Post by TheFu on 2014-02-04
I was under the impression that you were convinced that **RAID1 wasn't really what you wanted.** Backups are 1000x more important than RAID mirrors. If you have an automatic, daily, versioned, backup, then there is very little chance that a disk failure would loose much important data. OTOH, using RAID can allow viruses and corrupted files to be stored in both locations, immediately. Backups with versioning avoids those and many other issues.

I've looked at snapRAID - more like file storage with parity bits, cloned from time to time - not really a RAID.  I'm confused by their claims. 
I don't see how with 1/3rd the data for parity that a complete loss of a HDD can be recovered. I think that is impossible unless RAID5 is used (which stores data and parity across all 3 disks). 

I use par2 (a parity tool) all the time and in order to recover a 100% lost file, the parity needs just a little over 100% of the same storage as the original.  Slightly corrupted files need much, much less parity (5-10%), but I'm talking about a 3 drive setup with SnapRAID where 2 drives for data and 1 is for parity. All HDDs identical sized.  There just isn't enough room on the parity disk to restore all the files if 1 data HDD is 100% failed. Physics gets in the way.  I'm probably just not understanding their claims correctly. With computers, _magic_ seldom happens.

To me a false sense of security is worse than none at all.

---

