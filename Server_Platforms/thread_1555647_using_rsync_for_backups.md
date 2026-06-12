---
title: "using rsync for backups"
date: 2010-08-18
forum: Server Platforms
---

### Post by djanie78 on 2010-08-18
I need some help please
I got two linux servers, one of then a ubuntu server
What am doing is backing up files from the ubuntu server to this other server using rsync. I want to preserve file permissions and owners so i created the same users and groups on the other server.
Now i rsync and use the option to preserve file permissions.
After my rsync i see all the files have been given to root.
What am i doing wrong? All i want is to preserve the users and rights when i rsync across. Any help will be great.

---

### Post by nbkr on 2010-08-18
Try the options "-o" and "-g".

---

### Post by djanie78 on 2010-08-18
> **nbkr said:**
> Try the options "-o" and "-g".

OK i re-read the manual and yes -o -g could be the solution.
So far... looks good but will have to wait till sometime tomorrow as am backing up a 3TB server. Scary..... 
Thanks dude

---

### Post by LightningCrash on 2010-08-18
the -a option is somewhat analagous to cp's -a option and will also do what you want.

check rsync's man page for more information.

---

### Post by doogy2004 on 2010-08-19
here is a good guide
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by brettg on 2010-08-20
I feel I ought to point out that rsync != backup. If your disaster recovery solution is built entirely around rsync then you should probably prepare yourself for the worst some time down the track.

---

### Post by CharlesA on 2010-08-20
> **brettg said:**
> I feel I ought to point out that rsync != backup. If your disaster recovery solution is built entirely around rsync then you should probably prepare yourself for the worst some time down the track.

Really? How so?

A copy of yer data is a copy of yer data, right?

Sidenote: To use the -a switch (and preserve permissions), you need to run it with sudo or in a root cronjob.

---

### Post by Plecebo on 2010-08-20
> **CharlesA said:**
> Really? How so?

A copy of yer data is a copy of yer data, right?


I think the idea is that rsync can protect you from hardware failure, since you can restore to your most recent rsync, however if you delete a file and run rsync you still don't have a backup of the file. 

With a "proper" backup solution you could restore the file from last week, two weeks ago, a month ago etc etc depending on your backup schedule/scheme. 

Look at rdiff-backup for a backup solution that uses rsync's principals of only working on what has changed. I've not used it much but it seems easy to use and well liked in the community.

---

### Post by CharlesA on 2010-08-20
> **Plecebo said:**
> I think the idea is that rsync can protect you from hardware failure, since you can restore to your most recent rsync, however if you delete a file and run rsync you still don't have a backup of the file. 

With a "proper" backup solution you could restore the file from last week, two weeks ago, a month ago etc etc depending on your backup schedule/scheme. 

Look at rdiff-backup for a backup solution that uses rsync's principals of only working on what has changed. I've not used it much but it seems easy to use and well liked in the community.

That makes sense. I do daily backups using cp -al and rsync, that way I have backups of files that are changed/deleted, in case I need to go back to a previous version.

---

### Post by LightningCrash on 2010-08-21
> **brettg said:**
> I feel I ought to point out that rsync != backup. If your disaster recovery solution is built entirely around rsync then you should probably prepare yourself for the worst some time down the track.

I can boot an rsync'ed root partition in a VM in minutes. What exactly is horrible about that?

rsync over to a new directory every time and have fslint dedup with hard links. throw in a copy of sfdisk's output and you have what you need to put it back down.
(BackupPC would work better though)

---

### Post by djanie78 on 2010-08-26
Wise men. Very helpful people

---

### Post by djanie78 on 2010-09-23
> **LightningCrash said:**
> I can boot an rsync'ed root partition in a VM in minutes. What exactly is horrible about that?

rsync over to a new directory every time and have fslint dedup with hard links. throw in a copy of sfdisk's output and you have what you need to put it back down.
(BackupPC would work better though)

This sounds interesting. Point us in the right direction please. Looks like something i will definately look at as a solution to other stuff

---

### Post by LightningCrash on 2010-09-23
> **djanie78 said:**
> This sounds interesting. Point us in the right direction please. Looks like something i will definately look at as a solution to other stuff
I would start with something like LINUXexplo
[http://www.unix-consultants.co.uk/examples/scripts/linux/linux-explorer/](http://www.unix-consultants.co.uk/examples/scripts/linux/linux-explorer/)

Have it run in cron and copy to NFS or email the results somewhere. The script needs to be modified to exclude process trees in /proc, though.

Then I would just run BackupPC.

To restore you will need the explorer output
[LIST=1]
[*]lvcreate a volume the same size as the original
[*]use your sfdisk output to partition it
[*]use kpartx to map the partitions
[*]mkfs, mkswap on the partitions
[*]mount the partitions in /mnt/restore/ as needed
[*]have BackupPC lay the filesystem back down relative to /mnt/restore
[*]pull the UUIDs of the kpartx partitions, then go into /mnt/restore/etc/ and modify the fstab to reflect the new UUIDs. (or if you're using xen you can use xvda1, xvdb1, etc)
[*]check the networking information in the networking directories
[*]umount the kpartx mapped partitions
[*]use kpartx to unmap the partitions
[*]make a xen config file or make a vmdk file for virtualbox,vmware
[*]boot the VM
[/LIST]

I have scripts that do most of this on my behalf. It's actually very similar to how I provision VMs when I don't use virt-install ;)

---

### Post by LightningCrash on 2010-09-23
I will add that one advantage to using image files (like dd files or qcow2, etc) in production over direct LVM assignment is that you don't have to screw with rsync and kpartx and sfdisk, etc. You just copy the image file and you're pretty good to go.
You get a lot of duplicated blocks that way, though.

---

### Post by paulisdead on 2010-09-23
This is the script I use for home backups, I have this machine and a couple others back up to /var/backup/ on my home file server for quick access.  Once it's done with that, it mounts a USB drive, and then dumps /var over to the USB drive, since I want some other stuff in /var dumped over to it.  Since I don't want to backup all the binaries, just the configs, I dump out the list of installed packages, so I can easily feed that list back into apt-get and have it reinstall everything, and since I have /etc backed up, I can then easily restore the configs for anything I need.

```
#!/bin/bash
/usr/bin/dpkg --get-selections > /etc/installed-software
/usr/bin/rsync -avrt --exclude 'mtab' /etc /var/backups/hal9000/
/bin/mount /mnt/backup
/usr/bin/rsync -avrt --exclude 'cache/apt' --exclude 'cache/apt-cacher-ng/' --exclude 'cache/man'  /var/ /mnt/backup/var/
/usr/bin/rsync -avrt --exclude 'smb/videos/' --exclude 'smb/downloads' --exclude 'smb/backup/Linux/' --exclude 'smb/backup/images/' /home/ /mnt/backup/
/bin/umount /mnt/backup
```

When I lost the hard disk in my home DNS/SSH/DHCP server, it took me just over an hour to replace the disk, reinstall debian (I use apt-cacher-ng as an apt proxy, so I had a copy of all packages sitting on my server), import the package list, bring over the config files, and get it up and running again.

Unless you use the --delete flag with rsync, it shouldn't be deleting files in the destination folder that no longer exist in the source folder.

If anyone is looking for a real managed backup solution, that can fully backup windows and linux clients, plus the OS files, I recommend bacula.  I use it at work to backup our servers, but it's way overkill for a few home machines.

---

### Post by SeijiSensei on 2010-09-23
> **Plecebo said:**
> I think the idea is that rsync can protect you from hardware failure, since you can restore to your most recent rsync, however if you delete a file and run rsync you still don't have a backup of the file.

Unless you use the one of the various --delete options, rsync won't remove files from the backup directory just because they don't exist on the source.

Sorry, I just noticed that paulisdead made this point as well.

---

### Post by amac777 on 2010-09-23
> **SeijiSensei said:**
> Unless you use the one of the various --delete options, rsync won't remove files from the backup directory just because they don't exist on the source.

What about if you inadvertently change a file (or it gets corrupted/malware etc) and you need to go back to an earlier version?

"rsnapshot" is another good option that will efficiently keep snapshots using rsync and hardlinks so you can recover older versions of files.

---

### Post by djanie78 on 2010-09-23
> **paulisdead said:**
> This is the script I use for home backups, I have this machine and a couple others back up to /var/backup/ on my home file server for quick access.  Once it's done with that, it mounts a USB drive, and then dumps /var over to the USB drive, since I want some other stuff in /var dumped over to it.  Since I don't want to backup all the binaries, just the configs, I dump out the list of installed packages, so I can easily feed that list back into apt-get and have it reinstall everything, and since I have /etc backed up, I can then easily restore the configs for anything I need.

```
#!/bin/bash
/usr/bin/dpkg --get-selections > /etc/installed-software
/usr/bin/rsync -avrt --exclude 'mtab' /etc /var/backups/hal9000/
/bin/mount /mnt/backup
/usr/bin/rsync -avrt --exclude 'cache/apt' --exclude 'cache/apt-cacher-ng/' --exclude 'cache/man'  /var/ /mnt/backup/var/
/usr/bin/rsync -avrt --exclude 'smb/videos/' --exclude 'smb/downloads' --exclude 'smb/backup/Linux/' --exclude 'smb/backup/images/' /home/ /mnt/backup/
/bin/umount /mnt/backup
```

When I lost the hard disk in my home DNS/SSH/DHCP server, it took me just over an hour to replace the disk, reinstall debian (I use apt-cacher-ng as an apt proxy, so I had a copy of all packages sitting on my server), import the package list, bring over the config files, and get it up and running again.

Unless you use the --delete flag with rsync, it shouldn't be deleting files in the destination folder that no longer exist in the source folder.

If anyone is looking for a real managed backup solution, that can fully backup windows and linux clients, plus the OS files, I recommend bacula.  I use it at work to backup our servers, but it's way overkill for a few home machines.

Damn there as some clever people in this joint. You all make the world go round

---

### Post by david.macquigg on 2010-11-05
rsync sure seems like the best way to do backups for anyone who can write a script, or even just modify one that somebody else has written.  Certainly no more difficult than figuring out all the settings in a black box like Acronis, and then you have a script you understand thoroughly.

I've got a Python script running as a cron job, keeping a fully-synchronized copy of all my program and data files on an external disk.  This script runs every night, and it also makes copies so I can keep snapshots of the system 1, 2, 4, and 8 days ago.  Everything is now backed up except the /proc and /sys directories.  I'm assuming those can be left as-is when I restore all the old files to a new hard disk with a system built from my original Ubuntu CD.  Is that a safe assumption?  Is there a better way to do this?

Here is the core of my script.  /media is the external drive.

```
src = '/'
excludes = "--exclude '/media' --exclude '/proc' --exclude '/sys'"
command = "rsync -a --delete %s %s %s"  %  (excludes, src, dest)
```

---

### Post by paulisdead on 2010-11-05
When you do the restore, the /proc and /sys folders need to exist, but don't need anything in them.  They're not actually folders on the disk, but a representation of the running kernel in memory.

If I've got a full backup including the binaries, or just want to transfer an existing install to another drive, I wouldn't do a full reinstall.  In the past, I took a livecd, partition the drive, mount all the partitions into the running livecd's os to somewhere like /mnt/ubuntu.  Then I copy all the files back into place.  It's very important to make sure your backups preserve permissions, and when you restore that you keep the original permissions.  A 'cp -Rp' will do it (note the capital R, so it picks up hidden files/folders), as will 'rsync -ar' work.  Once the files are copied in place, you need to fix up the fstab.  Use blkid to determine the new UUIDs of the partitions, and then put them into the new fstab.  You then need to mount /proc and /dev from the livecd's folders into the copied folder for the next step.  You can do it like this 'mount -o bind /proc /mnt/ubuntu/proc'.  The final step is to reinstall the bootloader by cd'ing into the new install and chroot into it, 'chroot /mnt/ubuntu /bin/bash' then a grub-setup && grub-install should do it, and you can exit and unmount everything and reboot.

---

### Post by david.macquigg on 2010-11-06
Paul, thanks for the tips on setting up fstab, grub, etc.  I did a little more searching and found a discussion of these procedures at [https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)  I'm hoping I don't need to do all this.  I don't need the backup copy itself to be a bootable system.

My goal is easy recovery from a failed main disk - less than two hours, including a trip to the store to pick up a new hard disk. I'm wondering if it would be possible to just boot from the original CD, install a minimal working system on the new hard disk, then restore my program and data files from the backup disk.

I know this won't work with Windows.  The Registry and other "lock in" tricks that M$ has devised, force a complete re-install of the OS and all programs.  I learned this the hard way, and that is what finally made me move off of Windows.

A well-designed system like Ubuntu should have all of its system stuff nicely encapsulated.

---

### Post by LightningCrash on 2010-11-06
David this is one of the areas that kickstarts, preseeds and configuration management(ie puppet/cfengine/chef/bcfg2) excel in.

I can provision and install an OS on bare metal in 10 minutes with kickstart/puppet. Every aspect of the system is configured in puppet. If I install a new OS on the same host, puppet is going to come back in and configure it exactly the way it was before it tanked.
As you see, at some point I do not care about the OS itself, only the data files that go with the host.

My ideal recovery situation goes as such:
[LIST=1]
[*]Kickstart
[*]Sign the puppet certificate req
[*]Force a puppet run
[*]Restore data partitions from backups
[/LIST]
In the case of servers with SAN HBA/CNAs, I don't even have to worry about the data files... they're on the SAN. ;)

Much easier than trying to worry about the state of the OS in my backups.

---

### Post by paulisdead on 2010-11-06
> **david.macquigg said:**
> Paul, thanks for the tips on setting up fstab, grub, etc.  I did a little more searching and found a discussion of these procedures at [https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)  I'm hoping I don't need to do all this.  I don't need the backup copy itself to be a bootable system.

My goal is easy recovery from a failed main disk - less than two hours, including a trip to the store to pick up a new hard disk. I'm wondering if it would be possible to just boot from the original CD, install a minimal working system on the new hard disk, then restore my program and data files from the backup disk.

I know this won't work with Windows.  The Registry and other "lock in" tricks that M$ has devised, force a complete re-install of the OS and all programs.  I learned this the hard way, and that is what finally made me move off of Windows.

A well-designed system like Ubuntu should have all of its system stuff nicely encapsulated.

That's pretty much what I described with the script I posted above.  I backup /home and /etc, which will have all the actual configurations in it.  I take that installed-software file and import it, like this on a new install
```
dpkg --set-selections < installed-software
dselect
```
To get the apps reinstalled, then I can copy over anything from the /etc backup I need.  All of /home can be restored to it's new location.

One beautiful thing about *nix type OSes, is that everything is a file, and you can easily just copy it around, clone whole drives easily, etc.  So just as long as you preserve the permissions, a copy of the OS will work, unlike windows.

You could do a kickstart as well.  I generally have different package sets and additional repos installed on my different boxes, since they're used for varying tasks, so a global list isn't the best for me.

I pretty much described restoring a system in about 2 hours above.  Apt-cacher-ng really helped that, since I had a local copy of all the packages on my server, and didn't have to download them from the internet.  Another catch is I had the hard drive laying around.  An apt proxy might be overkill, plus it takes up space on a machine to cache those packages.

SANs are cool stuff, but not typically found around the house.  Puppet also seems kind of overkill for most people's home usage.  The amount of additional hardware and electricity for a SAN isn't something most people are going to invest in.  An external drive is probably the best solution for most home users.  Even if you've got a SAN, external drives still make a great offsite back up solution.

---

### Post by LightningCrash on 2010-11-06
> **paulisdead said:**
>  Even if you've got a SAN, external drives still make a great offsite back up solution.

Most people who can afford SANs can afford the single mode fiber offsite for another, offsite SAN :)

---

### Post by david.macquigg on 2010-11-09
SANs, RAID arrays, Kickstart - this is all overkill for a small office with three computers and no sysadmin.  I need something like Time Machine on the Mac, backing up everything automatically every hour.  I'm surprised that Ubuntu doesn't have this already in the standard distribution.

I've discovered a few minor problems with rsync, not enough stop using my script, but hopefully will be improved in the future.  Compared with Time Machine, full-system backups are painfully slow and take a lot of disk space.  On my Macintosh, a typical hourly backup takes 40 seconds, and after 8 months my external USB drive is up to 118GB.

Using rsync with the --link-dest option, a typical full-system backup takes 32 minutes and adds 5 GB to my backup disk.  Clearly, this is not an hourly cron job.  I run it once a night, and delete old backups before the disk gets full.

I also keep a modified copy of the script in each project directory, and run it manually whenever I work on the project.  A typical project backup takes about 1 second, and add 5 MB to the backup disk.  Between the nightly system backups and manual project backups, I think I'm pretty well covered.

I gave up on my Python script, and am now using a modified version of RLBackup.  Lots of nice logging and other tedious stuff I don't want to re-invent.

---

### Post by CharlesA on 2010-11-09
You are rsyncing to a seperate folder each time, correct?

That would explain why it takes half and hour and uses 5GB of space.

---

### Post by david.macquigg on 2010-11-09
> **CharlesA said:**
> You are rsyncing to a seperate folder each time, correct?

That would explain why it takes half and hour and uses 5GB of space.

If I rsync to the same destination folder each time, no space is wasted, but older versions are lost.  Time Machine allows me to recover files from any time in the past.

I think the key to providing fast, compact backups is to avoid replicating the entire directory structure when only a few files have changed.  The /usr directory, for example, could be nothing but a link in the root directory, pointing to the most recently modified /usr directory.  rsync uses hard links, and hard links can't point to directories (I don't know why).  Time Machine seems to have found a way around this problem.

---

### Post by CharlesA on 2010-11-09
I use cp -al and rsync to do the incremental backups. That would probably let the backups not take up a load of space or a long time to backup.

The script is probably very confusing, but I could post it if you want.

---

### Post by david.macquigg on 2010-11-09
> **CharlesA said:**
> I use cp -al and rsync to do the incremental backups. That would probably let the backups not take up a load of space or a long time to backup.

The script is probably very confusing, but I could post it if you want.

I don't see how cp -al can help, since each incremental backup must include fresh copies of all directories in the tree, even when none of the files have changed.  How does your script avoid making copies of directories that haven't changed.  I could do it with symbolic links, but that would ruin the backup.  Directories full of symlinks are not the same as the original.

At 4K per directory, copying all directories takes a lot of space. 
Example:  I just did an incremental of my entire home directory (772 items, totaling 957.3 MB).  RLBackup reports that 44 files were transferred, totaling 90.4 MB.  It took 61 seconds, almost all of it in processing the directories.

---

### Post by CharlesA on 2010-11-09
I do it with hard links, one of the nice things about the linux file system.

---

### Post by david.macquigg on 2010-11-09
How do I make a hard link to a directory?
```
$ ln /home/david
ln: hard link not allowed for directory
```

---

### Post by CharlesA on 2010-11-09
I don't think it hard links the directories, since they are directories, but it does it for all the files. Then it rsyncs the files. *shrugs* It's worked fairly well for me so far.

The script I use is pretty crappy, but it gets the job done:

```
#!/bin/bash

###
### monthly.sh
### Script for monthly document backup
### Created by Charles
### Tested 10/03/2010
### Updated 10/03/2010
###

BIN=/bin/
USR=/usr/bin/
ARRAYPATH=/array/
MONTHLYPATH=/monthly/
HOME=/home/charles/
ERR=${HOME}logs/monthly_backup_error.log
DATE=$(${BIN}date +%D)
FOLDER=$(${BIN}date +%m%d%Y)

if ${BIN}mountpoint -q $ARRAYPATH
then
  { ${BIN}mount -t ext4 UUID=f00c8f27-7a11-42b0-96f9-0e04a261d682 $MONTHLYPATH; } 2> $ERR || { echo "Mounting of backup drive failed"; exit; }
else
  { echo "$ARRAY not mounted!"; exit; }
fi

OLDMONTHLYNAME=$(${BIN}cat ${MONTHLYPATH}latest)
NEWMONTHLYDIR=$MONTHLYPATH$FOLDER
OLDMONTHLYDIR=$MONTHLYPATH$OLDMONTHLYNAME
MONTHLYLOG=${MONTHLYPATH}log/${FOLDER}.txt

# rsync
if ${BIN}mountpoint -q $MONTHLYPATH
then
  { ${BIN}cp --archive --link $OLDMONTHLYDIR $NEWMONTHLYDIR && echo $FOLDER > ${MONTHLYPATH}latest && ${USR}rsync --archive --itemize-changes --delete --log-file $MONTHLYLOG $ARRAYPATH --exclude dvds --exclude lost+found $NEWMONTHLYDIR && ${BIN}umount $MONTHLYPATH; } 2> $ERR || { echo "Monthly backup failed."; exit; }
fi
# eof

```

---

### Post by david.macquigg on 2010-11-09
OK, there are no links to directories, therefore, every backup must include a copy of every directory in the tree that is backed up.  Try backing up a large tree like my earlier example, after changing just one small file.  Run df to see how much disk is actually used before and after the backup.  I think you will get the same results as I got.

rsync is just not able to do "Time Machine" style backups, given the limitations of hard links to directories.  I've tried this with both ext4 and NTFS filesystems in Ubuntu.

Note: I can make hard links to directories in Mac OSX, so this may be a fundamental difference between these systems.

---

### Post by CharlesA on 2010-11-09
I suppose it would add up after a while, but check this:

```
charles@thor:~$ du -h --max-depth=1 /cdrom/
1.4T    /cdrom/05312010
15G     /cdrom/07192010
53G     /cdrom/09042010
1.6M    /cdrom/08182010
1.6M    /cdrom/07152010
1.6M    /cdrom/09182010
1.6M    /cdrom/09142010
1.6M    /cdrom/05252010
1.6M    /cdrom/10182010
1.6M    /cdrom/06072010
1.6M    /cdrom/06162010
1.6M    /cdrom/07052010

```

So, yeah it takes some space, but not all that much if the files haven't changed.

---

### Post by Vegan on 2010-11-09
I use tar and gzip to make backups. The rsync tool is not as effective in my opinion for backup.

I see rsync as more of a replication tool for server roll over.

What I do is use a sump of MySQL and then tar up everything else I want to backup.

Now I have a DVD burner to write too, or I could cp them to another machine. If you have a take drive, that is another option.

tar is a better backup tool compared to other solutions I have seen.

I have looked in this area a lot. And every alternative has fell short compared to the way I do it now.

---

### Post by david.macquigg on 2010-11-10
Vegan, gzipped tar files are really inconvenient for browsing and recovering a single file from an old backup. rsync was designed as an alternative.  Each of us has different expectations, but for my small office, the features of the Time Machine are really ideal.  I just need to figure out how to make rsync do that more efficiently.

Charles, your cp --archive --link command is indeed making hard links to subdirectories in my destination directory!!  This is surprising since not even ln will do that.  This also tells me that the prohibition against hard linking to directories is not a limitation of Linux or of the file system, but something specific to rysnc and ln.  I'll have to experiment with this and get back to you.

---

### Post by CharlesA on 2010-11-10
Glad you are able to figure it out. :)

I don't use tar because it would be a major pain in the butt to grab a specific file from within the tar archive without using something like 7zip to open the archive.

---

### Post by david.macquigg on 2010-11-10
I've got some results comparing Charles' method to that in RLBackup.  Using cp -al to set up the link tree *before* the rsync command is orders of magnitude faster and smaller than using the --link-dest option in rsync.  

In both tests, I backed up my home directory (2125 files, 1.34GB).  In both tests, I started with a backup already in place, and did an incremental backup to a new directory.  26 files were updated, with a total data transfer of 90MB.

For TestA I ran RLBackup with no modification other than setting the directories for source, destination, and exclude files.
[http://ubuntuforums.org/showthread.php?t=912460&highlight=rsync+backup]("http://ubuntuforums.org/showthread.php?t=912460&highlight=rsync+backup")

For Test B I left out the --link-dest option on the rsync command, and inserted a cp -al command just ahead of rsync.  The hacked script then has these lines:
```
LASTBAK=back-2010-11-09_11-32-35       ### need to automate this
cp -al $DESTPATH/$LASTBAK $BACKUPNAME     ### make links with a local copy
rsync $OPT $SOURCE $BACKUPNAME > $OUTPUTLOG   # no link-dest in $OPT
```
```
                        Test A     Test B
 Time (seconds):            59          3
 Disk usage (MB):         1300         87
```

---

### Post by CharlesA on 2010-11-11
Wow. Thanks for posting the results. I didn't know it would make that much of a difference.

You need to automate creating the folder for the new backup, right?

My script does that based on the output of date, so maybe that'll be of some use to you. :)

---

### Post by senor_smile on 2010-11-11
> **david.macquigg said:**
> OK, there are no links to directories, therefore, every backup must include a copy of every directory in the tree that is backed up.  Try backing up a large tree like my earlier example, after changing just one small file.  Run df to see how much disk is actually used before and after the backup.  I think you will get the same results as I got.

rsync is just not able to do "Time Machine" style backups, given the limitations of hard links to directories.  I've tried this with both ext4 and NTFS filesystems in Ubuntu.

Note: I can make hard links to directories in Mac OSX, so this may be a fundamental difference between these systems.

I would recommend trying out backintime if you want a comparable solution to the mac's time machine.  I use it for backing up my home directory while at work. It requires a gui (i.e. gnome or kde).  It uses rsync, diff and hard links to do exactly what it sounds like you want to do.  It might not work for exactly what you need, but I wanted to throw it out there as no one else had.

---

### Post by david.macquigg on 2010-11-11
backintime looks nice, but it is just  a GUI frontend for rsync, which I don't really need, because I won't be needing interaction with my backup script.  A well-written script should be as easy to use as a GUI, especially if the parameters a user needs to change are at the top of the script, and well-explained in the text.  Take a look at the script for RLBackup as a nice example.

@Charles - your script stores the name of the last backup in a file.  RLBackup stores it in a link 'current-0'.  So to retrieve the name in RLBackup, I could use a command like
```
ls -l $DESTPATH/current-0
lrwxrwxrwx 1 root root 56 2010-11-10 18:36 /media/sdb/RLBackups/home/david/current-0 -> back-2010-11-10_18-36-01
```
I still need to extract the file name from the end of this string, and at this point, I will write a function in Python, and just call it from my bash script.
```
LASTBAK=`rlbfuncs.py lastbak $DESTPATH`
```
Maybe someone can suggest a way to do this directly in bash.  I lost interest in shell scripting languages after discovering Python.

---

### Post by CharlesA on 2010-11-11
I've not used RLBackup, but I am not sure how you can read the filename from the link.

It looks like it just adds the data and time.

I'll poke around a little and see if I can find a way to echo the path to a variable.

EDIT: [Found it]("http://www.linuxquestions.org/questions/linux-software-2/how-to-find-symlink-target-name-in-script-364971/").

There's a command called readlink.

```
charles@luna:~$ ls -l
total 4
drwxr-xr-x 2 charles charles 4096 2010-11-11 10:02 back-2010-11-10_18-36-01
lrwxrwxrwx 1 charles charles   24 2010-11-11 10:03 current-0 -> back-2010-11-10_18-36-01
charles@luna:~$ readlink current-0
back-2010-11-10_18-36-01

```

Throwing it into a variable would probably look something like this:

```
LASTBAK=$(readlink $DESTPATH/current-0)
```

---

### Post by david.macquigg on 2010-11-11
readlink does the trick.  Thanks.  Here are my diffs, if anyone wants to experiment with RLBackup.
```
161c163
<  OPT_LINKDEST=--link-dest=$DESTPATH/current-0
---
>  # OPT_LINKDEST=--link-dest=$DESTPATH/current-0  # links are done with cp ###
238a241,242
>  LASTBAK=$(readlink $DESTPATH/current-0)  # back-2010-11-09_11-32-35  ###
>  cp -al $DESTPATH/$LASTBAK $BACKUPNAME    ### make links with a local copy
```

I've made one other improvement in performance, and I can now back up my entire home directory in one second, instead of 3.  There was a file in my home directory: .xsession-errors, which was accounting for almost all of the 90MB of data transferred on each backup.  I wouldn't have noticed it without the excellent logfiles from RLBackup.  Anyway, moving this file to ~/tmp, avoids having it clog every backup.

There really is something wrong with the --link-dest option in rsync.  I'll ask the folks at Samba.org if they know anything about this.

---

### Post by CharlesA on 2010-11-11
Might want to file a bug report over on launchpad about rsync too.

---

### Post by SilverWave on 2010-11-18
> **david.macquigg said:**
> 
Charles, your cp --archive --link command is indeed making hard links to subdirectories in my destination directory!!
Well that's very interesting :-) 

I didn't think hard-linking directories was possible...

it couldn't be that this command hard links files but copies directories?

---

### Post by CharlesA on 2010-11-18
> **SilverWave said:**
> Well that's very interesting :-) 

I didn't think hard-linking directories was possible...

it couldn't be that this command links files but copies directories?
I just know that it does hard links of the files, but I don't think it does them on the directories, probably just creates them or copies them like normal.

This is from the man page of cp:

```
       -l, --link
	      link files instead of copying

```

---

### Post by david.macquigg on 2010-11-19
I was mistaken.  "cp -al" does *not* making hardlinks to directories. It does on my Mac, but not on my Ubuntu system.   "ls -l" shows only one link to each directory in the backup copies.  That means the entire directory tree is copied in full with each incremental backup, even if only one file has changed.  So I have no explanation for the difference in performance between my hacked script and the original RLBackup.  (See my post here last week.)

I checked Bugzilla for rsync, and there is a report #6746 on problems with the --link-dest option.  It's about a year old, and I see there are hundreds other of bug reports needing attention.  I wish I had more time, so I could follow up on this.   My nightly backups take about two hours, including an hour just for the final du command to scan all the directories and report the size of the backup.  The disks may fail early because of continuous heavy load.

---

### Post by CharlesA on 2010-11-19
I don't know why there is a huge performance difference either. I know mine works, but running du on an external drive will take a while, since it's got a ton of directories to read.

I don't really think that it'll wear out the drive any faster then it would normally wear out tho.

---

### Post by david.macquigg on 2010-11-19
See my last post at [http://ubuntuforums.org/showthread.php?t=912460&page=2](http://ubuntuforums.org/showthread.php?t=912460&page=2) for some typical performance measurements.  This is actually a second internal drive.  I assume a USB drive would be slower, and a backup to a remote machine might be impossibly slow.

Drive life is dependent on time, heat, and head motion.  Normally, my drives sit idle, with no head motion.  During a backup, the heads are thrashing continually for two hours.  The drive indicator light is ON without any break.

---

### Post by CharlesA on 2010-11-19
That makes sense, I suppose.

I backup to USB and the only time it's really slow is if I am backing up a ton of data (many hundreds of gigabytes).

My environment is different then yours, since I'm only backing up a small number of files (most stuff I've got is media that never really changes), but even my monthly backups take around 5 to 15 minutes to complete over USB 2.0.

Restores, on the other hand, take between 12 to 15 hours, since there's a ton of data that has to be copied back over.

---

### Post by SilverWave on 2010-11-19
> **CharlesA said:**
> That makes sense, I suppose.

I backup to USB and the only time it's really slow is if I am backing up a ton of data (many hundreds of gigabytes).

My environment is different then yours, since I'm only backing up a small number of files (most stuff I've got is media that never really changes), but even my monthly backups take around 5 to 15 minutes to complete over USB 2.0.

Restores, on the other hand, take between 12 to 15 hours, since there's a ton of data that has to be copied back over.

Yes I think the du times for [david.macquigg]("http://ubuntuforums.org/member.php?u=1146651")'s disks are telling. I think he has a problem related to his drive :sad: 

e.g. its very slow for some reason.

Here are my latest times using RLB.

> **SilverWave said:**
> My backup time was **6 mins** for 946,163 files (checked) 48,703 new/changed files (Copied)  (Size of copy 3.10Gb).

I am using another hard disk for storing the backup not a USB Disk.

```
[RLB (Rsync Local Backup). An easy way to backup your system]("http://ubuntuforums.org/showthread.php?t=912460")
/backup/dr/Backups
/backup/dr/Backups

rsync -ahvv  --log-file=/backup/dr/Backups/back-2010-11-19_18-49-26-LOGFILE.txt  --link-dest=/backup/dr/Backups/current-0  --exclude-from=/backup/dr/myscripts/rlbackup1exclude.txt --stats /  /backup/dr/Backups/back-2010-11-19_18-49-26

LINK: -File: `/backup/dr/Backups/current-0' -> `back-2010-09-26_12-26-33'
EXTRACT0: -/backup/dr/Backups/back-2010-09-26_12-26-33
LINK: -File: `/backup/dr/Backups/current-1' -> `/backup/dr/Backups/back-2009-11-06_22-10-06'
EXTRACT1: -/backup/dr/Backups/back-2009-11-06_22-10-06
LINK: -File: `/backup/dr/Backups/current-2' -> `/backup/dr/Backups/back-2009-10-27_17-59-45'
EXTRACT2: -/backup/dr/Backups/back-2009-10-27_17-59-45
============================================================

Free Space on /backup/dr/Backups
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  396G   40G  91% /backup

============================================================

Backup started:

Fri, 19 Nov 2010 18:49:26 +0000

Backup finished:

Fri, 19 Nov 2010 18:55:32 +0000

============================================================

Free Space on /backup/dr/Backups
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  399G   37G  92% /backup

============================================================

Statistics

Number of files: 946163
Number of files transferred: 48703
Total file size: 26.20G bytes
Total transferred file size: 3.10G bytes
Literal data: 3.10G bytes
Matched data: 0 bytes
File list size: 22.07M
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 3.12G
Total bytes received: 1.04M

sent 3.12G bytes  received 1.04M bytes  8.52M bytes/sec
total size is 26.20G  speedup is 8.39

``````
============================================================

Fri, 19 Nov 2010 18:55:37 +0000

Actual usage for the last 4 backups:
37G    /backup/dr/Backups/back-2009-10-27_17-59-45
947M    /backup/dr/Backups/back-2009-10-27_17-59-45
3.8G    /backup/dr/Backups/back-2009-11-06_22-10-06
15G    /backup/dr/Backups/back-2010-09-26_12-26-33
3.3G    /backup/dr/Backups/back-2010-11-19_18-49-26
60G    total

Fri, 19 Nov 2010 18:58:06 +0000

============================================================

Done.
```

3.3 -3.1 = 200M overhead for the hard links.

---

### Post by david.macquigg on 2010-11-21
I found the source of my original problem with RLB, and I have now switched back to the original script, which does not use "cp -al" before the rsync command.  See the recent posts to [http://ubuntuforums.org/showthread.php?t=912460&page=2](http://ubuntuforums.org/showthread.php?t=912460&page=2) for a full discussion, but a quick summary is that I was using the wrong type of filesystem on my backup drive.  This drive was originally formatted as NTFS.  I changed it to Ext4, and now I'm getting much better times - 3 minutes for the initial full-system backup to an empty directory, and 30 seconds for the nightly incremental backup.

I don't understand why your full-system restore is taking 10 to 15 hours.  This should be no more than the time it takes to do a full-system backup.  Just use rsync in reverse.

---

### Post by CharlesA on 2010-11-21
You were using an NTFS formatted drive before? That would be the reason why it was taking so long, since NTFS doesn't support hardlinks.

A full-system restore for me is around 2TB of data being transfered over USB 2.0 = takes a long long time.I guess I shouldn't have called is a "system restore" since it's just a backup of my data. The OS isn't backed up, since I can just reinstall it.

---

### Post by LightningCrash on 2010-11-21
> **CharlesA said:**
> I don't use tar because it would be a major pain in the butt to grab a specific file from within the tar archive without using something like 7zip to open the archive.

tar xvf backup.20101120.tar path/to/wordfile.doc

works great

---

### Post by CharlesA on 2010-11-21
> **LightningCrash said:**
> tar xvf backup.20101120.tar path/to/wordfile.doc

works great

Hrm. Didn't know it worked like that. Thanks. :)

---

### Post by LightningCrash on 2010-11-21
> **CharlesA said:**
> Hrm. Didn't know it worked like that. Thanks. :)

My main beef against tar is that it's a big binary blob and it cannot easily be deduplicated.

If I were using tapes I might have a different perspective... but I'm doing disk<->disk at home and at work.

ETA: It's great for quick backups of stuff, though.

---

