---
title: "best way to backup/secure data on remote root server"
date: 2015-03-24
forum: Server Platforms
---

### Post by fritz7 on 2015-03-24
Hello guys,

I'm searching for "the best backup solution" for a remote server.

I have an root server somewhere with an simple owncloud, mail server and git repository installation. At home I have an old PC also running with ubuntu server which has 3TB of raid 1 storage. My goal is to save/backup the remote server(230GB) from time to time because I fear that sometime data can be lost cause of misconfiguration or updates.

I found a lot off solutions:
[LIST]
[*]rsync - could be started on the remote or the local server an sync the whole server as root(security?) but here is the problem that I only have one copy of my data and it will be lost if I misconfigure something and delete stuff and the sync is started before I recognize. also making copys for every day of the week is not that secure if it needs me more than 7 days to recognize a failor
[*]deja-dump - looks very nice cause it has incremental backups(low amount of storage needed localy) but I think it won't work on the server cause it's a gui program
[*]dd - make image of remote server and download it ... downside is the high amount of wasted storage
[*]tar - same as dd but with less storage wasted
[/LIST]

but none of them realy suits my needs - are there any other solutions? I would prefer something like deja-dump cause it can make incremental backups.


Another think I thought of is the problem that the server is running while I want to make the backup. Are there things which could make troubles cause of that? I think here of files Channing while the backup is running, could this result in corrupted files?

---

### Post by papibe on 2015-03-24
Hi fritz7.

A few thoughts.

What do you want to backup? For Instance, 
[LIST]
[*]You want to backup your data so that a disaster happens you won't loose your pics, docs, etc. However, getting up and running as fast as possible is not a priority. The time it would take reinstalling and configuring again the server is not a problem.
[*]You want backup your system, because the availability of the service is very important. If something happens, you can have your server up and running pretty fast.
[*]All of the above.
[/LIST]
For regular data, like personal files, you don't need to stop the services to make the backup (although, I don't know how Owncloud works). For system data, or data that is contain in a database, most of the time you would need to stop the services to backup it up.

If your server is on the 'cloud', your cloud hosting provider may provide backup functionality for an additional costs. For instance, DigitalOcean offers backups that only adds 20% to the cost of the server.

Another functionality that cloud providers offer is snapshots, which could take care of both personal data and the system itself. If your server dies for some reason,  you could spin up a previous snapshot, and be up and running pretty fast.

If you want do snapshots yourself, you may want to consider using a snapshot enable filesystem. Take a look at Btrfs and Zfs.

Since spin up a server, install software and upgrade it, is pretty simple and fast these days, and alternative to backup everything could be to run scripts that backup important configs file to personal directories. That way when you backup your personal data, you'll be backing up also the server config files.

Finally, I'd recommend taking a look at '**duplicity**' which:
[LIST]
[*]Works on the command line.
[*]Provides full backups.
[*]Also provides incremental backups.
[*]Use encryption for security.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by oldfred on 2015-03-24
I use rsync for my desktop, but you may want to review this alternative.

 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

