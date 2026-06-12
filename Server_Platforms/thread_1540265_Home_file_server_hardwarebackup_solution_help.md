---
title: "Home file server: hardware/backup solution help"
date: 2010-07-27
forum: Server Platforms
---

### Post by ObiDamnKenobi on 2010-07-27
Hello good sirs.
I've started looking into finally getting a home server, and stopped by for some pointers and a sanity check:) Requirements are pretty simple; primarily for file sharing to a Win7 HTPC and backup of my Vista desktop. Started looking at windows home server but soon started leaning towards an Ubuntu solution. I have only dabbled with Ubuntu desktop, but would consider this an entertaining project:)

First off I'm wondering if anyone could comment on my hardware list. I'm thinking:
CPU: Intel core i3 530 
Mobo: Intel DH55TC mATX
4 gig RAM

I have a 160GB caviar blue hard drive around; would this work as OS drive? 

For storage I'll aim for at least 2x 2TB drives. Looking at the Samsung f3 eco something now. Probably also a 1TB caviar green from my desktop. 

Reading on WHS I understand that it does a form of JBOD with folder duplication to spread the data to several disks. I'm not very interested in RAID (honestly don't see the point for my use), but would like to have all the data duplicated to two disks regularly. Is there a way to arrange this? My thought now is just a scheduled routine where one disk is mirrored to another. Although this seems like it cause some hassle, especially if I add disks. E.g always monitoring space on individual disks. Guess what I would like is a disk pool, where files are also duplicated. Any way to do this?

I started looking at Bacula in the guide, is that a good start?

Getting the server to back up my PC seems simple enough, I'm just wondering what is the best way to arrange the disks on the server.
Thanks for any help!

---

### Post by arrrghhh on 2010-07-27
Well the *best* way is typically what works best for you.

With that said, it sounds like what would be best for you would be a software RAID array.  I'm not a fan of software RAID personally, but if this is all the server does (IE no other OSes on it) then I say go for it.  It's going to be your best option if you want true data redundency.  The WHS method (as I understand it) is very similar to JBOD, except if you lose one hdd you only lose the data on that hdd.  JBOD as I understand it has issues if one drive fails in the array.  The only real advantage of JBOD or the WHS method I see is that you can use different sized hard drives.  Assuming the drives are the same size, RAID would be your best bet.

However... if there's only certain things that you deem extra-important... you could have a particular directory that when something is copied into it, that file/folder is also mirrored over to the other hdd.  Bind mount or symlink would probably do it.  That way you could have some hardware redundency if you do suffer a drive loss, but you don't lose all the space in the other hard disk by mirroring everything.

---

### Post by drdos2006 on 2010-07-27
Also check these out. Very informative, may answer all your questions.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

### Post by ObiDamnKenobi on 2010-07-27
Thanks for the link to the guide drdos! Looks very helpful.

arrrghhh; yes part of the reason I like the JBOD solution over RAID is to use disk of different size, and from different manufactures later. Buying all of them now, and having to rebuild the array with similar disks if I upgrade later, seems very inconvenient for my use. 

The WHS solution (I think) basically just creates a pool, and makes sure all files is copied to at least 2 disks. If one fails all the data will still be available, and without rebuilding a RAID. It can still be accessed on the server normally. The simplicity of this is appealing to me. But even without this I'm still leaning towards giving Ubuntu a try:)

I would like all my data to be duplicated, but something like weekly should be enough. If I buy disks in pairs (1 data, 1 mirror) and just have a a couple I guess it shouldn't be too much trouble keeping track. 

However, I'll go read up on JBOD and see if that is something to consider. 

Thanks to you both!

---

### Post by arrrghhh on 2010-07-27
> **ObiDamnKenobi said:**
> Thanks for the link to the guide drdos! Looks very helpful.

arrrghhh; yes part of the reason I like the JBOD solution over RAID is to use disk of different size, and from different manufactures later. Buying all of them now, and having to rebuild the array with similar disks if I upgrade later, seems very inconvenient for my use. 

The WHS solution (I think) basically just creates a pool, and makes sure all files is copied to at least 2 disks. If one fails all the data will still be available, and without rebuilding a RAID. It can still be accessed on the server normally. The simplicity of this is appealing to me. But even without this I'm still leaning towards giving Ubuntu a try:)

I would like all my data to be duplicated, but something like weekly should be enough. If I buy disks in pairs (1 data, 1 mirror) and just have a a couple I guess it shouldn't be too much trouble keeping track. 

However, I'll go read up on JBOD and see if that is something to consider. 

Thanks to you both!

There's a project that's beta that may be right down your alley... I'm just not sure how much I trust my data to 'beta' projects ;)

[Greyhole](http://code.google.com/p/greyhole/) and [mhddfs](http://manpages.ubuntu.com/manpages/lucid/man1/mhddfs.1.html) are the two things I speak of.  Greyhole looks like it only works thru samba, so mhddfs may be more flexible in that sense... Let us know what you do, I've seen this WHS concept of throwing a bunch of disks together on these forums several times, and those are the two programs that I've found that could best replicate that kind of feature...

With that said, Greyhole seems to have a lot of options as to where the data goes, while mhddfs just seems to take several mount points and make them appear as one... Not quite what you're lookin for unfortunately.

---

### Post by ObiDamnKenobi on 2010-07-27
> **arrrghhh said:**
> There's a project that's beta that may be right down your alley... I'm just not sure how much I trust my data to 'beta' projects ;)

[Greyhole](http://code.google.com/p/greyhole/) and [mhddfs](http://manpages.ubuntu.com/manpages/lucid/man1/mhddfs.1.html) are the two things I speak of.  Greyhole looks like it only works thru samba, so mhddfs may be more flexible in that sense... Let us know what you do, I've seen this WHS concept of throwing a bunch of disks together on these forums several times, and those are the two programs that I've found that could best replicate that kind of feature...

With that said, Greyhole seems to have a lot of options as to where the data goes, while mhddfs just seems to take several mount points and make them appear as one... Not quite what you're lookin for unfortunately.

lol, after I posted here I searched around for drive extender/JBOD features in linux and came across the same Greyhole beta:D
Beta seems a bit sketchy for securing my data, especially many gigs of vacation photos in RAW etc.. But the features look very nice, and pretty close to what I'm looking for! Debating whether I should give it a try, perhaps just for my media.. 
Will give mhddfs a look too, thanks.

---

### Post by garfonzo on 2010-07-27
> **ObiDamnKenobi said:**
> ...Buying all of them now, and having to rebuild the array with similar disks if I upgrade later, seems very inconvenient for my use. 

...

I would like all my data to be duplicated, but something like weekly should be enough. If I buy disks in pairs (1 data, 1 mirror) and just have a a couple I guess it shouldn't be too much trouble keeping track. 


I have a Ubuntu Server doing just what you want to do. I stayed away from RAID setups because if you accidentally delete a file, the backup copy is deleted immediately too (as far as I understood). What I did was as you mentioned -- buying hard drives in pairs. I have 3 pairs of hard drives. Two are 320 GB and one pair is 500 GB. Thus, I have a total of 1140 GB of data space available. Since these are all pairs, I also have 1140 GB of backup available. 

Every week, I have a cron job execute a script I wrote (a one liner - very easy) which backs up only those files that have changed using **rsync**. After the first backup, each backup is really quick. 

With this setup, I can have any hard drive fail and have the backup in place with all my data in about ten minutes. These are true duplicates of my data with the same folder structures and no compressed backups or something. I could do a backup every night, but like you said, once a week is fine by me. 

I have Vista and XP computers in the house and all they see are the three available data drives and none of the backup drives.

---

### Post by ObiDamnKenobi on 2010-07-28
> **garfonzo said:**
> I have a Ubuntu Server doing just what you want to do. I stayed away from RAID setups because if you accidentally delete a file, the backup copy is deleted immediately too (as far as I understood). What I did was as you mentioned -- buying hard drives in pairs. I have 3 pairs of hard drives. Two are 320 GB and one pair is 500 GB. Thus, I have a total of 1140 GB of data space available. Since these are all pairs, I also have 1140 GB of backup available. 

Every week, I have a cron job execute a script I wrote (a one liner - very easy) which backs up only those files that have changed using **rsync**. After the first backup, each backup is really quick. 

With this setup, I can have any hard drive fail and have the backup in place with all my data in about ten minutes. These are true duplicates of my data with the same folder structures and no compressed backups or something. I could do a backup every night, but like you said, once a week is fine by me. 

I have Vista and XP computers in the house and all they see are the three available data drives and none of the backup drives.

Cool, nice to know:) Your system sounds good to me.

For my use (and yours it sounds like) the fact that a accidental delete, virus or corrupt file will instantly be copied over to the "back up" is not really a good solution. A straight up mirror image, in a universally accessible format (or in the normal file structure like yours) might take some more space, but I think it is easier and less prone to failure from corruption, malware etc. 

Just a question; I currently use the built in windows backup in my vista machine with 2x 1TB drives, but the backup software seems to just copy over new files. I.e it keeps growing even if I delete files on my data drive, as these are not deleted on the mirror. Will something like rsync just copy new files or actually sync, so that the two disk remain identical? If not I'm sure there is a tool that will.. :)

The problem is that with my SLR I tend to take hundreds of phots on occasion, but only want to keep 50% or less. But if these are backed up before I sort through them I get a bunch of non-keepers clogging up my back up drive.

---

### Post by arrrghhh on 2010-07-28
> **ObiDamnKenobi said:**
> The problem is that with my SLR I tend to take hundreds of phots on occasion, but only want to keep 50% or less. But if these are backed up before I sort through them I get a bunch of non-keepers clogging up my back up drive.

Rsync only copies - it syncs in a very intelligent manner, but it won't delete stuff for you.

---

### Post by garfonzo on 2010-07-28
> **arrrghhh said:**
> Rsync only copies - it syncs in a very intelligent manner, but it won't delete stuff for you.

I record TV programs through the week and store them on the server. These are all backed up. After I watch the show, I delete it. This deletion is mirrored on the backup and that file is no longer part of the backup. rsync will delete files if you tell it to (see code below).

[QUOTE=ObiDamnKenobi]Just a question; I currently use the built in windows backup in my vista machine with 2x 1TB drives, but the backup software seems to just copy over new files. I.e it keeps growing even if I delete files on my data drive, as these are not deleted on the mirror. Will something like rsync just copy new files or actually sync, so that the two disk remain identical? If not I'm sure there is a tool that will.[/QUOTE]

Edit: I didn't really answer your question first time around. Let me try again: 

I had the same frustrations with Vista's backup system. It kept growing and growing which is ridiculous. With the rsync setup I have going, the data disk (where users add and remove files) and the backup disk (inaccessible by users) are perfect replicas. The files and directories are all identical and, as a result, are identical in size. If I delete a few GBs from a data disk, my backup disk will reduce in size too (when the backup day comes). 

The other thing I like about how I have it setup is that if a data disk dies, I can just change the mount point to the backup disk and all computers on the LAN will have no idea that it is a different disk. Because the directory structure and files are all written to the backup disk in the same was as the originals, moving to a backup disk in the event of a failure is a two minute process. You don't even have to physically touch any hardware (other than remove the dead drive later). 


*original answer*

With my setup, I don't store anything on my local machine. I have mapped the server's drives to my computer so that if ever I save a document, it is automatically on the server. Thus, if something ever happens to my Vista machine (as did last week - majour virus wiped my Vista machine clean) I can reinstall Vista and not have anything lost. 

Having said that, I know that there are Windows versions of rsync which will allow you to copy in the same manner as the server. I looked into it briefly but decided not to go that route as I had mapped the network drives to the local computer. 

For what it's worth, here are a couple of resources I was looking at:
[Delta Copy - rsync like program for windows]("http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp")
[cwrsync - another rsync package for Windows]("http://www.itefix.no/i2/node/10650")

Just as an FYI, I have three shell scripts (one for each disk to be backed up). Within each shell script is this command:

```
sudo rsync --ignore-existing --delete --stats --progress -hrv --log-file=/garfonzo/320Alpha/BackupLogs/$(date +%Y%m%d)_320Alpha_rsync.log /garfonzo/320Alpha/ /garfonzo/320Betta/
```

Then I have a cron job which executes that script once a week.

---

### Post by arrrghhh on 2010-07-28
> **garfonzo said:**
> I record TV programs through the week and store them on the server. These are all backed up. After I watch the show, I delete it. This deletion is mirrored on the backup and that file is no longer part of the backup. rsync will delete files if you tell it to (see code below).

Never really understood why (maybe just one of those 'best practices' things) but I was told it's a bad idea to have rsync delete for you.  Meh.

---

### Post by ObiDamnKenobi on 2010-07-28
Thanks a lost garfonzo! Tons of helpful info about exactly what I'm looking for! 

The more I hear about your solution the more I think it is the best and simplest way to do it for my system as well. Maybe not as "elegant" as RAID, but I think it provides better redundancy for home use. I'm not exactly worried about up time.. 

Especially since you say it is possible to set up rsync where it will add and delete to always mirror the data drive, unlike the Vista back up center thing. 

I took a quick look at mhddfs that arrrghh mentioned above, which it seems basically will combine several disks into one mount point. To make the system a little easier to manage with lots of disks one could possible use this to create two mount points with identical capacity, one for data and one mirror? Hopefully it won't mess up and become inaccessible or something at some point.. And I don't know how easy it is to add more disks to this. Not really anything I would need at first I think, but maybe something I'll look into..

Thanks again!

---

### Post by garfonzo on 2010-07-28
> **ObiDamnKenobi said:**
> Thanks a lost garfonzo! Tons of helpful info about exactly what I'm looking for! 

The more I hear about your solution the more I think it is the best and simplest way to do it for my system as well. Maybe not as "elegant" as RAID, but I think it provides better redundancy for home use. I'm not exactly worried about up time.. 

Especially since you say it is possible to set up rsync where it will add and delete to always mirror the data drive, unlike the Vista back up center thing. 

I took a quick look at mhddfs that arrrghh mentioned above, which it seems basically will combine several disks into one mount point. To make the system a little easier to manage with lots of disks one could possible use this to create two mount points with identical capacity, one for data and one mirror? Hopefully it won't mess up and become inaccessible or something at some point.. And I don't know how easy it is to add more disks to this. Not really anything I would need at first I think, but maybe something I'll look into..

Thanks again!

You're quite welcome! I decided to go with Ubuntu Server instead of Debian (or some other variant) simply because of the great support I received from these forums. Now that I am up an running (and have been for a few years) I enjoy giving back and helping others within this community. 

If you need any help with setting things up, feel free to private message me and I'd be happy to help in any way I can.

---

### Post by drdos2006 on 2010-07-28
+1 for garfonzo's backup routine. It is what I use.
Here is a HOWTO you may find useful.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

regards

---

### Post by ObiDamnKenobi on 2010-07-30
> **garfonzo said:**
> You're quite welcome! I decided to go with Ubuntu Server instead of Debian (or some other variant) simply because of the great support I received from these forums. Now that I am up an running (and have been for a few years) I enjoy giving back and helping others within this community. 

If you need any help with setting things up, feel free to private message me and I'd be happy to help in any way I can.

Awesome, thanks! The info I've spied here and all the How to's I've seen linked are a great help, and have made me confident I can go with an Ubuntu server. Whether Debian or something else might possibly, maybe, somehow be better is not really concerning me:) As long as I can get it to work that will be good enough for now. 

May start looking for some parts on sale, but will probably spread the shopping out a bit. Maybe that will make the expenses easier to explain to the spouse as well, but she'll notice once it's sitting in the basement anyway so not quite sure;) 

Thank you drdos for the link, that will surely be helpful once I get started.

---

### Post by kgatan on 2010-07-30
I know this is a ubuntu forum but you should consider a FreeNAS for your needs.
ZFS device pool and raid capability with easy configuration.
FreeNAS can also run on extremly low end specs with good performance.

Youtube link which describes some features, they are a bit annoying but give you a good overview.
[http://www.youtube.com/watch?v=kZqGHKKIK48](http://www.youtube.com/watch?v=kZqGHKKIK48)

Very easy to set up and alot of other good services for a home server, lots of streaming support, smb/cifs etc etc.

If you chose to continue with ubuntu i read somthing about a program called unison which seems to do what rsync does but two way.
I havent tried it my self but check it out.

[http://www.ubuntugeek.com/unison-file-synchronization-tool.html](http://www.ubuntugeek.com/unison-file-synchronization-tool.html)

---

### Post by Atamido on 2010-08-16
> **ObiDamnKenobi said:**
> lol, after I posted here I searched around for drive extender/JBOD features in linux and came across the same Greyhole beta:D
Beta seems a bit sketchy for securing my data, especially many gigs of vacation photos in RAW etc.. But the features look very nice, and pretty close to what I'm looking for! Debating whether I should give it a try, perhaps just for my media.. 
The "beta" moniker for Greyhole is similar to the way that much of the software that ships with a Linux distro is "beta", which is to say that it works well, but doesn't have all of the features the programmer wants yet.  Greyhole is even enabled by default now in the Amahi distro.  The biggest disadvantage is the system requires that you access the files through Samba, otherwise Greyhole won't be aware of changes you've made to files.

To protect against malware/etc from deleting your files, just use a versioning file system on the drives you add to your pool.  Really, anything that creates snapshots you can view will work.  Just, pull up the snapshot for the drive, and then browse to the directory that Greyhole uses for its root on the drive.

Also, while Greyhole is authored by one person, it is a very active project, and the author is very nice and responsive.

---

### Post by kevinthecomputerguy on 2010-10-11
+1 for garfonzo ! (very nice)

If you add the -a option it will preserve the file permissions on the backups for you.

---

### Post by borahshadow on 2010-10-14
I don't think that there is anything wrong with the redundancy plan that i think you are persuing but I just wanted to mention what the best way is IMO.

if you really want to make your pictures and other data secure I would recommend a simple software raid mirroring 2 disks. Then either use another disk inside that machine or an external disk and do your weekly rsync backups to that. The RAID is not a means of backup by its self but with an external Rsync backup it becomes fairly robust because the RAID pretects you from drive failures between rsync runs.
Obviously this adds some extra expense and some extra complexity but I believe that it is worth it for the extra protection.

oh and contrary to popular belief a replacement RAID drive doesn't have to be identical to the others. As long as it is equal size (down to the sector) or greater you are good to go. The extra space of a larger drive will just be (usually) wasted though. That is with linux software raid. Other implementations could differ.

---

