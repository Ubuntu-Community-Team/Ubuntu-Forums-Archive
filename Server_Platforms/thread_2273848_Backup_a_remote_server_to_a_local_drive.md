---
title: "Backup a remote server to a local drive"
date: 2015-04-16
forum: Server Platforms
---

### Post by StMaro on 2015-04-16
I have a hosted server running Ubuntu 14.04 LTS. On this server I have only installed the necessary things to get Pydio Server running (MariaDB, Apache, PHP, etc) along with Pydio Server itself.

What I would like to do, is create a daily, or weekly incremental backup, that is bootable. So at any point, if the server has a problem with Pydio, or a problem with the server itself, then I can just restore to the day before, or a week before, or a month before.

The limitations:
 - The server is about 50GB of data
 - It can only be accessed via SSH as far as I can tell.
 - The only place to backup is to my local Mac via 100Mb/s up&down network
 - The server is in constant use 7 days/nights a week (not sure if this will effect the MySQL database)

From what I've been researching online, something like rsync would be best due to passing data across network. rdiff-backup and rsnapshot both sound like they would be good for me, but I have very limited knowledge of ubuntu, and dont fully know what im doing. I like the idea of using a gui like Carbon Copy Cloner much more, but I dont know if that will work on a remote Ubuntu server making it bootable.

So I was hoping one of you kind souls could help advise me on which option would be best for my situation? 
And any tips on what to do or not to do? For example folders that can be excluded to save on data transfer/storage that are not necessary for the backup to function correctly with pydio intact?

---

### Post by TheFu on 2015-04-16
Forget the GUI.
You can get a non-bootable backup with **rdiff-backup**, then at restore time, run 2 commands (2 sec each) to make it bootable again (worse case) - grub-install and update-grub.  
You'll need to quiesce the DB before doing a backup. That can be accomplished either by shutting down the DB or by dumping it to text before the backup starts.
Versioned backups with rdiff-backup usually take just a few minutes - after the 1st backup has been made which will take hours.
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best how-to I know for rdiff-backup.
```
=== Time for Backups to qbe === 
StartTime 1429164905.00 (Thu Apr 16 02:15:05 2015)
EndTime 1429164907.90 (Thu Apr 16 02:15:07 2015)
ElapsedTime 2.90 (2.90 seconds)
TotalDestinationSizeChange 279 (279 bytes)

``` Just a few seconds for a KVM host machine.
```
=== Time for Backups to blog31 === 
StartTime 1429164310.00 (Thu Apr 16 02:05:10 2015)
EndTime 1429164371.33 (Thu Apr 16 02:06:11 2015)
ElapsedTime 61.33 (1 minute 1.33 seconds)
TotalDestinationSizeChange 14534432 (13.9 MB)

``` Less than 2 min for a blog host.
Of course, the first backup will take the time it takes to mirror everything. Definitely do that manually and don't start the daily automatic backups until it completes.  I'd be surprised if you really get all the data xferred in 2 hrs.

You may want to use duplicity - it has encryption built-in and will store the backups encrypted on remote storage. S3 storage is supported.  It works like the old-school backup solutions, so you'll want to research that method dailies, weeklies, monthlies.  rdiff-backup doesn't work the same way.

rsync is awesome for mirrors, but not so good for versioned backups. It looses permissions, only retaining the latest permissions for the system, which isn't really enough, IMHO.

Oh - and all of these tools are dependent on having ssh setup between the systems so the transfers are encrypted. Both can pull or push their backup data - just depends on which side you want/can run an ssh server and open the port.

I do daily backups here and keep 60-120 days worth depending on the risks to the VMs. I do NOT have a complete backup - just what is needed to rebuild the system back the way it was.  That means I don't backup the OS or installed apps, just the list of installed packages - this saves about 4G per host that doesn't need to be backed up. With 30 hosts, that savings adds up.  For example, our email gateway has 120 days of backups and all of those total to 75MB of storage. If I need to rebuild that system, it takes about 16 minutes.

Since I use VMs, there is an image of the VM storage on another VM host from about a month ago for every VM.  That can provide a head start, if needed.  I will spin up the email front-end on an alternate VM host during OS upgrade sessions just to keep the public SMTP server up.  To make those images requires the OS to be powered off and an imaging tool booted and used.  **fsarchive** is one of the nicest.  Don't know if you can do that on a remote VM from a VPS provider.

Of course, if you have access to LVM snapshots, then all the rules change.

---

