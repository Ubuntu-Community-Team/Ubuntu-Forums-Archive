---
title: "Complete Server Backup"
date: 2015-01-08
forum: Server Platforms
---

### Post by Harpz on 2015-01-08
Hi

I've had my Ubuntu 14.04 + SnapRAID Server up and running now for a good few months now and have been thinking its about time i should back up the OS drive.

The reasoning behind this is that i have got it set up how i like now, I've managed to cobble together a number of scripts that email me the various info's that allow me to keep an eye on things when I'm not there and it would be a pain if i lost them. MySQL is running for my XBMC setup and Deluge, Monitorix, Webmin and various other little tools.

The Server OS is installed on a 64GB SSD and wouldn't take to much space to backup but I'm trying to figure out what the best option for me would be as I'm new to this area (servers / linux backups).

I was looking at the following articles using tar: here [ http://ubuntuforums.org/showthread.php?t=35087]( http://ubuntuforums.org/showthread.php?t=35087) and here [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) but I also came across articles using rsync and clonezillia. 

I have used clonezilla before to backup windows laptops and its worked fine, it just seems a little overkill for an 64GB SSD. Is it just as simple on linux partitions, clone, restore, working, what about grub?

I'm fairly comfortable in the command line now and slowly learning my away around the system, I'm leaning toward the TAR fourm post as seems the simplest to implement, Is it complete and accurate as my knowledge is still lacking in some areas. 

Thanks in advance.

---

### Post by TheFu on 2015-01-08
Tar is really old school and has a place, just not for system backups.

Whatever you choose, be certain that you 
a) have a way to get a consistent backup of any MySQL DBs.  You can either shutdown mysql or dump the data to a "dump text file" - that is critical. A corrupt DB isn't any use during a restore.
b) practice the restore to ensure you get everything you need. Practice it a few times, maybe 3 to iron out the restore issues.
c) decide if you want a partition backup (binary) or a file-based backup, which provides much more flexibility, but a little more complexity at restore time.
d) When someone says it is easy, that doesn't mean it is the best solution for you.

There are lots of other people asking similar questions - definitely read those carefully.

Please don't use tar. It is not a good idea for system backups.  It is good for backing up small directory structures and taking the tgz file with you on a flash drive, however.

With all that said, I use **rdiff-backup** for about 30 systems here and like it. The best how-to for it [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) - better than all the articles I've written on it, definitely. ;)   However, my articles talk about other parts of the backup process - like cleaning up temporary files, capturing system data, configs, crontabs, and installed packages BEFORE doing the backups, so you know what to restore without backing up 4G of OS and Applications unnecessarily.

---

### Post by mastablasta on 2015-01-09
meh just image the disk with clonezilla then do auto backups (withsome automated backup like the mentioned rdiff) of database only (if that is really needed...).

64GB ssd just for the OS. I wonder what else is on there... :) I use 8 GB reliable USB stick. and there is about 6 GB free. if I added XBMC + database I am sure it would still have more than half unoccupied space. in any case ju8st image it with clonezilla or redobackup and be done with it. the created image won't be 64GB but will be about 3 GB probably. unless you store other stuff on the SSD. remember that the empty disk space is compressed and takes up near 0 space.

---

### Post by Harpz on 2015-01-09
Thanks for the reply guys

Been having a think on what was said and when i really look at it, it wouldn't take that long to reinstall the OS, the part that would take the time would be setting everything back up and re-downloading all the updates.

TheFu you mentioned your articles talk about other parts of the backup process - like cleaning up temporary files, capturing system data, configs, crontabs, and installed packages.

When can i find these articles, as looking at it if i could back up my scripts, configs, crontabs and installed packages, not sure if i will keep mysql yet, this would speed the restore process up allot and be a great leaning experience for me.

Or i could do what mastablasta said and just use clonezilla, this would give a ready to run base to start with in the event the SSD died.

---

### Post by TheFu on 2015-01-09
Every storage media will die. Plan on it.  Plan on it happening when it is least convenient.  Even if you have an image of the partition, you need to put it back in the exact same place for an image-based backup to work. If you have to use a different HDD/SSD, then the UUID to the partitions will change - your image isn't perfect any more. You'll need to manually fix that. A few other things will be broken too, which require manually fixing.

Clonezilla, partimage, fsarchive are all in the same family of tools. I like fsarchive the most. All of these need to be run from alternate-boot media. I.e., you can't run them from inside the running OS. That is a complete failure for me. My systems need to be up and cannot be down for an hour as I image the system.  5 minutes at 2am - I can get away with that downtime. Plus, it is hard to automate backups with so much manual interaction.  Things change on our systems daily, which is why companies do daily backups at a minimum. Some do hourly snapshots or write the data changes to 2 places concurrently because the hassle of losing data isn't worth it.  At home, it is trivial to setup automatic, daily, backups with rdiff-backup - why wouldn't you do that?

Don't forget to practice the restore.

I say - why bother backing up 3-4G of OS and Application binaries at all?  For 1 system, meh, doesn't matter too much. I have 30 systems to backup ... that's 120G of unneeded stuff when a single ISO with Ubuntu has that data already.  [http://blog.jdpfu.com/tag/backup](http://blog.jdpfu.com/tag/backup) - there are links to relevant articles here all over the place.

Oh - and imagine your HDD/SDD failed right now. Seriously, imagine it. What would you do?  I can still remember when 1 disk failed in 2002 in my LVM setup.  I lost 80% of my stuff. Made me sick to my stomach as the realization finally came over. Since then, I've had **backup religion**. Please learn from my mistake. There are so many reasons that versioned backups are absolutely critical - not just hardware failure, but viruses, attacked systems, accidental file deletions, system cloning ... RAID failures, LVM failures, and the list goes on and on.

Happiness is:
```
=== Backing up  lubuntu === 
StartTime 1420786987.00 (Fri Jan  9 02:03:07 2015)
EndTime 1420787262.92 (Fri Jan  9 02:07:42 2015)
ElapsedTime 275.92 (4 minutes 35.92 seconds)
TotalDestinationSizeChange -114653796 (-109 MB)


=== Backing up  xen41 === 
StartTime 1420789816.00 (Fri Jan  9 02:50:16 2015)
EndTime 1420789863.02 (Fri Jan  9 02:51:03 2015)
ElapsedTime 47.02 (47.02 seconds)
TotalDestinationSizeChange 2994681 (2.86 MB)


=== Backing up  c720 === 
StartTime 1420791188.00 (Fri Jan  9 03:13:08 2015)
EndTime 1420791378.67 (Fri Jan  9 03:16:18 2015)
ElapsedTime 190.67 (3 minutes 10.67 seconds)
TotalDestinationSizeChange 25898544 (24.7 MB)
```

That's from last night. There are about 30 systems in this status email. I can see which didn't get backed up last night (had a power outage here due to extreme cold weather and I didn't bother turning on 1 of the machines after). Desktop or server - it needs to be backed up.

---

### Post by Harpz on 2015-01-20
Haven't had a lot of time to deal with this over the last week so am trying to refocus my efforts now.

I came across an article using Rsync as a Date Stamped, Snapshot Style, Incremental Backups system using hard links.

[http://webgnuru.com/linux/rsync_incremental.php](http://webgnuru.com/linux/rsync_incremental.php)

I like the idea that it only backs up what has changed, at first i didn't understand allot of what was said but i now think i have a better understanding of it.

```

#!/bin/bash
 
#Website Backup Script
 
#Todays date in ISO-8601 format:
DAY0=`date -I`
 
#Yesterdays date in ISO-8601 format:
DAY1=`date -I -d "1 day ago"`
 
#The source directory:
SRC="/var/www/htdocs/"
 
#The target directory:
TRG="/backup/website/$DAY0"
 
#The link destination directory:
LNK="/backup/website/$DAY1"
 
#The rsync options:
OPT="-avh --delete --link-dest=$LNK"
 
#Execute the backup
rsync $OPT $SRC $TRG

```

It took me some time to get my head around the hard links and still not sure i understand it 100% in the article you create your first full backup and then every backup after that it links to the original files and only creates a copy to the target of the files that are different / changed, that i get. 

Later on in the article it allows you to add the ability remove backups older then 28 days

```

#29 days ago in ISO-8601 format
DAY29=`date -I -d "29 days ago"`
 
#Delete the backup from 29 days ago, if it exists
if [ -d /backup/website/$DAY29 ]
then
rm /backup/website/$DAY29
fi

```

I can see how this code works but i cant get my head around if it deletes your original base files ( they could be older then 28 days ) and the rest of you sequential backups are only linked to them, what happens when you need to restore a file that's older then 28 days?

---

### Post by TheFu on 2015-01-20
Wikipedia has a good article about hardlinks.  Basically, there are file-information structures and there is file data.  A hard-link is just a copy of file-information stored under a different directory, but pointing to the same file-data.  The file-data retains a reference count (this is a common programming tool), and the data is not deleted until that reference count becomes zero (0).  

This means if there is any file corruption, every copy (i.e. hardlink) will have that same corruption.

It also means that backups cannot span across file systems (i.e. often partitions).

It also means that if there is any change to a file, even 1 bit, then the next backup has to create a new file-data area and the storage amount doubled for that file. Often this isn't a big deal.

It also means that target file systems must support hardlinks (NTFS does not).

It also means that file permissions, ownership, groups are maintained in the file-data. Changes over time are not retained, unless the file data changes to force a new copy.

Even with these flaws, there is much to like about this backup method.

BTW, there are well-tested and well-used scripts that do what yours attempts (I didn't check it) that have been around for decades. Generally, it is better to reuse someone else's script.  Think they are commonly called rsnapshop or rbackup. There is also a number of examples in O'Reilly books - like the UNIX Power Tools toolkit. Still, it is good to write your own to gain a better understanding.

Oh - and I would strongly, strongly, strongly, suggest that you backup more than just website data.  Get /etc - it is tiny and holds so much system settings (like the apache config).

If you have a DBMS running, it is critical to either stop it or dump the data to a file that doesn't get changed during backups. Restoring a corrupted DB isn't very useful.  [http://lifehacker.com/5885392/automatically-back-up-your-web-site-every-night](http://lifehacker.com/5885392/automatically-back-up-your-web-site-every-night) has an example using mysqldump.

rdiff-backup works differently (still uses librsync however) and doesn't suffer from most of those negative aspects listed above. Just sayin'. For systems here, I keep 60, 90, 120 days of backups - depends really on the total size needed. Our backups contain all the information to rebuild the server to that same point.  Some are 27M for 120 days of versioned backups, so the backups can be tiny. It all depends on the amount of data, databases, that are involved.

Regardless, be certain the backup isn't written to the same physical HDD - it is best if the backup is pushed at least 500 miles away, to avoid common natural disasters (Earthquake, Hurricane, floods, ... ).  If you live in a place without those - perhaps just tornadoes, 20 miles may be far enough.

---

### Post by Harpz on 2015-01-20
Thanks for the info TheFu.

The scripts were a learning tool for me learned a lot about bash in the short time I've been playing with them.

Think I'm just over thinking it, now looking at rdiff-backup like you suggested to see if i can get my head around it :) 

Will just back up /etc or just the conf i change and /home 

Was thinking about cp /etc/apt/sources.list ~/sources.list.backup and apt-key exportall > ~/repositories.key also.

Can you recommend any other system folders that when backed up make a restore quicker?

---

### Post by MAFoElffen on 2015-01-20
I have a curiosity on your Snapservers...I have 2 of the old ones that someone gave me. Upgraded their disks to bigger...

Mind if I PM you or open another thread on my curiosities? (So I don't muddy this thread up.)

---

### Post by TheFu on 2015-01-20
> **Harpz said:**
> Can you recommend any other system folders that when backed up make a restore quicker?

[http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines) is how I've been doing backups for about 3 yrs. Restores take about 45 minutes and have been tested a few times on different machines. The restore process is not brain dead. The person doing the restore needs to understand what they did for the backups and how to restore.

[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best primer for rdiff-backup that I've seen. Much better than my 5 articles on the subject. ;(  dpkg --get-selections and dpkg --set-selections are key.

The best advice I have for learning this stuff is to do testing using /etc.  /etc is small, so tests don't take hours.  Some files there are protected, so you'll see the errors if you attempt a non-priviledge backup.  The files are text, so you can easily see how the incremental changes are stored and restored later.

---

### Post by Harpz on 2015-01-20
> **MAFoElffen said:**
> I have a curiosity on your Snapservers...I have 2 of the old ones that someone gave me. Upgraded their disks to bigger...

Mind if I PM you or open another thread on my curiosities? (So I don't muddy this thread up.)

Sure PM me if you want not sure what i can help with as very new to ubuntu server and SnapRAID myself but learning loads.

---

### Post by Harpz on 2015-01-20
> **TheFu said:**
> [http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines) is how I've been doing backups for about 3 yrs. Restores take about 45 minutes and have been tested a few times on different machines. The restore process is not brain dead. The person doing the restore needs to understand what they did for the backups and how to restore.

[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best primer for rdiff-backup that I've seen. Much better than my 5 articles on the subject. ;(  dpkg --get-selections and dpkg --set-selections are key.

The best advice I have for learning this stuff is to do testing using /etc.  /etc is small, so tests don't take hours.  Some files there are protected, so you'll see the errors if you attempt a non-priviledge backup.  The files are text, so you can easily see how the incremental changes are stored and restored later.


Lots of reading :) many thanks once again I'm sure Ill have more questions.

---

### Post by john.errington on 2015-01-29
Harpz, mind if I join in? I have ubuntu 14.04 running a LAMP server on an old COMPAQ PRESARIO PC  (around 2005). 
The internal HD is dying, so I want to replace it.  I bought an SSD (128G) - but the machine doesnt see it. 

Is there any way I can save a disk image as a .iso file and then move it later to the SSD on another PC?
I've read the above comments - I really dont want to start from scratch as getting the LAMP server running and talking on my windows XP/Vista/7/10 network was a b*tch.

---

### Post by mastablasta on 2015-01-30
sure. I just had to move widnowsXP from failing HD to new one. same can be done in Linux (probably even better): [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

you can move data to some other external disk and then clone it again to SSD on new machine. 

also make sure to reduce swapinees or move it to HDD on the new PC. 128 GB is big SSD disk, but I guess you know why you got it...

---

### Post by TheFu on 2015-01-30
> **mastablasta said:**
> 128 GB is big SSD disk, but I guess you know why you got it...

Not really.  There are 500G SSDs now and I've seen hybrids much larger.
Heck, when I swapped the 16G SSD in a netbook, could have got 32/64/128G options - got the 128G version "just in case."  I'm only using about 54G and most of that is extreme waste. For the stuff I **need**, 32G would have been more than enough - it just reduces the music and video on the box. It isn't like we can't get small 500G external USB3 storage devices cheap.

The main concern about using bit-for-bit copies is that partition block sizes aren't always the same, which can impact performance. OTOH, if the partition is pre-created and all the files are sync'd over using something like rsync, that goes away. Not sure any performance hit matters on an SSD - those are soooooo fast already.

---

