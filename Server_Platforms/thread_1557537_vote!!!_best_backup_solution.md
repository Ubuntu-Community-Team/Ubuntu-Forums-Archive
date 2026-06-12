---
title: "vote!!! best backup solution"
date: 2010-08-20
forum: Server Platforms
---

### Post by andrewuy8888 on 2010-08-20
hi all!

new to the forum and ubuntu as well, but i really like ubuntu!

looking for a centralized backup solution to backup:

1. srv01 (openldap,dhcp,dns)
2. srv02 (nfs file server)

here are the requirements, (or what i'm thinking anyways)

3sets of backup:

1st set: (local backup)

full backup at 12 midnight on day 1
incremental backup hourly, monday - fri from 7am till 6pm, saturday 7am till 12noon
backup overwrites the 7day old data

2nd set: (offsite backup) through external usb hard disk (3 disks)

disk01 extract every saturday 1pm
then every saturday you can just umount and mount the 3hdds so it will cycle.

3rdset: NAS (freenas maybe and mount it in fstab) weekly dump

not really sure how to do this but basically that's the idea, one local backup set that will reside in the server, 3hdd external usb for offsite use weekly.

would be nice if the backup dumps it to a folder with a date format.

i'm open to suggestions on the backup scheme.  just want this automated.

any help would be much appreciated!

thank you very much!

*note:  aside from backup, i hope the restoration is simple too :)

---

### Post by koenn on 2010-08-22
have a look at rsync

the --backup and --backup-dir options will allow you to do differential backups 

you can target the appropriate destinations by using $(date +%A) in the backup folder path 

rsync can copy to local disks as well as over a network, so can also use it to backup to your NAS. Alternatively, you can use an NFS share from the NAS.


once you have somethings that works, make a cron job to schedule it.

---

### Post by Vegan on 2010-08-22
I still use the antique TAR tool. The I gzip it up and then I can move it to a USB disk or some other safe place.

I have also looked at Bacula which is not as ubiquitous as TAR.

---

### Post by andrewuy8888 on 2010-08-22
@koenn

that would be

rsync –azvv /home/ /data/$(date +%A)

right?

restoring would be opening the backup and replacing the file manually?

offsite would be making one more schedule to the usb drive (mounted) right?

hmmm... is there any other better like with a gui or something? :)

---

### Post by psusi on 2010-08-22
A conventional backup tool creates an archive file that contains the relevant backup information; rsync simply copies files.  It is essentially a smart version of cp that figures out how to transmit/copy only the files/parts that have changed when you are copying over a file that already exists.

You can use rsync to make a full copy of your files and then update that copy hourly.  You can even use hard links to create separate versioned directories so you can have one for each hourly backup, but files that are unchanged between backups don't take up more space.  Restoring is as simple as copying all of the files back and you can easily browse the backups and pull out old copies of specific files with your usual file browser.

The disadvantage of this is that it requires that you have a disk large enough to hold the entire set of files with some room to spare for any files that change between backups.  It also requires that the disk be online and fully accessible to make another backup.

With a conventional backup tool like tar, you can create an incremental backup without needing access to wherever you have stored any of the other backup archives.  The archives can easily be compressed, split up, emailed, and so forth.

One issue you are likely to run into backing up in a server environment is open files.  Any file that is open ( for writing ) during the backup is likely to be corrupted since it may not be fully written when it is backed up.  This is why backups historically were done only done late at night, when the server could be taken offline and all files closed.

Lately I have been using the old dump tool for backup.  It requires that you unmount the filesystem and it directly scans the disk looking for files to backup, rather than accessing them via the usual kernel file apis.  This makes it somewhat fast.  It also encourages the use of the tower of hanoi backup pattern, where you take a full backup only once ( ever, each year, or each quarter ) then the nightly dumps rotate between between a set of tapes in a tower of hanoi patern.  This lets you keep only 5 nightly backup tapes where you always have at least 3 old versions of any file up to a month old, and if one of them goes bad, the worst thing that happens is you end up with files a bit older than your most recent backup, rather than loosing them completely.  If you want you can duplicate the full backup tape(s) and store a copy off site.  You can also do this with the level 1 dumps to make sure you also have an off site copy of more recent files than the full, and only have to transport them off site twice a month.

To avoid the inconvenience of unmounting the fs to dump it, I stop apache, mysql, and other things that could have open files, then take a snapshot, restart the servers, and dump the snapshot.  This is all done automatically by a shell script run by cron each night at 1 am.

---

### Post by koenn on 2010-08-23
> **andrewuy8888 said:**
> @koenn

that would be

rsync –azvv /home/ /data/$(date +%A)

right?

That will give you 7 **full** backups

I was more thinking along the lines of
```
rsync --delete --backup --backup-dir=/backup/$(date +%A) -avz /data/ /backup/current
```

That should give you 1 full backup in .../current + 7 diffs : with each run, the files that rsync adds to or modifies in .../current, will also be put in today's backup-dir. 
 "current" is the most recent backup and it's a full backup, but you also have 7 days of history which are smaller

Caveats:
1- I might be off by a day here, you'll need to look it up or try it
2- this is counter-intuitive if you're used to "conventional" backups where the full backup is *older* than the diffs. 




> restoring would be opening the backup and replacing the file manually?
for single files, yes. 
You can also rsync in the oposite direction,  from /backup/... to /data, to restore entire dirs+subdirs
note that too revert to an older backup, eg last Friday, and you need entire directories, you'd have to rsync from /backup/current, and then also form /backup/Friday, because *some files* in /current will be newer than "Friday". 

> 
offsite would be making one more schedule to the usb drive (mounted) right?

yes. You could either rsync /data again, to your usb drive, , or rsync /backup (better: diffs included). Likewise for your NAS

> 
hmmm... is there any other better like with a gui or something? :)
There probably are things with GUI but I don't know if they are better. 

I think rsync is pretty powerful, but you really need to test your setup to make sure you backup everything you need to backup, and that you know how to do a restore.

---

### Post by scorp123 on 2010-08-23
Best backup solution? Bacula. Hands down. Heck, I even know a few Swiss banks where they use it ... 

[http://www.bacula.org](http://www.bacula.org)

---

### Post by Vegan on 2010-08-23
I find TAR meets my needs well. The old backup.tar.gz is an old standby that is well supported and easy to copy to any convenient location.

---

### Post by scorp123 on 2010-08-24
> **Vegan said:**
> I find TAR meets my needs well. Sure, "tar" works tip top if you just have to backup one single system. I do that at home too.

But the OP asked about a *"centralised backup solution"* ... and if you really want that e.g. because you have dozens of systems that you have to take care of then there is no way around backup solutions such as Bacula.

Just my 0.02&#8364; :)

---

### Post by awe on 2010-08-24
I've been using Dirvish for quite a while and it meets all my needs. It's in the repositories. The Debian How-To from the Dirvish website is a good kickstart. Furthermore, I do a daily mysql-dump of all databases in addition to the Dirvish backup, simply because if I come up with a problem in one particular database mysql dumps are the easiest way to restore data. You can Cron it all (Dirvish comes with a sample cron job description).

If you are to do an out-of-house backup (which is a very good idea) you can edit the Cron job for Dirvish so that it will copy the newly-created backup onto a remote computer, meaning that you no longer need to bother going to the server with an external disk.

---

### Post by andrewuy8888 on 2010-08-26
@psusi wow, i don't think my skill level is par or even near to comprehend what you are recommending :) i'll have to read through it again.

@koenn thank you for the detailed command, i will try this :D

@scorp123 will check out bacula, hmmm... web gui!!! \\:D/

thank you!

if you guys know of any other good/easy/stable way for backups and also recommend a backup strategy, please do post.  my backup strategy may not be adequate or too complicated, please feel free to comment.

thank you!!!

---

### Post by psusi on 2010-08-26
Figuring out dump from the documentation is a bit tricky.  It seems rather complicated at first, but once you wrap your head around it, it is kind of neat and you can stop worrying about it.

The important thing to understand is that dump backs up only files that have changed since the most recent dump of a lower level.  So you start with a level 0 dump to get everything, then you can alternate up and down higher levels to dump different sets of files.  If you just did 0, 1, 2, 3, 4, 5 each day that would be same as a setup with tar doing a full backup on sunday, then an incremental backup each other day of the week.  Each incremental only contains files that changed since the day before.  The down side to this is that you have to spend a lot of time doing a full backup every week, and if you change a file on tuesday, the new version goes in tuesday's backup, and only tuesday's backup ( unless you change it again ), so if on Friday your drive crashes and tuesday's tape went bad, you have lost the new version of that file.

When you cycle up and down between levels 1-5, that file you change on Monday ends up in multiple backups by Friday so you have some redundancy should a tape go bad.  Also since dump backs up all files that changed since the last lower level dump rather than yesterday's dump, when you overwrite a tape with a newer dump, you don't loose the files that were backed up to that tape last time.  This is what allows you to keep reusing the same set of 5 tapes without having to make another full backup every week.

Here is my dump script:

```

#!/bin/bash
set -e
declare -a LEVELMAP=(1 5 4 5 3 5 4 5 2 5 4 5 3 5 4 5 1 5 4 5 3 5 4 5 2 5 4 5 3 5 4 5)
DATE=`date +%-d`
LEVEL=${LEVELMAP[$DATE-1]}
echo Performing a level $LEVEL dump
/etc/init.d/apache2 stop
sync
lvcreate -s -n snap vg0/root -L 400m
/etc/init.d/apache2 start
dump -$LEVEL -quz9 -b 1024 -f /backup/dump.$LEVEL /dev/mapper/vg0-snap
lvs vg0/snap
lvremove -f vg0/snap
cd /backup
echo put dump.$LEVEL | smbclient //server/backup -Uuser password

```

It maps today's date to the dump level via the array, shuts down background servers to make sure no files are being written to, takes an lvm snapshot, restarts the servers, dumps the snapshot, then deletes the snapshot.  Finally it copies the dump to a windows sever on the network for extra safe keeping.

I chose a 5 level pattern since it only reuses the level 1 dump on the 1st and 17th of the month.  You do a level 0 dump manually when you set it up to get things started, or whenever the level 1 dump gets too big for your taste.  It grows over time since it always backs up all files that changed since the level 0 dump, so the older the level 0 dump, the more files you likely have changed since then.

This script runs from cron each night at 1 am and results in a set of 6 files in /backup named dump.x where x is 0-5.  You could just as easily dump to a tape drive instead of files, or to an external disk drive you can take off site.  Once the dump is complete, you don't have to keep the file on hand for the next night's backup.  Once the dump is done, cron of course, emails me the results so I know if all went well or if there was a problem.

I use the LVM snapshots so that the servers can be brought back online immediately instead of having to wait for the backup to complete.  You could do without that if you want, but you would need to keep servers shut down and the fs remounted read only for the duration of the backup.

---

### Post by kuda on 2010-08-26
Hi

check amanda, openfiler and bacula<<as sugested earlier ...k.

---

