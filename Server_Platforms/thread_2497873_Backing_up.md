---
title: "Backing up"
date: 2024-05-21
forum: Server Platforms
---

### Post by tonyr55 on 2024-05-21
Hi everyone hope all OK.
Im still very new to Linux still finding my way around all the commands mine field lol.
I Wanted to ask because I haven't got a clue. 
I got my ubuntu server up and running ,mounted hard drives and folder will terminal only no gui.
What I'm after is backing up my windows pc and ubuntu laptop to the ubuntu server.
But I can't find out how you go about it.
Had a look on Google and you tube,
But all I can seem to find is how to back up the server which I not ready to do yet.
So  can I backup my Windows pc to my ubuntu server.
If so how do I go about it please. 
Best regards tony

---

### Post by currentshaft on 2024-05-21
Lots of ways to go about it.

You could connect the other computer's hard drive and mount it on your Ubuntu server. This is probably the least convenient or even impossible if you don't host the server in the same location.

You could transfer the files with a network sharing protocol like NFS or Samba. That sometimes requires additional software and probably more suited to a shared network environment with many users.

Personally I would use rsync over SSH, provided your network is capable of handling the network traffic. This gives you strong security and a reliable file syncing mechanism.

---

### Post by aljames2 on 2024-05-21
You are at the point of defining your backup scheme, some very important decisions you are about to make.

When I got to your point, Ubuntu Server, I took a month and read a lot of information on backup concepts, when and how to use them.  If you don't have a backup of anything at the moment, perhaps plugging in a USB drive and rsync'ing, or simply copying your important files off of those systems would be a good start while you really figure out what scheme you want to deploy.  Get clear on what you want to back up.

Depending on what you are trying to back up can dictate the tools you should consider.  For example, static docs vs. system files.  Also, where are the hosts physically located, are they on your LAN or in Maryland somewhere.  I stayed away from RAID to start with.  RAID does not create a backup and it adds complexity that I wasn't ready to handle.  More importantly, RAID is not backup solution.  Also snapshots are not typically backups either, but more of an in-between step, or tool used to create the actual backup.

I landed on using rdiff-backup for backing up system files because of it's versioning. I prefer to not back up entire operating systems, instead only the files that I would need to restore configurations after a fresh install.  I like rsync for creating an extra copy of static files (not live systems).

There is also the concept of "push" and "pull" backups.  If your Ubuntu server is your backup server, you will want to learn how to pull backup data off your source hosts, to your backup server.  Not best to allow other hosts to access your backup server.  Would you want an unpatched "W" box to have access to your sacred backup pools, likely not.

Search these forums for posts by @TheFu, with backup keywords.

---

### Post by tonyr55 on 2024-05-22
Ok had a go with rsync over ssh.
Can't get past error messages lol.
Had I play with winscp and that works ok able to back up my windows pc to Ubuntu server. 
Winscp not what I really wanted 
So will try  playing with rsync again.
I do have all my important files stored on 2 external hdds.
Backing up to my server was just something I'm interested in doing hehe

---

### Post by TheFu on 2024-05-22
Backups are an exercise in trade-offs between ease of running, ease of restoring, time to run, and storage to be used.  Only you can choose the relative priorities for each of those things.  

I'm with aljames2 on my backup methods.  For me, daily, versioned, backups were a requirement.  Initially, I was doing local copies, just to a different disk.  Then slowly I moved to "push" backups over the network and after seeing all the malware and crypto-ware problems that versioned backups could protect against, I switched to "pull" backups. The client system don't have any access at all to the backup storage on the server.  

If they did, then malware could corrupt all the versioned backups, which defeats the purpose.  That also mean that using network storage is a bad idea for backup storage, so don't use CIFS or NFS mounted storage.  Choose tools that use a non-storage client/server architecture.

In the profession, we start by asking a few questions - what are the RPO and RTO requirements?  
[LIST]
[*][https://en.wikipedia.org/wiki/Recovery_point_objective](https://en.wikipedia.org/wiki/Recovery_point_objective)  - How old can the data be?
[*][https://en.wikipedia.org/wiki/Recovery_Time_Objective](https://en.wikipedia.org/wiki/Recovery_Time_Objective) - how long should recovery take?
[/LIST]

Answering those questions will determine how much money needs to be spent and the complexity of the backup methods.  

Typically, backups once a day are just as cheap as once a week or once a month, so there's little reason to do anything besides daily backups.

For my needs, my RTO was 1 hour for core capabilities.  So, my recovery process needs to take less than 1 hour until the system is back up and working with the most important capabilities.  Any computer here with less than 100GB of data can be restored from scratch in less than 1 hour.  It won't be exactly the same, since _I don't backup everything_, but it will work the same.  Because I use snapshots, sometimes I can restore from logical issues in just a few minutes.  LVM and ZFS snapshots are extremely powerful, but those have to be setup BEFORE they are needed and most often, they need to be selected during the OS install. There's no way to go back and add them post-install.

If you are new, it is likely that "pull" backups are beyond your ability.  So, start with what you can wrap your head around and plan to move to "pulled" backups perhaps in 6-12 months after you have more understanding.

Some links to get you started:
[LIST]
[*][Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)
[*][https://ubuntuforums.org/showthread.php?t=2456011&p=14011294#post14011294](https://ubuntuforums.org/showthread.php?t=2456011&p=14011294#post14011294) - is slightly older and I'm trying to talk someone out of doing image-based backups, which are slow and wasteful.
[*][https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html) - save that link. It is the basis for LVM snapshots used in a backup process.  Backups that don't use some file-system-based snapshot are prone to file corruption if the files are being written at the instance a backup copy is taken.  Most of the time, this would happen only for log files or active DBMS, but it can happen for other types of data too.
[/LIST]

An important point of consideration is exactly how much trouble are you willing to have at restore time.  1-click restores waste 100x more storage, so they aren't really viable for an entire system.  Remember why we are doing backups - it is 10% backups and 90% about restoring files, so be certain you test the restore or you'll never know whether it actually works or not.  When I was first creating my new backup techniques (around 2010), it took me 5 attempts before I solved all the chicken-egg issues and had enough practice doing the restore process that for most systems here, a restore takes less than 30 minutes.  It is only systems with lots and lots of data that take more.  I have a 2 systems with over 20TB of data ... just copying the backup data to new HDDs (assuming I had those HDDs available) would take about 3 days.  However, the core services those 2 computers provide can be up and working in about 45 minutes, just without all that data, 

What do they say?  Begin with the end in mind.

Just so you don't think TB and TB of data are needed for every versioned backup.  Here's the massively cut version of my email gateway server backups:
```
# rdiff-backup --list-increment-sizes spam2
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed May 22 00:03:28 2024         3.90 MB           3.90 MB   (current mirror)
Tue May 21 00:03:21 2024         2.95 KB           3.90 MB
Mon May 20 00:03:29 2024         1.60 KB           3.91 MB
....
Thu May 25 00:03:19 2023         14.0 KB           4.43 MB
Wed May 24 00:03:17 2023         1.27 KB           4.43 MB
Tue May 23 00:03:15 2023         1.25 KB           4.43 MB

```
I keep 1 yr of daily backups because it is a high risk system.  But it doesn't have any data on it and it uses extremely standard tools. The backups are really just a list of installed packages and configuration files for those packages.  Less than 4.5MB of storage to have 1 yr of backups?  Seems like a bargain to me.  

Of course, other systems need more storage and I don't keep as many versions.  Here's my desktop computer:
```
# rdiff-backup --list-increment-sizes deneb
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed May 22 00:07:48 2024         11.4 GB           11.4 GB   (current mirror)
Tue May 21 00:11:32 2024          257 MB           11.6 GB
Mon May 20 00:06:43 2024         13.7 MB           11.6 GB
Sun May 19 00:07:20 2024         1.72 MB           11.6 GB
...
Thu Jan 25 00:05:37 2024         1.44 MB           15.8 GB
Wed Jan 24 00:05:46 2024          147 KB           15.8 GB
Tue Jan 23 00:07:02 2024          209 MB           16.0 GB
```
I have just 120 days of versioned backups for it.  16GB for a desktop. Seems like a bargain to me.  Of course, most of the data that desktop uses is on network storage accessible via NFS.  Locally, I only have active files for current programming and presentations.  Reference materials are on the network storage.

And the time needed to backup each system daily is important, just like the total storage used. I get a daily report for each system:
```
=== Time for Backups to spam2 === 
StartTime 1716350608.00 (Wed May 22 00:03:28 2024)
EndTime 1716350613.77 (Wed May 22 00:03:33 2024)
ElapsedTime 5.77 (**5.77 seconds**)
TotalDestinationSizeChange 10344 (10.1 KB)

=== Time for Backups to deneb === 
StartTime 1716350868.00 (Wed May 22 00:07:48 2024)
EndTime 1716351017.72 (Wed May 22 00:10:17 2024)
ElapsedTime 149.72 (**2 minutes 29.72 seconds**)
TotalDestinationSizeChange 252629230 (241 MB)

```
My daily backups take less than 45 minutes total across all systems here.  Before I switched to rdiff-backup, I needed over 8 hrs every night to backup the systems and didn't have storage to keep so many versions. I was using rsync.  Before that, I was using image-based backups and before that I was hoping that I wouldn't need any backups, ever.  Hope is never a plan.

---

### Post by Kyle142 on 2024-05-24
Lots of different options, If it's at home I'd personally use samba.

---

### Post by ajgreeny on 2024-05-25
Moved to Served Platforms which is more appropriate.

---

### Post by TheFu on 2024-05-25
> **Kyle142 said:**
> Lots of different options, If it's at home I'd personally use samba.

All network file systems have a huge liability when used for backups.  If any of the client machines gets malware or crypto-ware, then the backups will be searched out and destroyed too.  This is why a client-server backup tool needs to be used AND why backups need to be "pulled" by the server, not "pushed" by each client.  Just think of all the people and businesses that have died due to using network file systems or "push" backups that were taken out by the malware.  We hear about 0.001% of the impacted businesses.  Many smaller businesses are killed when malware takes them out and gets their backups too.

But when just starting, some backups, even to a portable, external, USB is better than nothing.  The most important aspects are that it isn't just the data, but also the owner, group, permissions, ACLs and xattrs that must be retained on a multi-user system.  Linux is **always** multi-user, even if only 1 person uses the box.  Almost all Linux backup tools (there are exceptions), expect the target backup storage to hold the owner, group, permissions, ACLs, and xattrs.  rsync does.  Without that data, we only have 50% of what is needed in a backup. The data alone isn't sufficient and in many situations, restoring the data alone, without the other correct metadata won't work.

The duplicity-based tools keep that file metadata separate from the file system. This is why those tools (duplicity, duplicati, deja dup) don't care what the target backup storage file system is.  ALL OTHER backup tools expect a Linux/Unix file system to hold the extra metadata. Some don't handle versioning of the metadata, which can be a total failure as well.  rsync is one of those.  Tools that use rsync + hardlinks for versioning also only retain the last file metadata, not all the prior versions.  rdiff-backup handles all the versioning - AND it is faster than rsync while providing efficient versioning.  

**Anyone using _rsync_ as a backup really needs to switch to _rdiff-backup_.  The command options are very similar.  **  There's a reason so many people choose it in these forums. I've already linked to simple examples.

Duplicity does check all the boxes for what an ideal backup tool should do, however, it requires a new full backup every month.  It follows the style of backup tools like dump/restore and tar from 1970.  I suppose it is proven, but there are lots of people in these forums who end up with corrupted duplicity/deja dup backups. I can only guess it is because they didn't see the instructions that clearly say a fresh, full, backup is necessary monthly.  rdiff-backup works different.  

The most recent backup is the "master" and older versions are diffs off each other. After the first backup, there's no need to make another "full" again.  What is required is to remove the oldest versions and realize that intermediate versions must be retained, or all older versions won't work.

Feels like I say the same things every 6 months to someone trying to setup server backups in these forums.  For GUI users, rdiff-backup can be a challenge. There's no GUI.  OTOH, GUIs don't automate well and one of the keys to backups is having them be 100% automatic. We humans are lazy.  

Even I, with a fully working backup script, didn't initially have it run automatically.  Through some amazing luck, I happened to run it 1 week before someone cracked into a server.  It was dumb luck.  With the backups, I was able to figure out what they did, remove all their bad software and didn't even reboot the system, much less reload it.  That was long before I got backup religion.  Today, almost any problem with data is a minor inconvenience, thanks to automatic, daily, versioned, backups, across all my systems (about 15 of them).  With all those computers and all that storage, something bad happens about once a year - HDDs fail. That's their goal in life.

It isn't just hardware failures.  Corrupt files happen to.  Once a database file got corrupted, but I didn't notice it for over a month.  Fortunately, I had 90 days of daily backups.  Of course, I restored the most recent backup. When that didn't work, I tried the next day, then the next, then a week old, then 2 weeks, 3 weeks, 4 weeks, .... eventually, I found that the backup from 37 days prior wasn't corrupted.  Because the DB was seldom used, but important, no data was actually lost after restoring.

So, when you plan your backups, those are some things to consider.

---

