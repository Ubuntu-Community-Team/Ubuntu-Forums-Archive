---
title: "How do YOU back up?"
date: 2010-01-09
forum: The Cafe
---

### Post by tuahaa on 2010-01-09
Since I almost lost my USB which had a major assignment saved on it which was due in a week and my backup was one month old, I decided to be more careful in backing up. So, how do YOU back up then?

Ever since the incident, I back up on my separate partition, on my USB and on my normal 'buntu drive

PS. I found my USB in my bag next morning

---

### Post by Psumi on 2010-01-09
I save all of my work to my 8 GB USB Drive. It has music on it too. It is fat32, so I have to be careful when I install ubuntu's mini.iso.

[http://ubuntuforums.org/showthread.php?t=1370770](http://ubuntuforums.org/showthread.php?t=1370770)

I usually NEVER save any work to a computer, so I can easily re-install the OS at any time. Also, I don't plan to use ext2/3/4 as they are much too slow in comparison to fat32.

---

### Post by Techsnap on 2010-01-09
DVD-R backups and a NAS drive.

---

### Post by jayze on 2010-01-09
I don't!...anything personal on ext hard drive....a few necessary drivers on memory sticks...the odd cd if I really want to hang onto anything....I prefer to leave the PC clean so easy to do quick reformatt . Also less for prying eyes when visitors pop in.:popcorn: Doesnt seem much point in clogging up the PC anymore. Everythings up on the airwaves that you need anyway. Which seems to suit the powers that be and I'm all for if you can't beat em join em!.....to be honest I use my nuke clean disc more often than I use a back up disc or anything!

---

### Post by Psumi on 2010-01-09
> **jayze said:**
> Everythings up on the airwaves that you need anyway. Which seems to suit the powers that be and I'm all for if you can't beat em join em!

So you support cloud computing? I know I don't, at all.

---

### Post by qazwsx on 2010-01-09
rsyncing to usb drive

---

### Post by jayze on 2010-01-09
> **Psumi said:**
> So you support cloud computing? I know I don't, at all....I most certainly DONT...but like I said...if you can't abuse them then use them!:popcorn:

---

### Post by cascade9 on 2010-01-09
I backup to a internal hdd, which is disconnected except for when I'm backing up.

External USB is too slow, I dont trust clouds (and besides that, it would take me over a year to get my backups back that way- 30GB a month quota, and over 400GB of stuff to backup LOL) and saving to another partition is just asking for trouble...hdds do die.

---

### Post by jrothwell97 on 2010-01-09
For my Ubuntu partition, I just image the disk using dd.

For the Windows disk, I use Windows's own backup utility.

Everything is backed up to a 500gB WD My Book, with NTFS and ext4 partitions for each OS.

---

### Post by jayze on 2010-01-09
> **cascade9 said:**
> I backup to a internal hdd, which is disconnected except for when I'm backing up.

External USB is too slow, I dont trust clouds (and besides that, it would take me over a year to get my backups back that way- 30GB a month quota, and over 400GB of stuff to backup LOL) and saving to another partition is just asking for trouble...hdds do die.

gud gawd.....what you storing....nasa's archives?!:o

---

### Post by speedwell68 on 2010-01-09
I just copy and paste my personal files to an external HDD on a weekly basis.

---

### Post by CharlesA on 2010-01-09
I store everything on my file server, which rsyncs to external drives.

---

### Post by llawwehttam on 2010-01-09
Small free NAS sitting in the corner of my room now. Not completely working now but hopefully will be soon.

---

### Post by jayze on 2010-01-09
I guess I'm still in the dark ages....there was an old saying> "if you dont want anyone to see it then don't put it on paper";)

---

### Post by jayze on 2010-01-09
> **llawwehttam said:**
> Small free NAS sitting in the corner of my room now. Not completely working now but hopefully will be soon....theres more truth in that than you could ever imagine....who sang "freedom is a word I rarely use without thinking"?:)

---

### Post by scouser73 on 2010-01-09
I back up data to two external hard drives, just incase one fails.

---

### Post by cascade9 on 2010-01-09
> **jayze said:**
> gud gawd.....what you storing....nasa's archives?!:o

LOL, hardly. 

My 400GB+ is made up of- a lot of flac files, lots of mp3s, some music vids, some ebooks, some TV, the odd movie. It adds up. 

I know somebody who has over 3TB of TV and movies.

---

### Post by jayze on 2010-01-09
gawd! you must all have square eyes! lol:o

---

### Post by CharlesA on 2010-01-09
Meh, I only have about 70GB of "user data" and 1.6TB of movies (rips of my dvd collection).

---

### Post by jayze on 2010-01-09
Methinks someone needs to invent a way to store DVDS as lightweights!:)

---

### Post by aaronp on 2010-01-09
incremental backups to external USB hard drive using rsync and hardlinks.
Allows me to have a 'snapshot' of each day/week but using the hardlinks means I don't have any redundant data stored.

---

### Post by CharlesA on 2010-01-09
> **aaronp said:**
> incremental backups to external USB hard drive using rsync and symlinks.
Allows me to have a 'snapshot' of each day/week but using the symlinks means I don't have any redundant data stored.

How did you set that up? I'm guessing you used rsync.

---

### Post by The Real Dave on 2010-01-09
My main computer has an 80GB drive just for backups, using rsync on my /home dir twice a day, and the space is also used for clonezilla images, taken every fortnight. It also rsyncs that whole drive to my server twice a day. I don't back up other user's data, because its mostly just videos, which are stored on a different server anyway :) My servers, the backup drive, and my /home partition all use ext3 for the stability, but / uses ext4 for speed :D

---

### Post by aaronp on 2010-01-09
> **CharlesA said:**
> How did you set that up? I'm guessing you used rsync.

Yes, basically a bash script that runs on a daily cron schedule.
It copies yesterday's backup folder newly named with today's date as a hardlink (i.e. using cp -al)
Then rsync updates the files in the new folder. Any that are changed get overwritten in this folder (but not previous day's folders) and become the 'new' version whereas the existing ones just maintain the same hardlink to the original version of the file.

In my backup folder I can then see a folder for each date and within each folder is the full list of files for that day, even though most of them are just hardlinks to the actual file that was saved many days earlier.

Here is my script. Should be pretty easy to modify some variables and the parameters of the rsync command to get it up and running.



```
#!/bin/bash

#********************************************************************************************
#script backs up home directory
#Created: 17 Jul 2009
#********************************************************************************************

#********SETTING VARIABLES HERE********

#sets new backup folder name based on date
folder=`/bin/date +%Y%m%d`

#set directory path variable where backups are stored
dirpath="/media/store/homebackup/"

#retrieve most recent directory name from file
oldname=`cat /media/store/homebackup/latest`

#set paths and filenames to be used in script
newfolder=$dirpath$folder
oldfolder=$dirpath$oldname
reportfile=$dirpath"reports/"$folder".backuplog"

#*******FINISHED SETTING VARIABLES***********

#*******EXECUTING COMMANDS HERE**************

#hard link copy of oldest backup to new folder with new name, based on date
cp -al $oldfolder $newfolder

#overwrite file with new folder name/date
echo $folder > $dirpath"latest"

#rsync to retrieve files and incrementally effect changes on latest backup folder created above
rsync -rtu --delete --archive --log-file $reportfile --exclude "*.mp3" --exclude "*.avi" --exclude "*.iso" /home/aaron $newfolder
rsync -rtu --delete --archive --log-file $reportfile --exclude "*.mp3" --exclude "*.avi" --exclude "*.iso" /etc $newfolder
rsync -rtu --delete --archive --log-file $reportfile --exclude "*.mp3" --exclude "*.avi" --exclude "*.iso" /var $newfolder
rsync -rtu --delete --archive --log-file $reportfile --exclude "*.mp3" --exclude "*.avi" --exclude "*.iso" /usr/local $newfolder

```

---

### Post by CharlesA on 2010-01-09
Interesting. Thanks!

Do you just copy the files from the most recent backup if you need to do a restore?

I'm got plenty of space on my backup drive and I'm wondering if implementing that sort of scheme would be beneficial.

---

### Post by ~sHyLoCk~ on 2010-01-09
USB backup using a custom rsync script, it can be found on my blog. Nothing special but that's how I do it.

---

### Post by insane_alien on 2010-01-09
i have a large fileserverin my cupboard that i back everything up to. its RAID-Z so i'm protected in the event of a disk failure(worst that will happen is that i have to replace the non-RAID OS drive but i have an image of that on the RAID.

---

### Post by aaronp on 2010-01-09
> **CharlesA said:**
> Interesting. Thanks!

Do you just copy the files from the most recent backup if you need to do a restore?

I'm got plenty of space on my backup drive and I'm wondering if implementing that sort of scheme would be beneficial.

Yep, exactly. Restore is just a simple copy from the latest folder or if I know I changed a file on a particular date (or if I did something that ruined everything on a particular date) I can just go to the folder for that date and find it there too.

Yeah I've got an 80gb drive with my backups on it atm and I put my wife's backups there too so it was filling up fast. Doing it this way, I can keep weeks/months of backups without too much space getting taken up (unless I'm changing massive files on a daily basis) but the thing I like most about the hardlink approach is having what 'appears' to be a full copy of the snapshot for each day without using the space that a full daily copy would take - as opposed to just a folder with files that changed on that day.

And hardlinks are excellent because the actual file never gets deleted until the last link to it is deleted. So I can just go through and delete a whole bunch of old backup folders and any files that are unchanged in the kept folders will retain links to the same file even though I'm deleting the original links to them.

---

### Post by CharlesA on 2010-01-09
Oh awesome. I think I'll try to impliment it later. Probably keep 2 weeks worth of backups.

I wonder if it's possible to delete the oldest folder automatically.

---

### Post by forrestcupp on 2010-01-09
I throw my car into reverse and press the accelerator while either looking over my shoulder or looking into the rear-view mirror.

Hey, somebody had to say it. :)

---

### Post by SuperSonic4 on 2010-01-09
Depends how important the data is obviously :p

For nothing important I don't bother backing up. For example a PDF of the tube can easily be got back from TfL's website

If it is moderately important I save it on a different drive and on the main drive.

If it very important (non-document) I save it on 3 different drives, a USB drive, an external hard drive, my laptop and, in the case of music, my mp3 player.
For documents it's the above and a hard copy stored off-line

---

### Post by CharlesA on 2010-01-09
> **forrestcupp said:**
> I throw my car into reverse and press the accelerator while either looking over my shoulder or looking into the rear-view mirror.

Hey, somebody had to say it. :)

Lol. :D

---

### Post by markp1989 on 2010-01-09
my torrent slave has 2 internal 1.5tb drives, i have a small cron script that mounts the 2nd drive, uses rsync to copy my data accross, then unmount and spin down the drive. 

i would like to store stuff on the cloud for backups, but i have about 1.3tb of stuff, and i can only upload at 70kbs, so it would take like a year to back up all my stuff, (and would probably cost more then it did to buy a 2nd drive lol)

---

### Post by lightecho on 2010-01-09
Saving everything on my nas drive, configured raid 1. Never store any data anymore on my own harddisk.

---

### Post by cariboo on 2010-01-09
I do a daily backup of my home directory to my file sever, using rsync, and the server gets backed-up to an external drive once a week also using r sync.

---

### Post by standingwave on 2010-01-09
> **tuahaa said:**
> So, how do YOU back up then?

A subject near and dear to my heart. Most recently, back in November, I had a drive fail in the most unusual manner: One day, during a boot, my BIOS was suddenly incapable of detecting *any* storage devices (three hards, one optical). I thought it was a system problem but troubleshooting soon narrowed it down to one particular drive. Whenever this drive was connected to the system, it prevented detection of *any *storage device. Go figure. Something to do with the SATA interface, I guess. Fortunately, I was backed up.

My current solution is periodic rysncs to one of two removable drives that get rotated through off site storage.

I prefer a sync operation for the following  reasons:

[LIST=1]
[*]The largest files on my system are media which don't benefit from further compression.
[*]Hard drives are dirt cheap.
[*]I like to 'see' my backup data. About twenty years ago, a company I was working for implemented some proprietary third party backup solution. Everyone thought they were backed up until one day my hard drive failed and we discovered that for some reason, restore was simply not possible. I lost several months work of work. Reminded me of the old Seinfeld bit: *"See, you know how to take the reservation, you just don't know how to *hold* the reservation and that's really the most important part of the reservation, the holding. Anybody can just take them." *So yeah, I like to 'see' my data. Every now and again I mount my backup drive just to look at it.
[*]Recovery is easy. A few months I inadvertently deleted an entire folder. Human error and don't think it can't happen to you. Rather than digging through the trash, it was simpler to simply mount the backup drive and copy the folder.
[/LIST]

---

### Post by jamillikan on 2010-01-09
Acronis True Image 11 to an external USB Drive.  I create a full backup image and verify it, then do incremental thereafter.

---

### Post by Duncan J Murray on 2010-01-09
I wouldn't mind a bit of advice about backing up.

Currently my system is to copy my home directory to an external hardrive on an irregular basis (i.e. when I remember and have time).

But, as my laptop's harddrive has been filling up, and I've been offloading more and more onto external drives I've been thinking of what I need...

I think what you call it is a fileserver.  I'm not sure how to do it, but there must be some way to configure a cheap desktop computer with a whole load of storage, that automatically backs up to another harddrive (on the computer).  And it would provide (almost*) all my files over wi-fi.

Is this easily doable?

I'm not sure about RAID or rsync - but would I use one or another of these?

Thanks,

All best,

Duncan.

*I'm sure that stuff I'm currently working on would be stored locally, so I guess this would need to be backed-up, until I move it completely over to the fileserver.

---

### Post by Eisenwinter on 2010-01-09
> **jayze said:**
> IWhich seems to suit the powers that be and I'm all for if you can't beat em join em!
So the people of all the occupied countries of Europe in WW2 should have joined the German military and assist with its battles against the USA and the Soivet Union?

---

### Post by standingwave on 2010-01-09
> **Duncan J Murray said:**
> I'm not sure about RAID or rsync - but would I use one or another of these?.

RAID is many things but in my opinion it's not really a backup solution as while mirroring can give you improved fault tolerance, you remain vulnerable to many other ways to lose data. I think rsynch would best serve your needs. Either write your own script that serves your particular needs or configure  one of the  shells for it, like Grsync.

---

### Post by phawnex on 2010-01-09
external hard drive via time machine on apple.

linux, separate external on stuff i can not afford to lose i back up on

---

### Post by Exodist on 2010-01-09
Another stupid pole! 
You ask how does someone backup their data but there is no list for Tape Archives (.tar) or even Optical Disc. /facepalm

---

### Post by aaronp on 2010-01-09
> **standingwave said:**
> Reminded me of the old Seinfeld bit: [I]"See, you know how to take the reservation, you just don't know how to *hold* the reservation and that's really the most important part of the reservation, the holding. Anybody can just take them." 

haha love it. *"Would you like insurance?" "Yeah you better give me insurance because I'm going to beat the hell out of this thing!"*

---

### Post by aaronp on 2010-01-09
> **CharlesA said:**
> Oh awesome. I think I'll try to impliment it later. Probably keep 2 weeks worth of backups.

I wonder if it's possible to delete the oldest folder automatically.

No doubt it is. If you retain the date numbering system of the original script (i.e. YYYYMMDD) it should be easy enough to just delete any folder named with a date less than or equal to a particular date/number.
It's the logic for figuring out the dates when they cross over a month boundary that has a bit of work in it.

---

### Post by hessiess on 2010-01-09
Version control everything, check out a working copy onto all my computers. I have a LOT of files, managing it manually is imposable, as it is I can sync my mashes with a simple svn up + svn commit.

---

### Post by marco123 on 2010-01-09
Drag files to 2 separate external hard drives.

---

### Post by zerubbabel on 2010-01-09
rsync to an external drive plus an 8g thumbdrive encrypted with truecrypt

---

### Post by CharlesA on 2010-01-09
> **aaronp said:**
> No doubt it is. If you retain the date numbering system of the original script (i.e. YYYYMMDD) it should be easy enough to just delete any folder named with a date less than or equal to a particular date/number.
It's the logic for figuring out the dates when they cross over a month boundary that has a bit of work in it.

I found this here:

[http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/)

Sounds pretty straight forward. :D

---

### Post by SuperSonic4 on 2010-01-09
As I misread the question before

I use *cp -u *

---

