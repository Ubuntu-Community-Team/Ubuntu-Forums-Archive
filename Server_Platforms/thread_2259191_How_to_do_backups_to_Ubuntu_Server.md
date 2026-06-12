---
title: "How to do backups to Ubuntu Server?"
date: 2015-01-02
forum: Server Platforms
---

### Post by josh111 on 2015-01-02
Hi! I was wondering how I could backup my Windows 8.1 to my home server which is running Ubuntu Server. It would be nice if the program wouldn't interfere with Samba and Nginx as I use those programs on Ubuntu Server. Thanks a bunch in advance!

---

### Post by sandyd on 2015-01-02
You can do backups by using duplicati ([http://www.duplicati.com/](http://www.duplicati.com/))

First, create a user account where the backups will be stored.
You can do this by running
```

sudo useradd -m backupuser
```

Second, create  SSH key on Windows using Putty (See [https://code.google.com/p/duplicati/issues/detail?id=952](https://code.google.com/p/duplicati/issues/detail?id=952))

Add the SSH Key to the Linux host, and you should be in business.

Edit:

Some more options:
- Crashplan (Install crashplan on server, [plenty of guides do do this]("http://support.code42.com/CrashPlan/Latest/Configuring/Configuring_A_Headless_Client"), and crashplan on the windows computer)
- BackupPC
- Bacula/AMANDA (Side note, very complicated)
- Syncthing with backup enabled on server side

---

### Post by josh111 on 2015-01-02
> **sandyd said:**
> You can do backups by using duplicati ([http://www.duplicati.com/](http://www.duplicati.com/))

First, create a user account where the backups will be stored.
You can do this by running
```

sudo useradd -m backupuser
```

Second, create  SSH key on Windows using Putty (See [https://code.google.com/p/duplicati/issues/detail?id=952](https://code.google.com/p/duplicati/issues/detail?id=952))

Add the SSH Key to the Linux host, and you should be in business.

And that will not interfere with my Samba and Apache Web Server?

---

### Post by MAFoElffen on 2015-01-02
Samba (SMB over TCP) listens on port 445.
Apache listens on ports 443 and 80.
SSH listens on port 22.

---

### Post by TheFu on 2015-01-04
There must be 50-500 different answers for this question.

Anytime server resources are used, they interfere with other requests on the same server - networking, disk, CPU, RAM. You can minimize any issues by doing backups when the systems aren't in heavy use for other reasons.  Backups tend to load the network and disk-IO. Plan on that and you'll be happier.

Windows has lots of backup tools - most commercial ones understand how to write to CIFS shares ... i.e. samba shares in Linux terms.  There are also free backup tools - like Bacula which use their own client/server protocols.  Of course, if your Windows version is Professional or higher, you can use the built-in backup too to write to a "network drive" ... though under Win7, I've had extreme issues attempting to restore later.  Seems the Windows restore process demands the share be mounted in an exact location regardless of where it was during backup. [http://www.howtogeek.com/189452/8-backup-tools-explained-for-windows-7-and-8/](http://www.howtogeek.com/189452/8-backup-tools-explained-for-windows-7-and-8/) has a few options. [http://pcsupport.about.com/od/backup/tp/free-backup-software.htm](http://pcsupport.about.com/od/backup/tp/free-backup-software.htm) has some more and was updated this week.

If you stay with cross-platform and free tools, sandyd's option is probably good.  However, I tested duplicati 3 years ago and found it to be extremely, extremely, extremely slow. Perhaps things are better now?

You can also do like I do on Windows and create highly manual quarterly backup images for the OS and nightly diff backups for data files (not OS or applications).  To make the images, I boot off a liveCD/flash drive for Linux loaded with tools.  fsarchive, partimage, clonezilla are all popular for this and compress the image. Each are a bit-for-bit copy.  
Data backups can be handled by rdiff-backup, rsync, xcopy, robocopy, or any other file copy routine.  Because only data that changes is copied nightly, these are fast - usually less than 2 minutes.  I keep data on Windows to a minimum, most is only working files. Preferring using Linux storage for completed projects and long term storage. I'm more comfortable with that, but not everyone is.

---

### Post by MAFoElffen on 2015-01-04
Like FU said, this could be to any personal preference... and to the business requirements.

I'm still playing with this. I use cron triggered Scripts > which use ssh (with certs) to go to my servers and to the SMB and NFS shares server... LVM, so do temp snaphots > compress using TAR > then write the backups to SMB share on Backup server > then copy of that written to tape. Tape drive is off my Backup server on a subnet of it's own.

Not sure this is best for me yet, but still working that out. I've thought maybe of plumbing those servers on a dedicated subnet, straight to that backup server, just for this purpose... but haven't worked that out yet.

---

### Post by mastablasta on 2015-01-05
still testing. using Areca - but i am not sure why it writes some files and what kind of files it writes to local disk. I checked the documentation but couldn't find what is being written.

luckybackup also has Windows version, but it doesn't start in Windows propperly. at the moment i am using OwnCloud but this is not a good backup solution. it is mostly good for sharing. so i can share pictures and videos only with with faimily members. 

i will now give duplicati a try as well. i checked the screenshots and it seems easy enough to use.

---

### Post by ted.drain on 2015-01-05
I did a lot of research on backing up my Windows machines when I built my Ubuntu home server and settled on UrBackup.  I've been very pleased with it.

[http://www.urbackup.org/](http://www.urbackup.org/)

---

### Post by mastablasta on 2015-01-06
so i tried Duplicati - same quesiton as with Areca - what does it do with temp folder on local disk? does it compress the file first and then transfer the backup? also based on Microsoft .net framework  :-) otherwise it seems to be working fine.

hmm it seems i need to try urbackup next. client seems simple. does it support SSH backups? it looks very interesting as you can control to a degree the clients on the network via web browser.

---

### Post by ted.drain on 2015-01-06
> **mastablasta said:**
> 
hmm it seems i need to try urbackup next. client seems simple. does it support SSH backups? it looks very interesting as you can control to a degree the clients on the network via web browser.

See page 10: [http://www.urbackup.org/ServerAdminGuide-v1.4.pdf](http://www.urbackup.org/ServerAdminGuide-v1.4.pdf)

TL&DR: for local area backups, data is in the clear.  for internet backups, transmitted data is encrypted.

One of the things I like the best about it is it's use of hard links for files that didn't change in an incremental backups.  It makes every incremental backup look like a full backup so it's really easy to recover files just by copying them out of a directory.

---

### Post by scott.bouch on 2015-01-06
This is an interesting topic,

Just last week me and a friend in our village were discussing backing up each others data on a nightly basis across the internet... so that our backups are geographically seperated in case of house fire, flood, theft etc...

 What I've just read here makes it appear quite viable, however, he just has a NAS, albeit a clever one that hosts websites and a media server...

A project for another day though... Cheers, Scott

---

### Post by TheFu on 2015-01-06
> **scott.bouch said:**
>  What I've just read here makes it appear quite viable, however, he just has a NAS, albeit a clever one that hosts websites and a media server...

I do this with a friend:
Nightly backups to an internal backup server using rdiff-backup. It is the preferred backup tool here.
Then those systems are backed up to a business partner's backup system about 30 miles away using rsync. We both run Linux and encrypted storage for which only we have the key. I cannot unlock his storage and he cannot unlock mine.

Why?
* local backups are faster to restore. There are times when that is needed. Remote data is a hassle to get back.
* rdiff-backup doesn't use hardlinks, which would case issues for rsync, but it is more efficient in storage use than hardlink+rsync solutions.
* rdiff-backup makes the last backup appear as a mirror, which is highly, highly convenient.
* encrypted storage on the other end means I don't see his stuff and he doesn't see mine. I don't want to know what he backs up. Suspect it is mostly wedding videos and baby photos. ;)
* pre-seeding the first backup is trivial with a local rsync.  Less than 100MB is transferred nightly each way though we have 500G of backup data each.
* This is not used for media stuff except priceless personal things and business server data.

**Duplicity** might be easier, since it has both encrypted storage and encrypted transport, I just don't like the way they store the backup data. It is more like how enterprise backup systems do it in equal sized chunk files. Ugly, IMHO.  There is much to be said for backups looking like normal storage when it is time to recover.

---

### Post by mastablasta on 2015-01-07
> **ted.drain said:**
> 
TL&DR: for local area backups, data is in the clear.  for internet backups, transmitted data is encrypted.


transmited data is encrypted, there is a password, but no keys it seems. it doesn't use ssh. hmm... I wonder how strong is the encryption. it does use it's own server. I only installed the client to see how it looks like yesterday. I will need more time to also setup the server and then give it a god. it definitely seem interesting and preety easy to setup.

> **TheFu said:**
> 
**Duplicity** might be easier, since it has both encrypted storage and encrypted transport, I just don't like the way they store the backup data. It is more like how enterprise backup systems do it in equal sized chunk files. Ugly, IMHO.  There is much to be said for backups looking like normal storage when it is time to recover.

the recovery part is something we forgot to worry about when testing backups :-)

I am still not sure why owncloud doesn't have one way sync... or did I miss it somewhere?!

so does anyone know why these backup programs need temporary disk space on local PC? is it because they compress data there first before upload? I am fine with that but I would need to know how much free disk space should I leave for backup then.

---

### Post by TheFu on 2015-01-07
> **mastablasta said:**
> so does anyone know why these backup programs need temporary disk space on local PC? is it because they compress data there first before upload? I am fine with that but I would need to know how much free disk space should I leave for backup then.

I have no idea what you are talking about.  I've never worried about temporary space for backups on the system being backed up.  The librsync-based tools may need a little in /tmp, but it isn't much, if any at all.

OTOH, I've never used any GUI backup tool. After, running a GUI from cron doesn't work, so why would I bother?

BTW .... happiness is seeing something like this every day for about 30 difference systems ... 
```
=== Backing up  lubuntu === 
StartTime 1420614206.00 (Wed Jan  7 02:03:26 2015)
EndTime 1420614405.19 (Wed Jan  7 02:06:45 2015)
ElapsedTime 199.19 (3 minutes 19.19 seconds)
TotalDestinationSizeChange 39481339 (37.7 MB)


=== Backing up  xen41 === 
StartTime 1420617015.00 (Wed Jan  7 02:50:15 2015)
EndTime 1420617050.83 (Wed Jan  7 02:50:50 2015)
ElapsedTime 35.83 (35.83 seconds)
TotalDestinationSizeChange 4705318 (4.49 MB)


=== Backing up  c720 === 
StartTime 1420618387.00 (Wed Jan  7 03:13:07 2015)
EndTime 1420618450.06 (Wed Jan  7 03:14:10 2015)
ElapsedTime 63.06 (1 minute 3.06 seconds)
TotalDestinationSizeChange 35712604 (34.1 MB)

```
See the elapsed times? Jealous?  Above are 2 desktops and 1 blog server.  Some servers are 11 seconds and other are 4 minutes. Most don't change that much - like a project management server (about 30 sec).

---

### Post by mastablasta on 2015-01-07
elapsed backup times depend on changes made as well :P

GUI like Duplicati or Areca both do some *temp* writing and what I can't figure out is exactly what they are writing there. Last time it looked like it was the files being backed up. 

And an update on UrBackup after doing some RTFM - it doesn't use SSH but it does use encrypted file transfer where data is encrypted via password as well as with key.

GUI is a must if people that are not so computer literate and for example want to do change what is being backed up or when. let's say if they wanted to add a new folder to the backup. this is usually easily done with a GUI. and anyone that knows a little bit about computer can do it. while doing rsync command or rdiff might prove too challenging. for starters you need to read the manual first. 

UrBackup has interesting feature where server can push setup changes to clients.

---

### Post by mastablasta on 2015-01-12
Goal: backup solution with safe data transfer (certain data transfered over internet), versioning (weekly backup) and no encrpytion possibility running on windows as well as linux with an easy to use GUI 
client. 

Owncloud client - forget about it as backup eventhough it has versions. But server is very good for sharing and showing the family photos to a selected few. i will do another test with version but it seems 
there is no way to use client for one direciton sync (PC->Server).

UrBackup - ended up not testing it - i was afraid about what it would mean to add all those extra threads. It's basically a pull solution that would probably work even over the internet. Those using it - 
how are the speeds comapred to other options? Otherwise client is easy to setup. i read the server guide and server seems also easy to setup. could someone that is using this explain a bit about the server 
load? as i undertsand it constantly ping clients, checks out if they are on or not etc. 

Areca - i tested the non compressed backup. it's fast, data stays as it is. pictures are pictures. If file changes new version is uploaded in new folder marked with date and number. If file is deleted the 
info is saved in another file. it's easy to setup and i found out theat the temp folder can be selected working folder. the programs has a wizzard that will help to set up scripts or batch files per your 
instructions, these are then added in task scheduler or crontab on linux. scripts have comment sections added per command line which is a nice touch (make it easy to setup via wizzard then modify if 
needed). runs on java. uses SSH (or rather sFTP) to transfer files. client is easy to setup. 

Duplicati - client is super easy to setup. New version runs a localhost to setup in browser. this part i find tad bit strange. however both old and new are easy to setup. they can transfer via WebDAV to 
various clouds (S3, owncloud...). New version has a new method for file transfer and backup. reading some proposals and background it appears this is actually a kind of GUI for rdiff. And her eis a 
challenge for TheFu as google offered one of his excelent articles on comparison between the two but it was on older version. Perhaps it is time to run another test with latest version used? :P anyway it will encrypt the data. but the issues i have with this solution is that files are always zipped. so while you can transfer you family photos directly into your owncloud setup, forget about being bale to simply share them. they are zipped. furthermore the new method devides it all (or at leats larger files) into blocks. hmm... but you can backup to owncloud and i would certainly use this one instead of Owncloud client if i wanted to share backups.

2 more i plan to try out but need to read the documentations first to see if they fit the goal. and that is FreeFileSync and CreateDuplicity.

The thing that puzzled me a bit - Everyone is offering this WebDAV as the next best thing after FTP, but user experience seem to show that transfer via WebDAV is significantly slower than the old FTP transfer 
when doing big files transfer. So while WebDAV is easier to use is it also faster or as fast as FTP? a HD cam movie can quickly go into GB file size... they probably might not need versioning for most users just automated fast transfer to server. rdiff has a limit on file size (at least on windows). but still works well for smaller files such as documents and such.

---

### Post by TheFu on 2015-01-12
WebDAV has many problems. These make it unsuitable for consideration as a backup target, at least to me.  
The main issue? There is a long history of security failures in WebDAV server and clients.

I'm not likely to look at duplicati again, sorry. Back then I was looking for a solid backup solution. In the end, I've decided to use fsarchive for Windows images and to keep all important data on Linux systems.  I had hoped to use the build-in backup tool, actually trusted it for about a year, but when it came time to restore, that failed (in my mind).  It was probably just my UNIX-head getting in the way of things. Sometimes knowing too much is detrimental to using Microsoft tools.  Yes, I tried just clicking next, next, next ... that didn't work either.

Plus a friend is a core developer for duplicity. Saw him yesterday and pointed out my issues getting it to work.

GUI for backup tools do not interest me at all. Sorry.  Desktops are throw-away for me. It is the servers that matter. Servers don't have a GUI.

There is a nice comparison of Ubuntu backup tools here: [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)  I've tried 7 of these. rdiff-backup is my choice.  BTW, rdiff is different from rdiff-backup.

---

