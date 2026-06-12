---
title: "Ubuntu Server Backup"
date: 2012-05-03
forum: Server Platforms
---

### Post by anonymouschief on 2012-05-03
Hello All,

Before I upgrade to 12.04, I would like to back up my current installation, in case things go bad after I upgrade.

I have a drive, already mounted, that I would like to back up to.

Please let me know if backing up / with rsync will do, and if copying the contents of my backup back to / will serve as a restoration.

Please also suggest the commandline options that I have other than rsync to do a snapshot-type backup that I can revert to should the upgrade fail. I do not have any web interface or Gui installed on it.

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-03
Clonezilla has always worked fine for me, but you would have to take the server down and image the drive from a livecd.

---

### Post by LHammonds on 2012-05-03
I recommend a dead-simple utility called [Redo Backup and Recovery]("http://redobackup.org/").

I requires the server or PC to be rebooted and unavailable during the backup/restore.

You download the redo .iso, burn to CD and you now have a bootable backup CD.

Attach the media you want the backup to reside on (such as an external USB drive) and boot the machine with the CD in the drive.  Then follow the simple instructions to make a full backup.

If your system get's hosed up after an upgrade, repeat the process but when redo is up, choose the restore option.

I've tried it and it works like a champ and is great for handing out to people you support with a simple one-page how-to so they can backup and restore by themselves.

LHammonds

---

### Post by anonymouschief on 2012-05-03
Thanks CharlesA and LHammonds for the responses. My server is down in the basement, and has no monitor. I manage it via shell from my other computers. Is there a system as efficient as Redo and Clonezilla that is not livecd based that I can use?

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-03
You could always use tar, but that might be a bit of a pain.

---

### Post by anonymouschief on 2012-05-03
> **CharlesA said:**
> You could always use tar, but that might be a bit of a pain.

I would really prefer an implementation that did not just copy the files and folders in their native format to another location.

I think tar would work. Do you have a working script you could share that use tar?

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-03
You should be able to just run tar on the root and exclude /dev and /proc

---

### Post by LHammonds on 2012-05-04
For online and complete backups, you can make use of LVM snapshots which can all be scripted.  There are caveats so do your research and be sure you test and document how to backup and restore with your preferred solution.  rsnapshot is another option.

---

### Post by SeijiSensei on 2012-05-04
> **anonymouschief said:**
> I would really prefer an implementation that did not just copy the files and folders in their native format to another location.

Why?  This is by far the easiest method if you simply want to create a restorable backup.

If the backup drive is at least as large as the current drive, you could use **dd** to make a bit-for-bit copy of the current drive to the backup.  You'd need to boot from a CD or USB drive, though, which it appears you'd have problems doing.  

Personally I'd just use rsync.  

```

sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup
cd /
sudo rsync -av . /mnt/backup --exclude=proc/ --exclude=dev/ --exclude=mnt/

```

---

### Post by SeijiSensei on 2012-05-04
> **anonymouschief said:**
> I would really prefer an implementation that did not just copy the files and folders in their native format to another location.

Why?  This is by far the easiest method if you simply want to create a restorable backup.

If the backup drive is at least as large as the current drive, you could use **dd** to make a bit-for-bit copy of the current drive to the backup.  You'd need to boot from a CD or USB drive, though, which it appears you'd have problems doing.  

Personally I'd just use rsync.  

```

sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup
cd /
sudo rsync -av . /mnt/backup --exclude=proc/ --exclude=dev/ --exclude=mnt/

```

If you want to use tar, and compress the image with bzip2, use this:

```

sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup
cd /
tar cjvpf /mnt/backup/fullbackup.tar.bz2 . --exclude=proc/ --exclude=dev/ --exclude=mnt/

```

---

### Post by anonymouschief on 2012-05-04
> **SeijiSensei said:**
> 
Personally I'd just use rsync.  

```

sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup
cd /
sudo rsync -av . /mnt/backup --exclude=proc/ --exclude=dev/ --exclude=mnt/

```

Ok, I am convinced, I will go with your rsync recommendation. I already have the other drive mounted as /data

Could you please:
[LIST=1]
[*]Explain why you excluded the "proc" and "dev" folders.
[*]Tell me how I would restore these files to my file system from a backup. 
[*]Will a reverse version of this script still do to restore files to the file system. Same switches, but no exclusions?
[*]Confirm if this command will backup my current ubuntu 11, and will be able to restore it if ubuntu 12.04 goes awry
[/LIST]

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-04
> **anonymouschief said:**
> Ok, I am convinced, I will go with your rsync recommendation. I already have the other drive mounted as /data

Could you please:
[LIST=1]
[*]Explain why you excluded the "proc" and "dev" folders.
[*]Tell me how I would restore these files to my file system from a backup. 
[*]Will a reverse version of this script still do to restore files to the file system. Same switches, but no exclusions?
[*]Confirm if this command will backup my current ubuntu 11, and will be able to restore it if ubuntu 12.04 goes awry
[/LIST]

Thanks,
:popcorn:
AnonymousChief
1) /dev and /proc are virtual file systems created by the kernel on boot.

2) Just switch the source and the destination.

3) It might be a good idea to do exclusions because if I remember right, you'd have to restore the file from a livecd.

4) Yes.

---

### Post by anonymouschief on 2012-05-04
> **CharlesA said:**
> 1)
3) It might be a good idea to do exclusions because if I remember right, you'd have to restore the file from a livecd.


Which live cd do I use to do the restore, the Ubuntu Server install cd?

Thanks,
:popcorn:
AnonymousChief

---

### Post by SeijiSensei on 2012-05-04
Whichever CD you used originally.  You'd start with a fresh installation of the original system.  Restoring from backup will then overwrite any existing files with their more recent versions and add any unique files like those in /etc and /home.

Before you do this, though, might I make a couple of suggestions about ways to make your life easier next time around?

It's often useful to have a spare partition available on the hard drive into which you can install any new versions of the OS.  Along with that I also have a small separate partition for /boot and another separate partition for /home.  I'd build a fresh installation like this:

/dev/sda1 - 512 MB assigned to /boot
/dev/sda2 - swap (usually 1-2x total physical memory; smaller memory requires more swap)
/dev/sda3 - extended partition
...   /dev/sda5 - 20 GB Linux for the primary OS mounted on /
...   /dev/sda6 - 20 GB Linux spare for any OS upgrade
...   /dev/sda7 - rest of extended mounted on /home

If you need to have Windows then I'd put that in /dev/sda1 and readjust the rest of the definitions accordingly.  Since this is a server, this shouldn't be an issue for you.

Now if you decide to install a new distribution for testing, you would put it in the spare partition.  You can choose which version to use at boot by selecting the appropriate kernel image from the grub menu.  Having /home separate allows you to preserve those files when upgrading and have them available to both OS images.  If the upgrade goes OK, you're all done.  Any future upgrade would be put in the now-unused partition, /dev/sda5 in the example above.  If things goes awry, you can revert to the original OS image by making it the boot default.

I actually have another separate partition for /usr/local because I occasionally compile programs from scratch and want to use the resulting binaries with future upgrades as well. I also store custom administrative scripts I write in /usr/local/sbin and want them available to all OS versions. For most people, though, just having a separate /home is sufficient.  However if you're running a database server, you might want to consider putting /var on a separate partition as well, especially if the databases are large.  If you do use PostgreSQL or MySQL, I strongly recommending using their associated "dump" utilities to create a plain-text backup of the database just in case there's a conflict between a new version of the DBMS software and the binary format of the old database.

---

### Post by CharlesA on 2012-05-04
> **SeijiSensei said:**
> /dev/sda1 - 512 MB assigned to /boot
/dev/sda2 - swap (usually 1-2x total physical memory; smaller memory requires more swap)
/dev/sda3 - extended partition
   /dev/sda5 - 20 GB Linux for the primary OS
   /dev/sda6 - 20 GB Linux spare for any OS upgrade
   /dev/sda7 - rest of extended for /home

If you need to have Windows then I'd put that in /dev/sda1 and readjust the rest of the definitions accordingly.  Since this is a server, this shouldn't be an issue for you.

Nice partitioning layout. I'd probably use something like that if the default "one partition for /" didn't work for me.

> 

I actually have another separate partition for /usr/local because I occasionally compile programs from scratch and want to use the resulting binaries with future upgrades as well.  For most people, just having a separate /home is sufficient.  However if you're running a database server, you might want to consider putting /var on a separate partition as well, especially if the databases are large.  If you do use PostgreSQL or MySQL, I strongly recommending using their associated "dump" utilities to create a plain-text backup of the database just in case there's a conflict between a new version of the DBMS software and the binary format of the old database.

That would be a good idea too. I've got the database from a small forum running on my web development box and I've been just dumping the db to a tar.gz with mysqldump instead of copying the entire database.

---

### Post by anonymouschief on 2012-05-04
Thanks a lot **SeijiSensei** for your partitioning layout and the backup script. Thanks **CharlesA** for answering my backups-related questions. I will use rsync for my backups, and will consider manually setting up my partition layout the next time I do a fresh install.

Thanks,
:popcorn:
AnonymousChief

---

