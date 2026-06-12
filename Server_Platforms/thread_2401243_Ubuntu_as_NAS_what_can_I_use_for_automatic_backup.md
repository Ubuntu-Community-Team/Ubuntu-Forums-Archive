---
title: "Ubuntu as NAS: what can I use for automatic backup?"
date: 2018-09-15
forum: Server Platforms
---

### Post by webmiester on 2018-09-15
Hi,

I was reading an article on commercially available NAS and it said that we just have to configure the NAS and then the NAS will be the one to copy the files from our PCs automatically, periodically without the person using the PC even noticing it.

So, i've setup an Ubuntu server with RAID, placed Samba and LDAP, and the server could now be accessed by my network computers. What software do I need on the NAS to automatically do the backup?  Also, once data is compromised in the originating PC, how do I restore the data from the NAS?  Thanks

---

### Post by TheFu on 2018-09-15
It depends.  There are thousands of different solutions.  
"PC" is a little vague.  The backup and recovery methods used will drastically depend on the OS.

These forums are full of answers for how to backup Linux systems.

---

### Post by webmiester on 2018-09-17
Thanks,

Sorry I didnt make so much specifications:

My NAS will be running Ubuntu Server, while most of the office PCs will be using windows.  Ill be using Ubuntu desktop on a few of the office computers.  Ive read that Ill need rsync.  So rsync will copy the files from the office windows and ubuntu PCs into the NAS.  What can I use to restore the files in case of lost files?

---

### Post by webmiester on 2018-09-17
> **TheFu said:**
> It depends.  There are thousands of different solutions.  
"PC" is a little vague.  The backup and recovery methods used will drastically depend on the OS.

These forums are full of answers for how to backup Linux systems.

There are thousands of solutions.  I just need one.  What can you recommend in terms of easy to use, and security?

---

### Post by TheFu on 2018-09-17
I can't recommend anything.  I don't use Windows much and wouldn't trust it to be secure.
I don't think rsync meets to minimum requirements for a versioned backup tool.  BackPC or amanda or something like that, perhaps?  

Whatever you use, don't use shared storage with Windows. Use a client/server architecture and have the "server" pull the backups.  These days, some of the nastiest malware out is the crypto-locker stuff.  Any storage the client can access as shared storage can be encrypted.  Using a client/server backup tool avoids having all your backups encrypted.

---

### Post by SeijiSensei on 2018-09-17
Users should be writing their files to the NAS server directly rather than their local machines.  Trying to manage the latter becomes a royal pain. If they are Windows clients, set up home shares with Samba that are automatically mounted when the Windows machines boot.  Usually the convention is the map drive H:\ to the user's home directory on the server.  The Samba wiki reviews methods to do this depending on the version(s) of Windows in use, whether you use Active Directory, etc.

---

### Post by webmiester on 2018-09-21
> **SeijiSensei said:**
> Users should be writing their files to the NAS server directly rather than their local machines.  Trying to manage the latter becomes a royal pain. If they are Windows clients, set up home shares with Samba that are automatically mounted when the Windows machines boot.  Usually the convention is the map drive H:\ to the user's home directory on the server.  The Samba wiki reviews methods to do this depending on the version(s) of Windows in use, whether you use Active Directory, etc.

I tried this setup, but during our tests, the read write was really slow.  I think I was using a computer that had specs that was too low.  Ill try this out with a computer with higher specs.  Then also, I was thinking of still having a backup pull the files from this NAS which they are putting their files to.  With a low-spec computer though, I think I can live with a backup computer pulling files from other PCs.  So even if the computer doing the backup is slow, it wont disturb the work of the others as the backup is done automatically and in the background.

---

### Post by webmiester on 2018-09-21
> **TheFu said:**
> I can't recommend anything.  I don't use Windows much and wouldn't trust it to be secure.
I don't think rsync meets to minimum requirements for a versioned backup tool.  BackPC or amanda or something like that, perhaps?  

Whatever you use, don't use shared storage with Windows. Use a client/server architecture and have the "server" pull the backups.  These days, some of the nastiest malware out is the crypto-locker stuff.  Any storage the client can access as shared storage can be encrypted.  Using a client/server backup tool avoids having all your backups encrypted.

Yeah,
 My idea is to have the backup pull the files from their computers directly.  Isnt this what rsync does?

---

### Post by HermanAB on 2018-09-21
First get SSH to work, so that you can log into any machine from any machine without having to type a password, then read up on rsync.

My NAS, is a Raspberry Pi3 with a terabyte of USB memory sticks.  

I backup my Mac with a script like this:
$ cat sync2rpi.sh 
#! /bin/bash
# Rync to Rpi 192.168.1.100
# Assumes your public key is installed in /home/pi/.ssh
rsync -avze ssh --progress --delete --max-delete=100 --max-size=20M --exclude '.Trash' --exclude "*bak" --exclude "*old" --exclude "*iso" ~/. pi@rpi:/mnt/sda/dataa/

The trick is to include everything "~/.", and then exclude a few things that you don't want to backup.  That is rather more effective than exhaustively specifying the things that you do want to backup, since that list is always changing.

BTW, on a Mac, 'launchd' will act like Linux 'anacron' and scripts that failed to run because the machine was asleep at the scheduled time, will run when it wakes up.  So you eventually need to read up on 'cron' and 'anacron' also.

---

### Post by webmiester on 2018-09-21
> **SeijiSensei said:**
> Users should be writing their files to the NAS server directly rather than their local machines.  Trying to manage the latter becomes a royal pain. If they are Windows clients, set up home shares with Samba that are automatically mounted when the Windows machines boot.  Usually the convention is the map drive H:\ to the user's home directory on the server.  The Samba wiki reviews methods to do this depending on the version(s) of Windows in use, whether you use Active Directory, etc.

If we users write to the NAS directly, this is considered a client/server architecture right?  The NAS is the server while the individual computers are the clients.

---

### Post by webmiester on 2018-09-21
> **HermanAB said:**
> First get SSH to work, so that you can log into any machine from any machine without having to type a password, then read up on rsync.

My NAS, is a Raspberry Pi3 with a terabyte of USB memory sticks.  

I backup my Mac with a script like this:
$ cat sync2rpi.sh 
#! /bin/bash
# Rync to Rpi 192.168.1.100
# Assumes your public key is installed in /home/pi/.ssh
rsync -avze ssh --progress --delete --max-delete=100 --max-size=20M --exclude '.Trash' --exclude "*bak" --exclude "*old" --exclude "*iso" ~/. pi@rpi:/mnt/sda/dataa/

The trick is to include everything "~/.", and then exclude a few things that you don't want to backup.  That is rather more effective than exhaustively specifying the things that you do want to backup, since that list is always changing.

BTW, on a Mac, 'launchd' will act like Linux 'anacron' and scripts that failed to run because the machine was asleep at the scheduled time, will run when it wakes up.  So you eventually need to read up on 'cron' and 'anacron' also.

This is really cool.  I am also considering using the RPI 3 but this time using USB to SATA converter so I can use Hard Disk drives.  I just realized that since the RPi will be pulling the files from the other computers, we dont need it to have SAMBA installed on the RPi even if the computer it will be pulling data from is a windows computer.  Is this right?

If so, this makes it so much safer since the windows computer can't "see" the file system on the RPi.

as for the "~/", it should be a problem as long as I tell my staff to save their files only in particular directories of their computers.  So rsync will only get files from these directories.

How long (months or years) have you been running your setup? I am interested to know how many years an RPi will last.

---

### Post by TheFu on 2018-09-21
> **webmiester said:**
> If we users write to the NAS directly, this is considered a client/server architecture right?  The NAS is the server while the individual computers are the clients.

Not as far as malware is concerned. The goal is **Not** to let the malware have access to the remote storage. Generally, if it is NOT mounted, then it will be fine.  OTOH, if it is mounted, then the malware like crypto-locker can encrypt anything connected.

If do NAS is connected to Windows systems with a remote mount, that storage can all be encrypted via crypto-locker type malware.  Ensure you have automatic, versioned, backups, that aren't accessable by any clients using a mount.

For unix-to-unix backups, the tools generally use ssh for the encrypted network connection. rsync does. rdiff-backup does. duplicity can.  Crypto-locker-like malware doesn't deal with that.

I have a 3+ yr old raspberry pi v2.  I find it too slow to be used as a backup server.  GigE networking (with that sort of throughput) is necessary.  No raspberry pi equipment does that today.  There are ARM-based SBCs which can, but those cost 2-4x the price of a rPi.  If you are spending more than $100, then using a cheap Pentium-based Intel as the backup server makes more sense.  IMHO.

---

### Post by HermanAB on 2018-09-21
I let the clients do their own backup with rsync over the network, since I only have two laptops at home.  The server doesn't 'pull' it, but you could do the same, by letting the server connect to the client with ssh and then execute the backup script on the client. This keeps the majority of the processing load on the laptop and not on the dinky little Raspberry Pi.

---

### Post by TheFu on 2018-09-21
> **HermanAB said:**
> I let the clients do their own backup with rsync over the network, since I only have two laptops at home.  The server doesn't 'pull' it, but you could do the same, by letting the server connect to the client with ssh and then execute the backup script on the client. This keeps the majority of the processing load on the laptop and not on the dinky little Raspberry Pi.

Nobody has the "ideal" setup, only the best for our abilities and knowledge at the time.  Then over time we learn more and our skills expand.

In the 1990s, I'd ZIP files together and copy to a different disk.  Then I moved to using tar and gzip - tar retains the permissions.  But tar was designed for 50MB storage and really can't be scaled beyond 500MB. Think of tar as ZIP. Would you try to backup a system using ZIP?  Round 1996, I stopped using tar for backups.

Next was dump/restore.  These are built-into many Unix systems.  They are part of the weekly "full" and daily "incremental" backup method.  After a failure, the restore is a multi-step process.  Restore the most recent "Full", then each of the incremental backups in the correct order.  Some modern backup tools still working this way, like duplicity and the tools based on it like deja dup, duplicati, ...   Only used these for a few years.

Then I moved to rsync-based backups using hardlinks for versioning. There must be 20 tools that work this way.  rsnapshot, rbackup, 500 personal scripts, back-in-time, many, many more.  The issue with rsync-based versioned backups is that only the last permissions are stored.  Permission changes over time are very important for OS and application files.  As applications change, the permissions for the data files often become more secure.  If you just backup HOME directories, then this isn't often very important. I was "pushing" the backups from each client to the server.  I used that method until around 2009.

All the time this was happening, I was learning other things and code version control was something I started with in the 1980s.  This got me addicted to having simple access to different versions. rsync with hardlinks was handling it, but the storage used had to be Unix (not NTFS) to retain the last permissions.

Around 2008, our systems all switched over to being virtual machines.  Using rsync the backups were taking longer and longer. Soon we couldn't finish them all in the allowed overnight period.  I had to find a better solution and while I was at it, fix some other areas where the backups were lacking.  I looked at about 20 different backup tools.  duplicity checked all the boxes for being an amazing tool.  Unfortunately, my testing showed it was slow and on Windows, painfully slow was putting it nicely.  Over 8 hrs to backup 100GB?!!!  At the time, it wasn't ready.

rdiff-backup checked almost all the boxes, had a command line that looked like rsync, it was FAST - VERY FAST, and it retained file permissions with the versioning data. Testing showed that backups were like rsync the first time and 1-3 minutes for every backup after that.  The last backup is presented like an rsync mirror, which is wonderful.  Older versions are stored as gzip-diffs, so storage use is minor. Only changes.  This also explains why the backups are so very fast.  rdiff-backup and "push" or "pull" the backup data.  It works over ssh like rsync does, so all the normal ssh authentication and security works.  

 Plus a minor issue was always a hassle - scheduling when each client was allowed to "push" the backup to their assigned server without conflicts.

I started out using the "push" method, until I thought about security a little more.  Some of my systems are high risk. They  provide services over the internet and if someone is able to hack in and take control, escalate to root, then use ssh to connect to the backup server, all our data can be wiped.   Sure, something like crypto-locker wasn't likely to do that, but systems of all sorts are hacked every day.  Linux isn't immune.   By switching the "pull" backups, the authentication for backups can be locked down to just the backup servers which aren't on the internet-facing LAN.  More security that retains the capabilities is good. And the scheduling for each backup was removed.  The server would backup each client machine in turn.  

Then crypto-locker malware became "a thing".  I talked over the new attack vector with some admin friends and security professionals.  We call came to the realization.  "Pull" and versioned backups were the solution.  If a client gets encrypted files, the prior version will still be there, available for restore.  1 day of data loss. Plus the size of the backup would be huge, so the admin would notice that quickly.  I get daily reports about each system in my backup responsibilities.  An example:
```
=== Backups  spam2 === 
StartTime 1537510264.00 (Fri Sep 21 02:11:04 2018)
EndTime 1537510272.69 (Fri Sep 21 02:11:12 2018)
ElapsedTime 8.69 (8.69 seconds)
TotalDestinationSizeChange 1309 (1.28 KB)
```
That system doesn't have **any** data, it is just an email gateway.  9 sec to backup. Quite acceptable.  My desktop system takes a little longer.
```
=== Backups  lubuntu === 
StartTime 1537506906.00 (Fri Sep 21 01:15:06 2018)
EndTime 1537507183.25 (Fri Sep 21 01:19:43 2018)
ElapsedTime 277.25 (4 minutes 37.25 seconds)
TotalDestinationSizeChange 39783642 (37.9 MB)
```

All raspberry pi systems have limited I/O capabilities. All that I/O goes through a single USB2 controller ... so total, theoretical bandwidth is limited to 480Mbps.  Nobody ever gets that.  It is shared by all USB ports and the network port.  100Mbps is the ethernet and it does fill that. For storage I/O, USB2 is fast enough to stream hidef movies, but not really sufficient to backup TB of data commonly seen these days.  Even 100G will be painful, IMHO.

A Rock64 SBC or ODroid do have GigE networking and I think both support SATA/USB3 connections.  That changes everything.   The R-pi v3 claims to have a GigE network port, but it only achieves about 280Mbps due to the USB2 shared bus.

But if you don't have something better, **any** backup, even simple rsync mirrors without any versioning, are better than nothing. OTOH, rdiff-backup commands are almost the same as rsync and provide so much more capability.

And don't for get to use lvm snapshots when you are doing backups, so the services and system are still available to users.

---

### Post by HermanAB on 2018-09-21
Well, OK, my RPi is not the fastest server in the rack, but I just completed a backup of my Macbook Pro over WiFi:
sent 7277455383 bytes  received 11126374 bytes  3212952.06 bytes/sec
total size is 155625970265  speedup is 21.35

So, 3.2 Megabytes per second, which is good enough for a home user.

BTW, I agree that rdiff-backup is better than plain old rsync, but I nevertheless use rsync for home backups, since I don't care about the versioning and as O'l Albert Einstein said: 'A thing should be as simple as possible, but no simpler'.

---

### Post by SeijiSensei on 2018-09-21
Yes, it's a client/server architecture.  My very first office setup used Novell Netware over 10BaseT Ethernet.  It never seemed all that slow even back then.

> **webmiester said:**
> I tried this setup, but during our tests, the read write was really slow.

What kind of physical network do you have?  10BaseT? 100BaseT? 1000BaseT ("gigabit")?  Even on a 100BaseT network, or over my N wifi network at 54 Mbps, I can read and write files from my (NFS) server with only minimal delay.  I don't store anything on any client machine; all of them use shares from my Linux server (in my case it's running CentOS).  Most of the files I'm storing are documents of some kind from LibreOffice Calc and Writer.

I sometimes run Win7 in a VirtualBox VM and transfer files to and from the server using Samba.  Doesn't seem that slow to me.  

How many users are we talking about?

---

### Post by webmiester on 2018-09-24
Thanks everyone for the interest in this thread.

My network is a gigabit network for most of it.  There are a few switches that are 100Mbps only, but they dont connect ot computers that need to be backed up.  There are over 30 computers in the network but only 10 need backup since the other 30 are kiosks.

The computers that need backup are currently all Windows Computers.  The type of files that they use are just microsoft word files and/or excel files.  About 2 computers have pdf files as their output.  Only 1 computer has powerpoint files.  So despite having 10 computers, these 10 computers combined will not produce TB of files that need to be backed up.

I want to start by setting up a linux backup machine which will pull the files from the individual computers at specific times of the day.  My impression after reading your threads are this:  (Please correct me if I am wrong)

Since the linux machine (whether I use a Pentium or an RPi) will be the one to pull the files from the Windows machine, then it doesnt need to have SAMBA installed on the linux machine.  Without Samba, Windows wont be able to "see" the linux partitions.  If a cryptojacker comes to a Windows machine, its files may be copied by the linux machine and then archived but it wont get activated in the linux machine.  Since windows cannot see the lnux machine, then the malware cannot use Windows to transfer to the linux machine.  However, if I use the Windows machine to be the one to "push" its files to the linux backup machine, then I will need SAMBA, and that opens my files in the backup to this threat.

Is this concept right?

Eventually I want to move all my office users to a centralized NAS where they will all save their files.  Each user will have a separate LDAP partition running on SAMBA  Then another machine will be used for backup, this one wont have SAMBA and will pull the files out from each partition just like it does with the individual machines in the paragraph above.  

Im very new to this concept, and I am just learning.  Like what TheFu says, I will learn a lot more on the way.  So it's why I want to start first with the little machine that will do the backups first, then work my way to the NAS setup after :)

So going back to my question:  My impression is that if my linux machine doing the backup doesnt have Samba installed, then it will be theoretically safe from Windows based viruses and cryptojackers, right?  Does my impression make sense?  (Of course I also recognize that this is based on what we know as of the moment.  It might be possible in the future that someone develops a malware, or trojan horse that can overcome this setup).

---

### Post by webmiester on 2018-09-24
Additional ideas for security of the backup:

Ill run the backups using Cron so they will be regularly done.  But I will ensure that it will be run by a user and not root.

I want to close the iPtables of the backup machine right after the backup is made and only open the IP of the computer whose backup is being made at the time the backup should be done.  This is very doable but only if I use root to do the backup.=, since only root can manipulate the iptables.

Ill need to study ssh tunneling to the windows machines too, to see if I can do that as well.

---

### Post by TheFu on 2018-09-24
The extra detail helps a bunch.

ssh doesn't work to any of my Windows machines, so that isn't an option.

With the relatively small files involved, I would make all the files stored directly on a Linux machine.  No local files on Windows.  None. Setup samba with HOME directories per user.  There's a special section just for that. [Homes]
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 172.22.23.0/24
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```
Is an example of that section. Notice the restricted "hosts allow" aspects.  These are in addition to a Linux firewall configuration, not instead of.  If the Windows machines only write to Linux storage, that greatly simplifies backups.  You might want to use disk quotas to prevent abuse by end users.  They will think of network storage as "free" and endless if you don't.

On the Linux machine, be certain to setup LVM and use LVM snapshots as part of your backup method for the home directories and backup disk.  Use different LVs for each area.  You can take snapshots every hour of the day if you make enough room on the snapshot LV to hold all the change data.  They are instantaneous.  Then you can use rdiff-backup to perform the backup to other storage either local or on a different machine.  I'd go to a different machine as often as you like or as fast as the network supports. There are many reasons only to do this daily, not more often.
LVM Snapshot + rdiff-backup video: [https://www.youtube.com/watch?v=ng2mtVwoRtc](https://www.youtube.com/watch?v=ng2mtVwoRtc)  There are a few other videos around that episode for beginner LVM use and restoring from the backups.  The video makes it simple and explains things.

Or you can use **back-in-time** which uses rsync under-the-covers and what they call "snapshots", but those are really just rsync + hardlinks.  The default schedule is hourly and as time passes different backup sets are selectively deleted. It is kinda cool.  Last time I looked, back-in-time didn't work without having storage mounted, so that is a liability. rbackup/rsnapshot would be better from that standpoint.

LDAP is an authentication method, not a partitioning method. I've not used Samba4 as a Windows Domain controller, but you might want to look into that.

Interesting problem.

---

### Post by webmiester on 2018-09-25
> **TheFu said:**
> 
LDAP is an authentication method, not a partitioning method. I've not used Samba4 as a Windows Domain controller, but you might want to look into that.

Interesting problem.

Thanks TheFU.  Eventually I want everyone to write to a linux machine directly...  About partitioning vs authentication method...

How about if I make multiple partitions, one partition per user, and I restrict a user's access to a particular partition only (LDAP maybe)?  Will that be able to contain the damage which a cryptojacker will bring?

Just for fun...

Since the Rpi 3+ is a little slow for an NAS... How about this machine?  It runs on Intel ATOM, and it also has a Gigabit ethernet.  Perhaps we can plug in hard disks through its USB slots considering it has USB 3.0 slots:  It can run ubuntu through USB, as seen on the video.

[https://www.youtube.com/watch?v=Q4nYlLkX0YE](https://www.youtube.com/watch?v=Q4nYlLkX0YE)

Im also wondering if its is possible to RDP into the Windows 10 of this device using renmina on ubuntu...  but I suppose this is out of place for this forums, but just in case someone has experience with such a device and the free Windows 10 it comes in, I suppose it will do no harm to share my question here too.

Thanks

---

### Post by TheFu on 2018-09-25
USB3 is fine for backups, but not for primary storage, IMHO.  I've seen USB connections come loose over the years.  For any external storage, look for a connector that has screws.

I saw a  Core i3 + motherboard new on Slickdeals yesterday for $115.  That is the sort of machine I'd use for a NAS. I avoid Atom CPUs. Been burned and there have been some issues with some models. Backups should require encryption. As encryption standards change, HW support won't be built-into the CPU. That means SW encryption will be necessary, which isn't good on slow, Atom CPUs.

I know nothing about Win10 except what I see here.  CIFS defaults have changed and RDP seems to work better between Windows systems but not so good between Linux and Windows.

---

### Post by slickymaster on 2018-09-25
*Thread moved to **Server Platforms**.*

---

### Post by webmiester on 2018-09-26
> **TheFu said:**
> USB3 is fine for backups, but not for primary storage, IMHO.  I've seen USB connections come loose over the years.  For any external storage, look for a connector that has screws.

I saw a  Core i3 + motherboard new on Slickdeals yesterday for $115.  That is the sort of machine I'd use for a NAS. I avoid Atom CPUs. Been burned and there have been some issues with some models. Backups should require encryption. As encryption standards change, HW support won't be built-into the CPU. That means SW encryption will be necessary, which isn't good on slow, Atom CPUs.

I know nothing about Win10 except what I see here.  CIFS defaults have changed and RDP seems to work better between Windows systems but not so good between Linux and Windows.

Well actually I dont know much about Windows 10 too, but the video shows that it is possible to run Ubuntu on this device through its hidden USB port.

---

### Post by webmiester on 2018-09-26
> **TheFu said:**
> The extra detail helps a bunch.

ssh doesn't work to any of my Windows machines, so that isn't an option.

With the relatively small files involved, I would make all the files stored directly on a Linux machine.  No local files on Windows.  None. Setup samba with HOME directories per user.  There's a special section just for that. [Homes]
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 172.22.23.0/24
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```
Is an example of that section. Notice the restricted "hosts allow" aspects.  These are in addition to a Linux firewall configuration, not instead of.  If the Windows machines only write to Linux storage, that greatly simplifies backups.  You might want to use disk quotas to prevent abuse by end users.  They will think of network storage as "free" and endless if you don't.

On the Linux machine, be certain to setup LVM and use LVM snapshots as part of your backup method for the home directories and backup disk.  Use different LVs for each area.  You can take snapshots every hour of the day if you make enough room on the snapshot LV to hold all the change data.  They are instantaneous.  Then you can use rdiff-backup to perform the backup to other storage either local or on a different machine.  I'd go to a different machine as often as you like or as fast as the network supports. There are many reasons only to do this daily, not more often.
LVM Snapshot + rdiff-backup video: [https://www.youtube.com/watch?v=ng2mtVwoRtc](https://www.youtube.com/watch?v=ng2mtVwoRtc)  There are a few other videos around that episode for beginner LVM use and restoring from the backups.  The video makes it simple and explains things.

Or you can use **back-in-time** which uses rsync under-the-covers and what they call "snapshots", but those are really just rsync + hardlinks.  The default schedule is hourly and as time passes different backup sets are selectively deleted. It is kinda cool.  Last time I looked, back-in-time didn't work without having storage mounted, so that is a liability. rbackup/rsnapshot would be better from that standpoint.

LDAP is an authentication method, not a partitioning method. I've not used Samba4 as a Windows Domain controller, but you might want to look into that.

Interesting problem.

This might be a simpler solution.  I have an old storage server here which probably has just a 100MBPs LAN port.  When I tested it as a primary hard disk for the other computers, it was really really slow.  So that is why I am thinking of just using it as backup...  But come to think of it, it might just be that my setup wasnt quite mature yet and I need to retry it again as a primary NAS.  I really like th script you gave me and Ill have to study how to use it.  With the LVM backups, I wont need to have the rsync and all.

---

### Post by webmiester on 2018-09-26
> **webmiester said:**
> 
So going back to my question:  My impression is that if my linux machine doing the backup doesnt have Samba installed, then it will be theoretically safe from Windows based viruses and cryptojackers, right?  Does my impression make sense?  (Of course I also recognize that this is based on what we know as of the moment.  It might be possible in the future that someone develops a malware, or trojan horse that can overcome this setup).

Ive been doing a bit of reading on this and it seems that I still need to install SAMBA so that the ubuntu system can see the windows computer.  I was hoping it would be like a local hdd with a windows and linux partition.  In the local setup, I can easily mount the windows drive so I can see the windows files but windows cannot see my linux files.

---

### Post by mastablasta on 2018-09-26
why does linux NAS needs to see windows computers? you can just push backups from windows PC to Linux NAS via SSH using a backup client (GUI) or script.

---

### Post by TheFu on 2018-09-26
LVM isn't a backup. It is a tool to quiesce the storage before you do a backup. This ensures a few things.
a) consistent backup data
b) zero downtime for the services, snapshots allow this.

A real backup tool is needed. Watch those 3 videos about using LVM and rdiff-backup. You'll thank me.

---

### Post by SeijiSensei on 2018-09-26
> **webmiester said:**
> Ive been doing a bit of reading on this and it seems that I still need to install SAMBA so that the ubuntu system can see the windows computer.  I was hoping it would be like a local hdd with a windows and linux partition.  In the local setup, I can easily mount the windows drive so I can see the windows files but windows cannot see my linux files.

Install the smbclient package on the server if it's not already present.  It should be able to see the Windows shares and transfer the files to the server. For full details, see its [man page]("https://linux.die.net/man/1/smbclient").

You would need to incorporate this into a script to poll each machine and do the transfers.

---

### Post by TheFu on 2018-09-26
There are 4 different cooks in this kitchen, each trying to make a different type of soup.  There are important differences in each of the recipes.  They will all work, but there are subtle differences in the security aspects.

---

### Post by webmiester on 2018-09-27
> **TheFu said:**
> There are 4 different cooks in this kitchen, each trying to make a different type of soup.  There are important differences in each of the recipes.  They will all work, but there are subtle differences in the security aspects.

Thank you so much.  Yeah, I have to figure out which soup I like most

---

