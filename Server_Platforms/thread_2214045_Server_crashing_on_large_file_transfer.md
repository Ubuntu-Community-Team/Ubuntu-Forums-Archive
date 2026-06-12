---
title: "Server crashing on large file transfer"
date: 2014-03-30
forum: Server Platforms
---

### Post by david_brown on 2014-03-30
Hi, I'm running a simple home headless server with 12.04. I use it for torrenting, media serving and backups. It has a habit of crashing when backing up where large file transfers are involved. I'm using Rsync as a cron job to back up from the internal drive EXT4 to an external ntfs drive. If the transfer involves copying movies over it dies. Doing a bit of googling I see this has been an issue over time. I'm still a bit of a newbie on a steep learning curve with Ubuntu, so any help in simple language would be much appreciated. Thanks

---

### Post by TheFu on 2014-03-30
What is a "large file?"
NTFS shouldn't have an issue based on size, but rsync does get confused for files over a few GB even on ext4-ext4 transfers.  I used to try this to backup virtual machines but found it unacceptable.  Ended up switching to a completely different backup method which it nicer, faster, more efficient in time, storage, and network bandwidth. For media files, I still use rsync. For backups of other files, I want versioning in the backups.

For backups of Linux system files, retaining permissions is critical, which rsync to NTFS will loose.

---

### Post by david_brown on 2014-03-30
Thanks. I think I'll return to the way I used to do it and have a USB drive on the router that everyone can use as backup and just use the server for torrents and media serving. Shame, but at least I don't have to remaster the flipping server every couple of weeks.

---

### Post by CharlesA on 2014-03-30
> **TheFu said:**
> 
NTFS shouldn't have an issue based on size, but rsync does get confused for files over a few GB even on ext4-ext4 transfers.

Define confused?

@OP: File system shouldn't matter and I would take a look at both the memory on the server and the health of the drives on the server. It could be showing signs of a problem and ignoring it would be a bad idea.

Are any error messages displayed?

---

### Post by TheFu on 2014-03-30
> **david_brown said:**
> Thanks. I think I'll return to the way I used to do it and have a USB drive on the router that everyone can use as backup and just use the server for torrents and media serving. Shame, but at least I don't have to remaster the flipping server every couple of weeks.

"Server crashing" can have multiple meanings. Could you please clarify?

An rsync shouldn't harm anything else on the machine, unless an important file system is being filled to 100%.  The system should keep working.

Why would you need to remaster anything?

What do the log files show? See my signature links for how to find out.

---

### Post by sudodus on 2014-03-30
@david_brown

I have used rsync directly and indirectly via Unison to synchronize and or backup huge files, sometimes several tens of megabytes (big compressed dd-image files, that I used before I found Clonezilla). I think rsync works if I have enough space to create a temporary file. Could that be related to your problem?

@TheFu

Please tell us what completely different backup method you use, which it nicer, faster, more efficient in time, storage, and network bandwidth :-)

---

### Post by david_brown on 2014-03-30
I need to remaster because the system will not boot. I can't see the server as it's hidden away with a manual start button connected remotely. I can't hear the post beep or see the drive lights and I might be pressing the button too soon and corrupting the boot sector??? I have a lot of space on the destination drives so space is not a problem. I don't know how to repair boot without remastering.

---

### Post by TheFu on 2014-03-30
> **sudodus said:**
> @TheFu

Please tell us what completely different backup method you use, which it nicer, faster, more efficient in time, storage, and network bandwidth :-)

**rdiff-backup** - it is based on rdiff and librsync.  It fails in meeting every "backup best practice", since it doesn't store the data into encrypted format, but in every other way, it does meet those best practices.
I've written about it in these forums and on my blog many times.

As a simple test, load up rdiff-backup (use the repo version), and run

```
mkdir /tmp/etc
sudo rdiff-backup --exclude-special-files /etc /tmp/etc
```
Then make a tiny change in any file in /etc and rerun the rdiff-backup command again.  Using /etc is good for testing since it is small, but will definitely be needed in real backups. Look at /tmp/etc/  .... it will be a mirror of the "current" system at the time of the command + 1 more directory - rdiff-backup-data/ Inside there are gz compressed diffs to the files that change by date and directory structure.  There is NOTHING proprietary about the file formats and we can manually get back any version desired ... or just use the tool with -r to specify a file, a directory and/or a date to restore.  Of course, since the most recent backup is a mirror, a normal file copy works for that, if desired.

After you are done testing, delete the /tmp/etc directory structure.  I store backups on a central backup server by hostname, currently for 38 systems. Most have 60-90 days of differential backups and use 1.1-1.2x the original storage.  Backups for each system take are less than 6 minutes, but usually under 1 minute. A full system restore takes about 30 minutes, since I do NOT backup the OS, just settings, package lists, and data (don't forget crontabs!). For our email front-end server, the backup is just ... 24MB.  It is 127MB for a virtual machine hostOS. For my daily-use desktop (runs in a private cloud), it is larger, 7.0GB - the oldest backup for that machine is:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Jan 29 02:03:06 2014         8.66 MB           6.14 GB
```
The newest is:
```
Sun Mar 30 02:03:06 2014         5.52 GB           5.52 GB   (current mirror)
```

I sleep extremely well. Failures are reported.

rsync gets confused when files are 2G and larger plus have lots of internal changes, IME. It usually fails, then just copies over the entire file - taking 2x longer to complete.  I was using this to backup 20G virtual machine files and it was taking longer and longer and failing. The versioning was failing too.  By using rdiff-backup running inside each VM, things are better.

I do use rsync for large media file backups where versioning is not desired.

---

### Post by TheFu on 2014-03-30
> **david_brown said:**
> I need to remaster because the system will not boot. I can't see the server as it's hidden away with a manual start button connected remotely. I can't hear the post beep or see the drive lights and I might be pressing the button too soon and corrupting the boot sector??? I have a lot of space on the destination drives so space is not a problem. I don't know how to repair boot without remastering.

I'd try:
sudo grub-install /dev/sd{whatever}
Or use **boot-repair**.

I think this is a much bigger issue. What do the log files show?
If your system has ext3/4 then this sort of corruption is likely to be failing hardware, bad connections. Any journaled file system should be able to handle the power-button 99% of the time.

Destination storage **is not** where temporary files are stored by most processes. How full is / and /tmp and /var/tmp?

---

### Post by david_brown on 2014-03-30
Hmm - you might be onto something with temporary file storage. Originally the OS was mounted on a very small hdd canibalised from a PS3 (20Gb). I then dumped the 20Gb drive and put a small partition on the main 2Tb drive for the OS. Now I have remastered the OS has it's own 260Gb drive so now there shouldn't be any constrictions on temoprary storage. I wonder if that was the problem???

Unfortunately any logs will I assume have been lost by remastering it?

---

### Post by sudodus on 2014-03-30
> **TheFu said:**
> **rdiff-backup** - it is based on rdiff and librsync.  It fails in meeting very "backup best practice", since it doesn't store the data into encrypted format, but in every other way, it does meet those best practices.
I've written about it in these forums and on my blog many times.

As a simple test, load up rdiff-backup (use the repo version), and run

```
mkdir /tmp/etc
sudo rdiff-backup --exclude-special-files /etc /tmp/etc
```
Then make a tiny change in any file in /etc and rerun the rdiff-backup command again.  Using /etc is good for testing since it is small, but will definitely be needed in real backups. Look at /tmp/etc/  .... it will be a mirror of the "current" system at the time of the command + 1 more directory - rdiff-backup-data/ Inside there are gz compressed diffs to the files that change by date and directory structure.  There is NOTHING proprietary about the file formats and we can manually get back any version desired ... or just use the tool with -r to specify a file, a directory and/or a date to restore.  Of course, since the most recent backup is a mirror, a normal file copy works for that, if desired.

After you are done testing, delete the /tmp/etc directory structure.  I store backups on a central backup server by hostname, currently for 38 systems. Most have 60-90 days of differential backups and use 1.1-1.2x the original storage.  Backups for each system take are less than 6 minutes, but usually under 1 minute. A full system restore takes about 30 minutes, since I do NOT backup the OS, just settings, package lists, and data (don't forget crontabs!). For our email front-end server, the backup is just ... 24MB.  It is 127MB for a virtual machine hostOS. For my daily-use desktop (runs in a private cloud), it is larger, 7.0GB - the oldest backup for that machine is:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Jan 29 02:03:06 2014         8.66 MB           6.14 GB
```
The newest is:
```
Sun Mar 30 02:03:06 2014         5.52 GB           5.52 GB   (current mirror)
```

I sleep extremely well. Failures are reported.

rsync gets confused when files are 2G and larger plus have lots of internal changes, IME. It usually fails, then just copies over the entire file - taking 2x longer to complete.  I was using this to backup 20G virtual machine files and it was taking longer and longer and failing. The versioning was failing too.  By using rdiff-backup running inside each VM, things are better.

I do use rsync for large media file backups where versioning is not desired.

Thank you for sharing this valuable information about rdiff-backup :-)

---

