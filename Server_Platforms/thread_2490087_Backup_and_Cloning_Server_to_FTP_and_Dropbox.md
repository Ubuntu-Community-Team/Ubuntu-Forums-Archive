---
title: "Backup and Cloning Server to FTP and Dropbox"
date: 2023-08-22
forum: Server Platforms
---

### Post by WhiteTigerIT on 2023-08-22
I need to backup a server with 160GB disk space so that I can also restore to another server/VM.
The backup must be done on FTP or on services like Dropbox, which rules out the possibility of using rsync and also dd having to do the compression on the fly.


The starting server is in Production, so I have to act very carefully.


I also knew of a tool that, like SysPrep for Windows, prepares the machine in case the restore needs to be done on a different machine.


Instead of a tool I could also use a real backup software, but it must be Open Source and manageable via command line or Webgui.


Thanks in advance for any suggestion.

---

### Post by MAFoElffen on 2023-08-22
Please search on username "TheFu" and "backup"... He has spent a lot of time posting ingenious ways to do his backups and restores. Though he uses rsync most of the time.

I don't use GUI tools, as I script most of my work to automate it for me. And most of that is over shh.

He and I use the same methodology for Disaster Recovery, and migrations, in which we isolate data and configuration files that are required on a fresh install to get back to where you need to be. Then back those files up. Then do incremental backups to keep it updated. Then i get a list of all the user installed applications beyond the default install. 

Install fresh. Use the user installed list in a post-install script to install all the applications that server had, and restore the data and config files over the fresh install. Shortens that process to around 20-30 minutes.

If you were on LVM2 or ZFS, you could do all of that Live, and much easier... All mine are now ZFS, where I can take snapshots of the datasets I've isolated. Send and recieve them to may backup pools. From the backup pools to wherever I need to restore them. All on a live filesystem. LVM2 has some of those features also. Ideas to make things easier and more robust... You are recreating to new. You could just as easily migrate into a File manager that has those features at the same time, to make future maintenance option possible.

The only tool I know of like Windows sysprep for Linux, is just for virtual machines (virt-sysprep). Linux checks the hardware on boot and tries to adapt to what is there dynamically. So if switching a machine one-for-one, that is negligible. If you implement your backups to how i said, and recover that way, there is no need for sysprep.

If you are dealing with images of disks, then when you restore, then you need to worry about possible specialized drivers for differences in storage controllers, machine ID's, network device names, unique storage device names, and hostname... So there isn't a conflict in the hardware or further out into the infrastructure.

---

### Post by TheFu on 2023-08-22
> **WhiteTigerIT said:**
> I need to backup a server with 160GB disk space so that I can also restore to another server/VM.
The backup must be done on FTP or on services like Dropbox, which rules out the possibility of using rsync and also dd having to do the compression on the fly.


The starting server is in Production, so I have to act very carefully.


I also knew of a tool that, like SysPrep for Windows, prepares the machine in case the restore needs to be done on a different machine.


Instead of a tool I could also use a real backup software, but it must be Open Source and manageable via command line or Webgui.


Thanks in advance for any suggestion.

A) Don't use images. Just. Don't.  It is a waste of your time. Images ARE a waste of time and not flexible. We can do much better.
B) You need local backups to the machine and remote backups.  The remote backups can use what storage you like and whatever network access protocols you wish.  plain FTP is a failure, however.
C) While it is true that most of my data is mirrored using rsync, that's only for media files which are too large to go into the versioned backup storage areas.
D) I use **rdiff-backup**. But it will only "pull" backups over ssh, not plain FTP nor dropbox.  You need to be "pulling" backups, not pushing them to combat malware and crypt-ware.
E) If you are stuck using FTP or any other non-ssh-based network protocol, then something based on **Duplicity** will be best.
F) Whatever you choose and setup, test the restore.  When I was first setting up new backup methods, it took about 5 attempts before I got everything I needed included in the backups. The first attempt had a number of chicken-egg problems.

Duplicity and rdiff-backup both suck, in their own ways.  Duplicity checks all the boxes for what we want in a backup tool, but the implementation details mean doing a full backup every month is still required. That sucks.  Plus the backup data is "chunked" to be more efficiently transmitted, which means the restore process needs to use the same tool. duplicity supports encryption of the backed up data, which is why using plain FTP with it should be fine.  OTOH, if you need to restore 1 file, it isn't just go find the file and copy it back.  
That's where rdiff-backup shines.  The most recent backup looks like an rsync mirror and older versions are stored as rdiff.gz files from the prior version. If you have 90 daily backup versions, you can only remove from the farthest end, not in the middle.  Encryption has to be handled by other tools, typically the file system.  Like rsync, rdiff-backup works over ssh, not plain FTP.  So that wouldn't be suitable for someone who wants to use dropbox or S3 storage.  Duplicity will work with both.

The first rdiff-backup version will take as long as rsync would take to backup, but after that, the next version will be just changed data. Typically, on my servers, that is about 1-3 minutes for each daily backup.  I pull the backups. The production systems cannot access the backup storage areas in any way. It isn't shared storage. That's important.

I tested dupicity, deja-dup, duplicati - all use the duplicity engine.  In my tests is was painfully slow or didn't work. But that was long ago.  It was taking over 8 hrs to backup 100GB.  rdiff-backup did that in about 20 min, on the exact same hardware/network/OSes.  I must have been doing something wrong.

After I create my local backups using rdiff-backup, I use rsync to mirror those at a relative's house. We swapped HDDs about a decade ago.  I have his backups and he has mine.  Nightly, the diffs are sent of the rdiff-backup areas between our 2 systems. This wouldn't be possible without big pipes to the internet. There is some trust in doing it, even with the backups placed onto encrypted storage.  When it is mounted, the local root can see and access it. Trust.

Before you pick a backup tool, test it out with something small.  I like to test using /etc/ as the source.  There are files of different sorts inside there, different owners, different groups, while still being 10MB or less. It is a good test.  Then go look at the backup target area storage. See what gets put there. How might that format be great and terrible. Change a small file, re-run the backups.  It will still be fast, but what happened in the target storage?  Is it a forward diff or a reverse diff?  Would you need to restore using 30 backup sets if your last full backup was 30 days ago, just to get back files from last night?

If you need to move to new hardware, can your backup method support that?  Images do not.
If you want to change the underlying storage completely, can your backup method support that?  I know this works with rdiff-backup.  As long as the restore location "appears" from a directory level to be the same, the actual file systems used don't matter.  Want to change from LVM+ext4 to ZFS?  It is possible.  Need to change from ZFS to BTRFS? It is possible.  

Tools that use the volume manager to clone files to another system have some limitations on flexibility.  If you have 7 days of snapshots and send them to another system, that could make for a very fast restore, indeed. But that's more for logical issues, not hardware issues.

Things to consider.

BTW, I pull backups to my backup server from VPS systems running at a remote virtual machine provider using rdiff-backup.  Because I don't backup the entire machine, just what is needed to restore it, I can setup on a new VPS is less than 15 minutes (actually, I think I could do it in about 4 min).  My VPS systems don't really have any data. They are gateway systems.  Everything I need to reproduce one of these "gateway" systems with 90 days of backups is only 34MB.  It only has a VPN  server and **haproxy** running on it. 

If your VPS provider doesn't support ssh, you should fire them ASAP. In 2023 ... actually since 2002, it has been unacceptable NOT to support ssh/scp/sftp/rsync on these hosting providers.

---

### Post by WhiteTigerIT on 2023-08-24
Thanks for the replies.
My ISP uses Acronis. I pay for 100GB of Backup space. Any excess is a separate cost.
The restore on the same VPS from which I made the backup works, in theory.
I tried to restore to a new VPS and it was a tragedy. 3 days of useless testing only to find that the LVM volumes are different and this crashes the restore.
But the disk configuration is done by the ISP and not by me.
At this point I'm not sure if it will work in the future due to technical-commercial choices of the ISP itself.

I also have two hosting plans with unlimited space and 1TB free on Dropbox.
So, I would like to create a reliable backup system using these destinations.
That rules out rsync though, and I'd like to avoid renting a third server just for backup. I can use SFTP.

I could use my own linux server locally, but my connectivity is only 100/20Mbs. A "Full" restore would take too long.

Where can I find something to test on my VMs locally in the meantime?

---

### Post by TheFu on 2023-08-24
> **WhiteTigerIT said:**
>  
Where can I find something to test on my VMs locally in the meantime?

Did you read my post?

---

### Post by WhiteTigerIT on 2023-08-24
> **TheFu said:**
> Did you read my post?
Sure!
You use rdiff-backup, but that assumes there is another server that I don't have. Unless it also works with SFTP.
Then you suggested duplicity, but listing flaws and problems.

Am I obviously missing something?

In any case, as I said in my initial post, it's not just a question of making a backup, but also a **global restore**.
In other words, **the entire operating system must be restored**.
So the software restore must foresee it because the destination VPS may not allow overwriting of system files.


Duplicity does not seem to me that this allows it.
RDiff-backup I don't know. A quick look at its documentation does not seem to me that the topic is addressed.

Searching among the various European ISPs, all VPSs with disks larger than 100GB also have at least 4 cores and 8GB of RAM. So they are all very expensive.
If there was at least one VPS with 2 cores, max 4GB RAM and more than 100GB disk with a low price, then I might consider buying a third VPS just for backups.

---

### Post by TheFu on 2023-08-24
> **WhiteTigerIT said:**
> Sure!
You use rdiff-backup, but that assumes there is another server that I don't have. Unless it also works with SFTP.
Then you suggested duplicity, but listing flaws and problems.


Image-based backups are going to fail for a number of reasons, unless you can always guarantee the exact same hardware will be used.  I cannot, even when I control the hardware, so there's little use.  Additionally, image-based backups provide next to zero flexibility and eat storage.  Most of my systems have at least 90 days of versioned backups.  Higher risk systems get over a year of versioned backups.  Nominal restore periods are from about 20 min to about an hour.  These restores are not "1-click".  I don't have that sort of money and having a system down for an hour isn't the end of the world.

Professionally, I work on HA and fast restore systems.  If a 45 minute restore time isn't sufficient, then HA is required with Active-Active systems.  Those systems need to be far enough apart so they won't be impacted by the same regional disasters.  How, specifically to accomplish that depends on the nature of each system and the applications being run.  If a short time is mandatory, open your wallet and be prepared to pay for it.  For systems with too high of transaction rates, we failover to the other location every 2 weeks, then fail back 2 weeks later, to ensure both systems work and our failovers work.  Those are in an active-failover setup.  The Active-Active systems are easier, but need to be sized to handle 100% of the load, before a failure happens.

Duplicity has flaws for my needs. Perhaps those aren't flaws for you?  Lots of people use it.
rdiff-backup can perform local or remote backups. It isn't perfect, but it does meet the needs I have and solves many problems that other backup tools don't seem to solve in my research/testing.

There are many different solutions for backups possible. Lots of forum posts there with suggestions as well as other articles on the internet. I wish you luck.

---

### Post by WhiteTigerIT on 2023-08-25
> **TheFu said:**
> Image-based backups....

Forgive me, but I still don't understand if with rdiff-backup you can do a full restore and restart the machine or if you do something else first. For example by installing the operating system.


For just saving data years ago I used rsnapshot, also based on rsync.
On a new VPS I installed the O.S. and then I ran the restore.
But I could not fully restore the VPS.
Even if the SO it was the same and in the same version, however there were some differences especially if there were web applications that required specific configurations.


I don't want to use pictures either.

---

### Post by TheFu on 2023-08-25
These forums are an amazing resource full of already answered questions.  I'd encourage you to use it.
[Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927)
I think the only thing not in that explanation that I do is to tag OS config files in /etc/ with a tag that can be found at restore time. I only tag files that have been manually modified, so I know to use **fgrep** to find them at restore time (I do get all files in /etc/) and review the files for any system-specific modifications.  In general, if there is a disk UUID, that file cannot blindly be copied back or it will break the new system.  This is why most dumb restore efforts fail.  But if you know what you are doing, just slightly, you can recognize system specific changes and manually merge them into the fresh OS install.  The order that things are restored matters. Read the link.

I know what you seek. It doesn't exist and it removes all flexibility. Once you get passed that and embrace that every restore needs to begin with a fresh OS install from installation media to handle different hardware, different disks, different setups, then you can move on to solving the problem.  What's the fastest way to backup and restore applications?  That's the real issue.

I used **rsnapshot** for a few years, until the amount of data made it fail, file metadata that changed was lost in the data-only versioning, and large files were taking more than the allowed approved backup window.  After switching to rdiff-backup, my backups that were taking many hours has dropped to less than 30 minutes total. Most system backups take 1-3 minutes.  rsnapshot is fine for simple data that needs versioning.  But for desktop users, back-in-time can do that is a more intuitive way, so that's the usual pointer for end-users with very simple backup needs.

BTW, I've posted simple rdiff-backup scripts for backing up all the important data in these forums a few times.  But if you don't have ssh access, that isn't useful to you.
[Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)

I don't keep huge amounts of data in the cloud.  Using cloudy services just rubs me wrong.  However, I do you them as gateway and proxy systems. The backup last night on of my gateway systems ...
```
=================
INFO: Backing up gw.example.com ...
=================
INFO: Backing up gw.example.com ...
INFO: Removing backups older than 280D
No increments older than Thu Nov 17 23:08:30 2022 found, exiting.
INFO: Post-Backup-Cleanup() 

INFO: Backup Start: 2023-08-25-00:08:20
INFO:   Backup End: 2023-08-25-04:08:30
```
so that took less than 10 seconds. Most of it was gathering system information before transferring files.  Looks like I have a bug in the way the end-time is calculated.  The hour part is wrong.  I'm using start_time=$(date "+%F-%T")  ... but the end_time isn't being calculated correctly, it seems.  Ah ... timezone differences, it seems. Fixed.  just ran it again ... 
```
INFO: Backup Start:     2023-08-25-07:16:41
INFO:   Backup End:     2023-08-25-07:16:59

```
Thanks for making me look at that.

---

