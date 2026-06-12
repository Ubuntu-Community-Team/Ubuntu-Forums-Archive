---
title: "a question about softwareRAID and backup software"
date: 2017-11-27
forum: Server Platforms
---

### Post by cazz on 2017-11-27
Hi
Right now I use Windows 10 and syncback to backup my files from one computer to another (Windows to Windows over network)
Now I try a little to replace my Windows backup server to Ubuntu server and SoftwareRAID.

But I have two question.

1)
Right now is that I run softwareRAID even in Windows and I use RAID0 to have a big file partion for my files and it works greate
Even if something happen to my Windows disk (I have windows on another harddrive then softwareRAID) I can easy connect the new Windows to the softwareRAID and find my files.
Is that same easy if somehow something happend to ubuntu server and I need to reinstall the server, can I easy access my files in the RAID if I connect the softwareRAID??

2)
I use syncback, very very easy to use and it only do it run every night and copy files from my one Windows computer to another, it does not do any sync so if I delete a file from Computer1 it does not remove the file in Computer2
and when it done it send a e-mail with result to my email address (I have put a SMTP address inside the syncback setup).
Is that any good software in ubuntu?
I have head something about Bacula but I think that is to much for me to use or is it easy to use?
Well I can make a script that run but I was thinking to use a finnish software that can send a email log every time its done and I do not need to install somekind of SMTP server on the server.


/UPDATE
A little update om question 1
I think I got it to work but I have to try some more

I did remove ubuntu server and reinstall a new one and after all update I did to this

did use 

```
sudo mdadm --stop /dev/md127
``` (I did find it with cat /proc/mdstat)
after that I did do
```
sudo mdadm --assemble --force /dev/md0 /dev/sdb /dev/sdc
```

after that just create a mount point and then mount the filesystem

not sure if that is the right thing to do but I going to try some more :)

---

### Post by mastablasta on 2017-11-28
1. yes, software raid is very versatile as well as some other partitioning schemes and file systems (such as for example BTRFS). on the next install i plan btrfs and no more raid but rather good solid versioned backup. i don't need the server to work 24/7, so raid is not necessary. versioned backup are more important.

2. do you need gui or do you prefer cli? there is plenty software that does just that. forums are full of backup threads. for email i use gmail - server creates and sends me a message from its gmail account.

---

### Post by cazz on 2017-11-28
thanks for the replay
I was thinking CLI, no GUI on the backupserver

yes is alot but have not find any that have build inside mail client.

but I have a mail server that I can use to send mail, then I just need a good basic backup script/software that even give me a log that I can attached.


/UPDATE

Have found that I can use rsync that can create a log and even skip if backup servern have the file already.
Time for me to build a script :)

---

### Post by mastablasta on 2017-11-29
rdiff-backup is better than rsync.

Areca also has CLI version. for example i set it up on windows, also at work. you use GUI to set it all up and then it gives out a script. which you then then run it with cron or similar jobs.

output form backup job can be  (for example if nothing else is present as option) "printed to file" and then file or log or output is sent as mail using some mail "service". 

for example this is a very light send only service - sSMTP: [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

it is sending me everything from update information (Unnatended updates) to break in attempts (fail2ban)...

---

### Post by cazz on 2017-11-29
Hi
I have now try Areca and sSMTP

I have got Areca to work in GUI in linux but have not got it to work in CLI, have also not find how it save a log for me to see and it also put alot of stuff in the destination folder that I don't like like a random foldernumer and som zip/tar file.
I guess it is some settings.

I have install sSMTP but when I try to send something nothing happend so after a minute I try to cancel but no luck
Did try with this tutorial
[http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html](http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)

---

### Post by LHammonds on 2017-12-01
With RAID, everyone has their own preferences and use cases but it is all about surviving a physically dead hard drive.  But keep in mind that RAID is NOT a backup.

For backups, I see needing 2 different areas of backup on at least 2 different sets of media (local and remote)
 1) Operating system.
 2) Data and config files.

1) The operating system does not change much so having a full backup you can restore on another machine or the same machine can be done less often.  I configure all my servers to use LVM and separate each of the main partitions to allow growth were needed.  I then use fsarchiver to take online snapshots of the various partitions.  Sometimes I snap all the partitions, sometimes I snap all of them but the backup and data partitions...just depends on the server.

2a) For data that changes frequently, I just rsync the files to another partition (/bak) and then rsync the /bak partition to a remote server (different physical media)

2b) If the data is small / manageable so you can keep multiple versions of it, you could rsync the files to the /bak partition and then compress the backup into a single archive file.  Then send the archives to a remote server.

I have a step-by-step tutorial for setting up a server but here are the highlights I covered above:
 * [Partition Design]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p445")
 * [Backup Partitions Using LVM Snapshots and FSArchiver]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p452")
 * [Restore with fsarchiver]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p453")
 * [Backup data (rsync and compress)]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=226#p488")

LHammonds

---

### Post by cazz on 2017-12-01
yes RAID is not a backup, that why I have two server with same file.
Is that why I was asking for a good backup software so I can connect ServerB to ServerA everynight to run a backup from A to B

---

