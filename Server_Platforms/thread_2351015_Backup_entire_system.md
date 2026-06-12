---
title: "Backup entire system"
date: 2017-01-30
forum: Server Platforms
---

### Post by torkness on 2017-01-30
Hello,
I am new Ubuntu Server user with little experience from Raspbian and Linux Mint. I want to create home server so i need to make backup of fully configured system. I tried to tar whole system (without some directories) but tar'ing working system wasn't good idea. I am thinking about creating iso of entire disk. Is it good trace? How can i make it?

---

### Post by Bucky Ball on 2017-01-30
You could try cloning the partition/disk with something like [Clonezilla]("http://clonezilla.org/clonezilla-live.php").

---

### Post by bearlake on 2017-01-30
> **Bucky Ball said:**
> You could try cloning the partition/disk with something like [Clonezilla]("http://clonezilla.org/clonezilla-live.php").

^^^ This, been using Clonezilla for partition and full disk backup for years now.

I like [Luckybackup]("https://www.linux.com/learn/easy-linux-backups-lucky-backup") for my personal data and files like music and so on.

Luckbackup is in the repositories.

---

### Post by Bucky Ball on 2017-01-30
> **bearlake said:**
> I like [Luckybackup]("https://www.linux.com/learn/easy-linux-backups-lucky-backup") for my personal data and files like music and so on.

Snap! Ditto. Quick and easy for the smaller jobs. ;)

---

### Post by TheFu on 2017-02-01
Welcome to the forums.

Having a backup is a smart thing. Bad things seem to happen to new linux people the most.  I avoid bit-for-bit clones. Find them wasteful and limited at restore time.

**fsarchiver** is an option, but like other imaging solutions, it requires a completely quiesced system. That usually means booting off alternate media. 
The normal backup tools are options too, like rsnapshot, rbackup, rsync, rdiff-backup, duplicity, etc. For people really new to Linux, these tools can seem too hard, so something like **back-in-time** might be better.  Just know that back-in-time uses rsync with hardlinks to make versioned backups. Hardlinks require a Linux file system - no NTFS or FAT allowed. They also don't track file metadata changes over time, so if the owner or group or permissions changed last week, that info is lost.

An ISO probably won't work. The OS will expect read-write access and an ISO is a read-only device.  Chances are you'd want the ISO to fit onto a single DVD too - most installs are larger than that.

Tar and tar-like tools are useful for less than 1G of storage.  After tar was designed for sequential tape backups.  I used tar to tape for backups for a few years. Wouldn't use tar for anything over about 250MB these days, there are just better options.

When I need a mirror, I use rsync, but I'm selective about the directories to be mirrored since trying to mirrors some tempfs and pseudo-file systems won't work. Same for device files/pipes.  With rdiff-backup there is a single option to stop those special files not be an issue; --exclude-special-files.  Makes life easy.

Also, at restore time, you need to know  Each method will alter the restore steps needed.  I generally assume I'll need to manually install and update grub - not a big deal on my systems, but on some systems it can be non-standard (HP with UEFI).  grub 2 made this all sooooo much easier, but it doesn't help with non-standard systems.

---

### Post by mastablasta on 2017-02-02
backup of entire system after configuration is done is easiest to do with either Clonezilla or Redo backup. you image the whole disk (or partition). the image is compressed and empty disk space is also nearly 0. 

redo backup has a wizzard that guides you, clonezilla has documentation and a bit more basic wizzard for that: [SIZE=2][http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)
[/SIZE]

---

### Post by LHammonds on 2017-02-02
I use fsarchiver.  I have a cron job that is setup to run a backup on the 1st day of each month.  It creates a hot backup of each partition because I use LVM and have free space in my volume group to do online snapshots.  It creates these backup files to a local partition (/bak) and then copies them to a remote server for safe-keeping in case the hardware is destroyed but I also keep them on the local machine in case a single partition is destroyed. If I only need to restore locally, it is much faster than over a network connection.

To restore my server, I boot the server using a rescue CD and restore that way.

The exact steps on how I setup my server using LVM, fsarchiver and automation backup/restore scripts are documented in my "How to Install Ubuntu Server" link in my signature.

LHammonds

---

