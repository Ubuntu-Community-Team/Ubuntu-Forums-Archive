---
title: "System restore in Ubuntu"
date: 2006-06-24
forum: The Cafe
---

### Post by forrestcupp on 2006-06-24
One thing I liked about Windows was its ability to automatically backup your system so you could do a system restore.  I don't know how many times I trashed my computer and I was able to choose from a calendar what day I would like to restore my system back to.  Then after doing a restore, which only took a couple of minutes, my system was back to normal.  This is just something that is built into Windows that runs in the background without the user even knowing it's happening.

After borking my Ubuntu system using ```
apt-build world
``` I kind of wished that Ubuntu had this feature.  Doesn't anyone else think this is a good idea?

---

### Post by evilghost on 2006-06-24
Just use tar with bzip2 or gzip to take backups at regular intervals.  I've written a bash script to do this for me and store the archives on an external firewire drive.

---

### Post by fuscia on 2006-06-24
i have no idea, but my guess is that, in linux, it's like trying to hit 'rewind' in a car accident.

---

### Post by slimdog360 on 2006-06-24
theres a reason why windows has that built in. Would anyone like to guess why

---

### Post by MiKuS on 2006-06-24
bashing windows is lame.

anyway - i also just use gzip and archive everything, then if something goes wrong and worst comes to worst, i'll just boot off the dapper cd, install it, boot into ubuntu, mount my back up partition, and un archive it.

it's easier then it sounds.

---

### Post by jason.b.c on 2006-06-24
[QUOTE=slimdog360]theres a reason why windows has that built in. Would anyone like to guess why[/QUOTE]


[Gee Wiz, I wonder .?]("http://www.quepublishing.com/articles/article.asp?p=101189&rl=1")

---

### Post by sharkboy on 2006-06-25
[QUOTE=forrestcupp]One thing I liked about Windows was its ability to automatically backup your system so you could do a system restore.  I don't know how many times I trashed my computer and I was able to choose from a calendar what day I would like to restore my system back to.  Then after doing a restore, which only took a couple of minutes, my system was back to normal.  This is just something that is built into Windows that runs in the background without the user even knowing it's happening.

After borking my Ubuntu system using ```
apt-build world
``` I kind of wished that Ubuntu had this feature.  Doesn't anyone else think this is a good idea?[/QUOTE]

I take it this is not about backing up your /home, which you should always do once in a while anyway.

When I mess around a lot with a system, I find it nifty to once in a while make a complete duplicate of it. I do this by copying everything in / except /dev to another partition. I use a simple 'cp -a' to do this. Then I mkdir /dev on the new partition, edit its /etc/fstab and finally add a grub entry for the duplicate installation and rewrite on mbr. I log into my backup system and check so that all is fine, and then I can go happily on to breaking things as I like on my regular installation -- I can always duplicate the duplicate back over the original.

Once you've established an fstab that works and have a working grub, all this can be extremely easily croned, should you want to (and you say above that you do).

man cp
man cron

---

### Post by forrestcupp on 2006-06-25
[QUOTE=slimdog360]theres a reason why windows has that built in. Would anyone like to guess why[/QUOTE]

That's true, but I've screwed up Linux even more than I ever did Windows because of the learning curve and complexity.

All of the suggestions are good, but none comes close to System Restore on Windows.  I don't know how it works, but it just makes images of your system, and you can restore it to any of the large number of images organized by date.  Then the restore process takes only a little bit longer than the time it takes to reboot.  And that includes a having to reboot afterward.

I don't like having to keep reinstalling Dapper, because for some reason my live cd takes about a half hour to boot up to the point that I can install it.  Installation is fast, but getting there is a drag.

This is definitely not something that makes it worth going back to Windows over; I love Ubuntu Linux.  I just think if they could figure out how to implement something like this, it would be an awesome thing.  After all, Linux is an environment where people screw around with their system a lot.

---

### Post by G Morgan on 2006-06-25
[QUOTE=MiKuS]bashing windows is lame.

anyway - i also just use gzip and archive everything, then if something goes wrong and worst comes to worst, i'll just boot off the dapper cd, install it, boot into ubuntu, mount my back up partition, and un archive it.

it's easier then it sounds.[/QUOTE]

While true the point was valid. Windows has a system restore option because its an option Windows more regularly needs. Linux doesn't need it to the same extent since it is posible to have a machine and do 99% of tasks without destroying your machine in Linux and its always posible to fix Linux without restore, exploits are always a threat in Windows and can take your entire OS down. You can take every step and still get your machine wrecked in XP so system restore is a very useful feature.

Linux has other issues so the devs have rightly targeted these issues. System restore is one of those things that will come in time but isn't an issue until more serious problems (like hardware compatibility and the LSB) are dealt with.

Its all a case of the right tool where it is needed.

---

### Post by flyingbrass on 2006-06-25
You could set up rdiff-backup.  Unlike rsync, it allows you to roll back to a certain time.  I haven't tried it yet.

---

### Post by H.E. Pennypacker on 2006-07-30
> **evilghost said:**
> Just use tar with bzip2 or gzip to take backups at regular intervals.  I've written a bash script to do this for me and store the archives on an external firewire drive.

Whether you're using a script or not, what you're describing is all manual.  Do you know of a way to create a system restore point with a click or two?  I assume you don't.  Most Linux users would recommend starting the terminal, typing in something for making a backup, and storing that backup somewhere.  How is this anything advanced or simple?  It's the same old create-a-backup-and-save-it-somewhere.  

System Restore changes this by doing all the dirty work with a few clicks, and when you do something wrong, all you have to do is select a date when Windows was working.

If I ever become an advanced programmer, this will be on my mind.

---

### Post by djsroknrol on 2006-07-30
That's the edge that MS has...it's just easier for people to use...got a screw up?...system restore will fix it...we need some sort of "partimage" sort of system restore built in...

---

### Post by TravisNewman on 2006-07-30
just for what it's worth, I've had nothing but trouble out of Windows System Restore. It never seems to work, at least 90% of the time, and when it does work occasionaly it hasn't restored what I need it to for some reason (even though I know when the change occurred). 

Automatic system backup and restore would be nice. If someone could set up a system that would get the date, get all of /home and /etc, get the currently installed software from apt, store it all in a day-of-the-week.tar.gz file, and also an install-program-name.tar.gz... set up a cron for it that deletes the old ones after a week and create the new one, then have a restore script that will let you choose what to restore (settings, installed programs, personal files), then purge any software not in the backed up apt database, and install any in the database that's not currently installed, throw over the contents of /etc, and /home, and that's PRETTY MUCH System Restore. Perhaps throw in an optional weekly full system backup as well?

All the tools are in place to do it, it's just a matter of packaging it. How hard would it be to do that, anyway? I know having the backups of /etc and /home would be easy, and I know it's easy to --get-selections and restore those after a reinstall, but how hard would that be to compare current software, purge what's not in it, all of that?

---

### Post by evilghost on 2006-07-31
I've seen System Restore destroy more machines than fix.  Heck, if you really want a "system restore" just add an event to /etc/apt/apt.conf.d which would kick off a backup (full/diff).

I certainly don't want a "System Restore" in any fashion similar to what Redmond has produced.

I can appreciate your desire for a "System Restore" but is this just a crutch in place of a normal backup routine or research prior to system-wide changes? ;-)

---

### Post by Compucore on 2006-07-31
I do have a 12/24 tape back up system over here in SCSI-1/2 over here. I just need to get it installed and update an essentials that I need it to run in it. Should work without a problem. Its a seagate 12/24 external tape back up. 

Compucore

---

### Post by adamkane on 2006-07-31
Use sbackup. There's a slight learning curve, but wonderful wonderful.

BTW - Windows backup sucks. It leads to more data loss than it prevents.

---

### Post by forrestcupp on 2006-08-02
Well, when I was a windows user, I used System Restore several times.  I've used it on several computers, and I have never had any trouble.  System Restore bailed me out a lot of times.  I wonder if some people that have bad things to say about it have actually used it.  But let me just say that System Restore on Windows Me was horrible.  The XP version turned out a lot better.  Like I said, I don't know how Windows System Restore works, but it has a lot of benefits over the backup techniques that have been mentioned.  

1. It doesn't take any time. It automatically sets restore images for certain dates without the user even knowing about it.  

2. It doesn't take up any noticable disk space.  You might have 20 different restore points with no disk space missing.  A full backup would use quite a bit of disk space.  

3. In each restore point it makes an image of what your os looked like at that time, including the registry, menu items, settings, everything.

When I first started using Linux, I screwed it up enough times that a System Restore would have been nice.  Even recently, I did an automatic update which included the new Linux kernel.  For some reason it trashed my xorg.  A system restore would have been really nice then, too.  It's a good thing I know more about what I'm doing or I would have ended up reinstalling Ubuntu from scratch, and with as long as it takes to boot up LiveCD, I wouldn't have liked that.

I know making backups is a good idea, but is there really anything wrong with making things easier in Linux.  Some of the same people that wonder why Linux isn't mainstream think that it's against the Linux code to make something easy for people.

---

### Post by aysiu on 2006-08-02
I think a system restore function would be a great idea. It is a frill, though, not a basic requirement. Most Windows users I know don't even realize the function exists. It's mainly Windows power users who do.

I'm not sure how one would get the ball rolling on this happening... maybe put it on the Edgy+1 wishlist for Ubuntu? Maybe actually hire some developers to create a SourceForge project for it?

In the meantime, I [use PartImage](http://www.psychocats.net/ubuntu/partimage.html) to back up my entire Ubuntu partition as is, which I can then restore to how it exactly was.

---

### Post by ClarkePeters on 2006-10-08
Windows bashing is childish. :frown: Bill didn't make all his money off nothing. :roll: 
My system is 100% Ubuntu now, =D> 
but that doesn't mean Windows never did anything right. Get off your emotional high-horses and let's look at the best of all things and see how we can improve, integrate, and improvise.

I used System Restore, not 1, not 2, not a few, but hundreds of times--and I mean hundreds. I frankly can't remember when I started using it (Windows 98?) because I've used it so much over the years. Never had a bit of trouble with WindowsME System Restore.  Key point, when you know your going to make changes, do a manual System Restore before making changes so you only lose the data on the tested changes. People who don't do that often do lose something more than they intended in a System Restore, or they simply choose the wrong restore date.

All that being said, I'm a Linux guy (UBuntu all the way!! =D> ), but sometimes I do fear pushing my system to the limit because I get tired of doing reinstalls (I have a real job and a real family and many real responsibilities outside of just wasting my time screwing up my system and then trying to fix it). I need my computer to serve me, not the other way around.:o 

The key with system restore is that I HAD NO FEAR and, therefore, I pushed my system to the limit. In the Ubuntu community, with something like System Restore, everyone can push the limits of their system, experiments, program installs  and such with comfort and ease, and with no fear, and therefore, the community will benefit. 

It's a great idea.  =D> =D>

---

### Post by Polygon on 2006-10-08
system restore is one of the cool functions of windows that i actually like. Even apple is coming out with their own version called "Time Machine" to debut in their new version coming out soon.

---

### Post by tagra123 on 2006-10-08
> **aysiu said:**
> I think a system restore function would be a great idea. It is a frill, though, not a basic requirement. Most Windows users I know don't even realize the function exists. It's mainly Windows power users who do.

I'm not sure how one would get the ball rolling on this happening... maybe put it on the Edgy+1 wishlist for Ubuntu? Maybe actually hire some developers to create a SourceForge project for it?

In the meantime, I [use PartImage](http://www.psychocats.net/ubuntu/partimage.html) to back up my entire Ubuntu partition as is, which I can then restore to how it exactly was.

I'd be willing to help code with this sort of project.  I keep good backups myself using partimage for the system and a weekly, daily, hourly script for important documents.  One of my pet peeves are the people who say that they do not have money for storage space for backing up, yet have time to reinstall ???

Normally before editing anything important, I make a copy of the file. 


From my days in windows -- System restore doesn'tm "fix everything" like internet settings and it cannot undo everything. 

 I think it keeps a copy of the system registry and key system dlls.

---

### Post by tagra123 on 2006-10-08
> **evilghost said:**
> I've seen System Restore destroy more machines than fix.  Heck, if you really want a "system restore" just add an event to /etc/apt/apt.conf.d which would kick off a backup (full/diff).

I certainly don't want a "System Restore" in any fashion similar to what Redmond has produced.

I can appreciate your desire for a "System Restore" but is this just a crutch in place of a normal backup routine or research prior to system-wide changes? ;-)


In my experience nothing beats partimage. I keep my home directory in a different partition too. A real backup routine is key to saving time. I also use scripts to get automated backups of important data.

A "preverve current system settings" would be a great feature though for when we get in a hurry and 'forget" to read 2 minutes of instructions that could have saved hours of grief..

Here's my hourly, daily, weekly how-to. There are many other backup how-tos in these forums.  [http://www.ubuntuforums.org/showthread.php?p=1402091](http://www.ubuntuforums.org/showthread.php?p=1402091)

---

### Post by ice60 on 2006-10-08
system restore is good, but it does use alot of resources and only backs up core system files. it's not an imaging program, that's why you still have all the recent files you've made since the restore point was made. 

you can backup all your viruses too lol, so if you've used it to remove a virus, you should disable it then re-enable it after a reboot i think. that will flush out the virii (viruses :mrgreen: )

there's this program for ubuntu (as well as sbackup) i haven't used either though.
[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)

---

### Post by darkhatter on 2006-10-08
system restore on windows scares me, it works GOOD. I have no idea how it works, but it works.

---

### Post by nixios on 2006-10-15
I have used windows restore a hundreds times and i don't have 
problem with it.That is why i'm still bit confused if i 
have to upgrade the community library the i'm helping for 
to upgrade their 34 workstation running on xp pro.

btw,quick question.What folder/directories should i install
programs like adobe,flash or other 3rd party softwares? i wanted
it on system wide so that limited users can also use it.

Thanks,
nix

---

### Post by argie on 2006-10-15
> **ice60 said:**
> 
there's this program for ubuntu (as well as sbackup) i haven't used either though.
[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)
That looks good. You'll need to recreate the install-sh symbolic link if you only have automake-1.4 though. I'll try it tomorrow and see. (My mistake: This is only a GUI, so far, does not do the job yet)

Wouldn't using partimage to a dedicated backup partition, give you more than Windows System Restore, though?

---

### Post by wrycatcher on 2006-12-15
> **ClarkePeters said:**
> 
All that being said, I'm a Linux guy (UBuntu all the way!! =D> ), but sometimes I do fear pushing my system to the limit because I get tired of doing reinstalls (I have a real job and a real family and many real responsibilities outside of just wasting my time screwing up my system and then trying to fix it). I need my computer to serve me, not the other way around.:o 

The key with system restore is that I HAD NO FEAR and, therefore, I pushed my system to the limit. In the Ubuntu community, with something like System Restore, everyone can push the limits of their system, experiments, program installs  and such with comfort and ease, and with no fear, and therefore, the community will benefit. 

It's a great idea.  =D> =D>

I haven't had time to read the entire thread, but this post by ClarkePeters is right on target.  I'm a recent Ubutnu convert, though I'm not totally new to Linux.  I'm customizing my OS environment like crazy, getting all things working just the way I want (codecs, applications, GUI settings, permissions).  I've invested a ton of time into getting my Ubuntu environment just the way I want it, and I'm far from done.  

Some of you out there have used Linux for years, so I'd like to know how many of you have started completely over with a fresh distro installation?  About often would you estimate you have done that?  Have you ever taken the time to develop (and maintain) some sort of "rebuild" script perhaps which gets all the packages you need, sets various OS options, etc.  Something that you knew would save time for future OS reinstallations?  For Windows, I used to have a checklist of tasks that I would *manually* need to do as part of a complete reinstallation.  Applications, custom registry updates, setting local variables, etc.  Even with a nice list like that, it still took a full day to reinstall and get all my stuff set up right.

I'm kind of dreaming (ideally) about an OS that I don't have to fear getting borked to the point that recovery is not a viable option (time, complexity, unknowns, etc).  What are the odds I'll be faced with that situation with Ubuntu?

---

### Post by SnTholiday on 2006-12-19
For those who have had success with Windows System Restore, that's great. I tried it a couple of times and it deleted most of the files I was trying to save once the restore was complete. I shut it off.

Now that Ubuntu is my only OS, I just backup my gnucash files, and all my music, pictures, etc. are on CDs.

---

### Post by rickyjones on 2006-12-19
> **nixios said:**
> btw,quick question.What folder/directories should i install
programs like adobe,flash or other 3rd party softwares? i wanted
it on system wide so that limited users can also use it.

Thanks,
nix

Nix,

Install everything to the default folders. If the program is "Made for Windows XP" then you will not have any issues. If, however, the program runs into issues (this is where testing comes in), then here are my suggestions:

* Use groups, especially if you are on a domain.
* Use the group memberships to give the necessary users write access to the program directories that they need.
* ^^ Same thing, but for the registry entries for the program.

It's simple to set up Windows securely, it just takes time and testing :).

-Richard

---

### Post by reacocard on 2006-12-19
I wouldn't think a basic system-restore-like program would be that hard to create for Ubuntu. You'd just have to:

-Keep a backup of /etc
-Keep a record of installation/removal of packages via apt

Obviously that won't cover all situations, but it would provide a good base to start from.

If anyone is interested in starting something this, I'd be willing to help.

---

### Post by sweemeng on 2006-12-19
i have this experience in edgy(dapper is very stable) where, something screwed up, and i can't restore it, not sure what is the problem, but most hardware don't work anymore, especially network card, cd-rom,usb. i resort to reinstall the system.  and reformat the disk again. 

here is a few things that i can see from here(from an intermediate user perspective, not familiar with apt-build world ):
[LIST]
[*]personal file is easy, it resides mostly, in home anyway.
[*]configuration file is like personal file, stays mostly at home
[*]system wide configuration file still not hard. 
[*]we will need to back up the .deb used for installation, from what i see not hard, but not really necessary
[/LIST]
maybe we can have a script to automate it.
it will not be something like system restore, but at least, when we reinstall the system, it will be easier. but can be crude, if only one components need to be reinstalled.](*,)  at least will be easier to a non technical user. 

also, it is quite common that a linux machine uses a back-up script to back up the disk into an external hard disk on an interval. so why don't ubuntu have a gui version that help people do that more easily.

maybe we can have an undelete feature, when someone accidentally delete(from trash bin) something we can restore it. can be done, :-k nah.............

---

### Post by spockrock on 2006-12-19
I keep /home and other important files on separate hdds and or partitions......same thing goes for winblows when I use it, nothing solves a problem like a quick reformat and install.

---

### Post by wrycatcher on 2006-12-20
OK, but that doesn't answer my question.  I want to know about being able to avoid having to do a total reinstallation of the OS/applications/settings, etc.  Data, on the other hand, is easy to backup and restore.

---

### Post by JAPrufrock on 2006-12-20
For me XP Restore worked about 15-20% of the time- not enough to be useful.

Generally speaking, Windows OSs have been inferior products (except maybe 3.1).  Consider this: the largest monopoly in the world and the richest company in the world can't produce a product that's any better than one made by a bunch of geeks in their spare time (over and over and over again if you consider the different distros). 

Why not bash windows? I like the sound.

---

### Post by RAV TUX on 2006-12-20
> **forrestcupp said:**
> 
[COLOR=Red] After borking my Ubuntu [/COLOR]system using ```
apt-build world
``` I kind of wished that Ubuntu had this feature.  Doesn't anyone else think this is a good idea?

Don't Bork your Ubuntu.;)

Sabayon actually has a feature like this...after breaking my KDE desktop I repaired the OS using the Live DVD...took a while but worked like a dream.

---

### Post by tagra123 on 2006-12-20
If you have some extra drive space or a network server dd can do a very good job from the live cd. Also part image is what I use the most -- apt-get partimage. It will also work from the live cd but I usually use sysrescue cd for this.

I always do this before upgrading just in case.

---

### Post by tagra123 on 2006-12-20
> **sweemeng said:**
> i have this experience in edgy(dapper is very stable) where, something screwed up, and i can't restore it, not sure what is the problem, but most hardware don't work anymore, especially network card, cd-rom,usb. i resort to reinstall the system.  and reformat the disk again. 

here is a few things that i can see from here(from an intermediate user perspective, not familiar with apt-build world ):
[LIST]
[*]personal file is easy, it resides mostly, in home anyway.
[*]configuration file is like personal file, stays mostly at home
[*]system wide configuration file still not hard. 
[*]we will need to back up the .deb used for installation, from what i see not hard, but not really necessary
[/LIST]
maybe we can have a script to automate it.
it will not be something like system restore, but at least, when we reinstall the system, it will be easier. but can be crude, if only one components need to be reinstalled.](*,)  at least will be easier to a non technical user. 

also, it is quite common that a linux machine uses a back-up script to back up the disk into an external hard disk on an interval. so why don't ubuntu have a gui version that help people do that more easily.

maybe we can have an undelete feature, when someone accidentally delete(from trash bin) something we can restore it. can be done, :-k nah.............


google for aptoncd -- it will make a cd that contains everything you've used apt to install.

---

### Post by wrycatcher on 2006-12-21
Whoa, I only understood about 1/2 of that.  Can you explain your backup process in more detail?

---

### Post by OffHand on 2006-12-21
I think some sort of snapshot tool would be an excellent idea. Think VMware server snapshot; it works great. Might be better ways to implement it though. This idea gets my vote :KS

---

### Post by tagra123 on 2006-12-21
> **wrycatcher said:**
> Whoa, I only understood about 1/2 of that.  Can you explain your backup process in more detail?

I normally use sysrescure cd for this but the following works on the live cd too.

I dont use partimage command line arguments when using ubuntu -- instead I select everything from the graphical program -- partimage (no command line options)

Partimage is smart in that it only backs up where data is stored -- dd wil make an exact image.

The dd command are used as is in the live cd terminal.

*******************************************
I have sysrescue cd on a small harddrive partition that I use for temporary purposes, It can be selected from the grub menu. On that drive I have sysrescuecd on the harddrive, and on another small partition I have a script so that I can mount the partition containing the script, run the script  and when its finished it will reboot the computer back into ubuntu. 

Below is a description of how backup and restore (CLONE) this manually.
*******************************************


This works on Dapper 6.06 and sysrescuecd.

Start the ubuntu live cd.

When everything is up and running go to Applications - Accessories - Terminal.

You may or may not have to type sudo ( I usually use sysrescue CD which already has part image on it.)

For Ubuntu:

```
sudo apt-get install partimage
```


Now lets says you have a second hard drive for backups with just one partition 

Ubuntu might see this partition as hdc1 hda1 hdd1 or sda1 etc... or something similar.  To find out what partitions are on the drive you can run gparted without making any changes to just look at your hard drive.

Menu: System-Administration-Gparted

or Terminal

```
gparted
```

write down the partiion(s) you want to back up (I always keep a printed copy of /etc/fstab from a working installation to keep track of the important drives)

Now that you know what you are backing up and where you are backing up its time to backup the MBR and PARTITION TABLE.

ASSUMPTIONS:  
#1 Windows (See notes below) is on hdc1, Ubuntu is on hdc2, Home is on hdc3, Swap is on hdc4
#2 Your backup partition is on hdd1

Make sure the devices you are backing up from are unmounted.
```

sudo umount /dev/hdc1
sudo umount /dev/hdc2
sudo umount /dev/hdc3

```

You must create a mount point and mount the partition you are backing up TO.
```

sudo mkdir /mnt/backup
```

In ubuntu you might have to (SysRescueCd does not require sudo)  

```
sudo chmod 777 /mnt/backup
```


Mount the BACKUP drive
```
sudo mount /dev/hdd1 /mnt/backup
```




**_Backup the MBR   (VERY IMPORTANT)_**

**Most of the time you wouldnt need these unless you really messed up.**

```
sudo dd if=/dev/hdc of=/mnt/backup/root-hdc-MBR-12212006 count=1 bs=446

```

**_Backup the MBR & Partition Table  (ALSO  IMPORTANT)_**


```
sudo dd if=/dev/hdc of=/mnt/backup/root-hdc-MBR-WITH-PARTTABLE-12212006 count=1 bs=512

```


#BACKUP UBUNTU ROOT
```
partimage -o -d -b -z1 save /dev/hdc2 /mnt/backup/root-hdc2-12212006
```

or 

```
sudo partimage
``` 

and use the graphical interface. On the Ubuntu live cd -- You will receive an error as partimage initializes for each partition but the backups work and restore fine.

#BACKUP UBUNTU HOME
#The f2 option tells partimage to reboot the computer when finished
```
sudo partimage -o -d -b -z1 -f2 save /dev/hdc3 /mnt/netbackup/home-hdc3-12202006

```

or 

```
sudo partimage
``` 

and use the graphical interface. You will receive an error as partimage initializes for each partition but the backups work and restore fine.



Restoring partimage backups (HOME and ROOT partitions)

Set up the mount points as described above.

```
sudo partimage
```

Select the backup file and location to restore to.

*********************************************************************************
**In the event that the MBR or PARTITION table needs restored (you'll know -- deleted all partitions etc...)**

**_USE THE COMMANDS BELOW WITH CAUTION_** 
[B][COLOR="Red"]Restoring the partition table to the wrong drive could cause you to lose data[/COLOR]
[/B]
- Google for dd for more information 


RESTORE MBR and PARTTION TABLE
```
dd if=/mnt/backup/root-hdc-MBR-WITH-PARTTABLE-12212006 of=/dev/hdc count=1 bs=512

```

RESTORE MBR only** (Recommended -- Only if needed)**

[B][COLOR="Red"]Most of the time simply retoring the "root" partition will fix things. If not then restore the home partition - I have automated hourly, daily, and weekly backups using rsync and tar -- see the how to.)
[/COLOR][/B]
```
sudo dd if=/dev/hdc of=/mnt/backup/root-hdc-MBR-12212006 count=1 bs=446
```

**NOTE:**
NTFS  (Windows) isnt fully supported by partimage, however if it backs up it will restore. I have never encounted a problem using partimage with NTFS. FAT systems work fine with partimage.

The dd command can be used to make a clone of the partition or entire harddrive.


I always keep a printed copy of /boot/grub/menu/lst and /etc/fstab  -- These are valuable when you need them.

For hourly, daily and weekly backups

I wrote this simple How To:

[http://www.ubuntuforums.org/showthread.php?t=240326](http://www.ubuntuforums.org/showthread.php?t=240326)

---

### Post by towsonu2003 on 2006-12-21
was this posted: [https://blueprints.launchpad.net/distros/ubuntu/+spec/system-restore](https://blueprints.launchpad.net/distros/ubuntu/+spec/system-restore)


if not, can you please add it to your first post for increased visibility -thanks

---

### Post by tagra123 on 2006-12-21
> **towsonu2003 said:**
> was this posted: [https://blueprints.launchpad.net/distros/ubuntu/+spec/system-restore](https://blueprints.launchpad.net/distros/ubuntu/+spec/system-restore)


if not, can you please add it to your first post for increase visibility -thanks



???????????????????

---

### Post by towsonu2003 on 2006-12-22
> **tagra123 said:**
> ???????????????????

that's a feature request submitted to launchpad, and it asks the exact same thing this thread wants (system restore). this link might clarify the process:
[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)

---

### Post by wrycatcher on 2006-12-22
All I can say is thanks for taking the time to spell it all out!!  I will experiment with all this soon.

---

