---
title: "How do you dual booters manage files with both OS'S?"
date: 2009-10-25
forum: The Cafe
---

### Post by Morty007 on 2009-10-25
I just am not sure what to do here. 


I have been using ubuntu exclusively and keeping all my files and web surfing done there. But, now since I liked the Windows 7 beta so much I now have 7 on there along with ubuntu.

What do you all do?

Put all your files on one OS? 

Put your files on neither and use a external harddrive?


 I just don't know what to do and am not sure I should copy over my files in ubuntu over to windows. (I love windows 7's ability to search within files and then highlight them.)

Any suggestions?

---

### Post by Ravernomina on 2009-10-25
Mac OS X 10.6, Ubuntu Linux 9.10


Removable firewire on NTFS file system

---

### Post by Morty007 on 2009-10-25
Ok so you just keep every file on there, including anything new you generate Ravernomina?

---

### Post by Icehuck on 2009-10-25
I built a file server and store everything there.

---

### Post by Firestem4 on 2009-10-25
Linux makes it easy to access ntfs shares and partitions so I retrieve files from there if I don't make a duplicate.

---

### Post by Morty007 on 2009-10-25
I guess my main issue is that I am enjoying using Windows 7 at the moment. Any new files I'm putting on the external harddrive, but I'm afraid I will forget to follow up.

File servers, well that might be too complicated for me.

---

### Post by Icehuck on 2009-10-25
> **Morty007 said:**
> I guess my main issue is that I am enjoying using Windows 7 at the moment. Any new files I'm putting on the external harddrive, but I'm afraid I will forget to follow up.

File servers, well that might be too complicated for me.

All you have to do is install debian and install samba. You can make 4 changes to the samba config file and you are good to go.

---

### Post by cariboo on 2009-10-25
If you can install Ubuntu and Windows 7, a file server is a snap to set up.

---

### Post by Morty007 on 2009-10-25
Ok, any good links on a setting up a file server? I'm googling samba right now.

---

### Post by hoppipolla on 2009-10-25
I really do use Linux too much to worry about it, so nearly everything is on here. Otherwise yeah I would probably put them on another "shared" partition, or just bung them all on the Windows one as then I can access it from Linux. Whatever works for you really, but generally NTFS is the best bet for this so both OSs can access it :)

---

### Post by Icehuck on 2009-10-25
> **Morty007 said:**
> Ok, any good links on a setting up a file server? I'm googling samba right now.

[http://www.aboutdebian.com/lan.htm](http://www.aboutdebian.com/lan.htm)   

[http://wiki.archlinux.org/index.php/Samba](http://wiki.archlinux.org/index.php/Samba)

[http://www.samba.org/](http://www.samba.org/)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Samba will be your file server.   It doesn't matter which distro you use, those links are all relevant.

---

### Post by Megrimn on 2009-10-25
You could always install the EXT2 IFS drivers in windows.  It's compatible with ext3, but I haven't tried it with ext4.  then you could access your files in ubuntu from windows, like I do. [edit] just don't accidentally delete important files...

---

### Post by Morty007 on 2009-10-25
> **hoppipolla said:**
> I really do use Linux too much to worry about it, so nearly everything is on here. Otherwise yeah I would probably put them on another "shared" partition, or just bung them all on the Windows one as then I can access it from Linux. Whatever works for you really, but generally NTFS is the best bet for this so both OSs can access it :)

Well if I put everything on windows, and then I boot into Linux, your saying that I could then save whatever new files I have onto the windows partition? I know Linux will do that but I'm afraid that I'll then have some files on windows that I don't have in ubuntu.

Or am I not thinking clearly?

---

### Post by Xbehave on 2009-10-25
linux partitions (root, swap, boot?, home?) [ext3]
windows7 partition [ntfs]
data, go with [FAT32, ntfs if you need it]

No need to overcomplicate this,
windows can read ext3
linux can read ntfs
both handle data on FAT32 fine (not great for system files, under linux)

---

### Post by jocheem67 on 2009-10-25
What about a second HD in your rig? I'm using a backup drive in ntfs filesystem to store my data...accessable from both OS'ses. Pretty easy.
An external drive for extra backup does the "ensuring"thingie.

---

### Post by Chronon on 2009-10-25
@Morty007
If Ubuntu can read/write from/to the location of the files then I don't really understand in what sense Windows has the files and Ubuntu doesn't.

---

### Post by Morty007 on 2009-10-25
I don't mean to make this complicated, it's just that I want to have a gameplan before I transfer all my data over to windows. You guys are probably right, I'm just not understanding. 

Feel free to speak to me like a 4 year old if you have to.

---

### Post by hoppipolla on 2009-10-25
> **Morty007 said:**
> Well if I put everything on windows, and then I boot into Linux, your saying that I could then save whatever new files I have onto the windows partition? I know Linux will do that but I'm afraid that I'll then have some files on windows that I don't have in ubuntu.

Or am I not thinking clearly?

I dunno I've never had any issues I don't think with Linux reading and writing to NTFS, but I have heard bits and pieces. Windows also broke once, but I don't think that was due to that.

Safest option is a FAT32 or maybe NTFS extra partition for shared files :)

---

### Post by Dimitriid on 2009-10-25
I tried several approaches. First Option was have my main partition ( 512gb ) as ext3 and my boot partition ( 164gb ) dual boot Ubuntu 9.04 and Vista sp2.

Sadly, that set up did not work since the vista ext2 driver could not mount the drive ( some issue that basically required me to format it anyway ). So I decided to run my 512gb with NTFS and just be conservative about defrag ( about 2 times per month ) and that is my current set up, although I am considering formatting my 164gb drive again to do a clean Windows 7 install, although for my system the performance difference would little if anything at all since its fairly capable ( Phenom II x2 black edition which is I believe 2 cores at 3.1ghz with L1, L2 and L3 cache, 4gb of ram, Geforce gtx 260 the evga factory overclocked version )

Future plans including updating to 9.10 and perhaps running Arch + KDE mod when its available for KDE 4.3, although I might run that on virtualbox since I spend 90% of my time on Vista because of games.

---

### Post by Regenweald on 2009-10-25
Ubuntu mounts NTFS easily enough, I don't know how your HD/'s are set up but i have a legacy NTFS drive from my solely windows days. Ubuntu plays all my media on it perfectly (mostly music) and When I boot into XP, it sees the drive fine. I mostly need Xp to print, so when i need to, i mount the XP partition, drop the documents on the desktop, boot Xp and print. I can likewise pull any files from XP i need by mounting the drive while in Ubuntu.

basically, I'd suggest a NTFS partition or drive if you need to share between OS'es.

---

### Post by Morty007 on 2009-10-25
Here are my partitions. Since ubuntu has so much I guess I can cut it in half and make it NTFS. 


[[img]http://xs1244.xs.to/xs1244/09430/partitions309.jpg[/img]](http://xs.to)

---

### Post by Xbehave on 2009-10-25
WHich one is ubuntu
100GB = windows
if your not storing any data 20GB+swap(1.5*ram(ish)), should be enough for ubuntu (20 is an overestimate I usually have <10 for / and 5 /home if my data is elsewhere)
The rest can either be added to your windows partition or made into a partition to store your shared data (Music,Docs,etc), I recommend FAT32 for that other recommend NTFS.

---

### Post by Kingsley on 2009-10-25
I just have a fat32 partition to store the files that I'll use in Linux or Windows 7. It works pretty well because there's no need for me to worry about transferring media files between Linux/Windows releases.

---

### Post by Skripka on 2009-10-25
> **Megrimn said:**
> You could always install the EXT2 IFS drivers in windows.  It's compatible with ext3, but I haven't tried it with ext4.  then you could access your files in ubuntu from windows, like I do. [edit] just don't accidentally delete important files...

EXT2IFS does NOT work with Ext4.  Not yet in any case.  Just sayin.

Also for ye recommending FAT32 as a go between...yes-sort of...UNTIL you have to DEFRAG that drive.  Defragging a current generation sized HDD...usually at least 80GB+. or partition is NOT fun.  Which if drive contents change-can be very often and even more annoying.

NTFS can get annoying, due to drive/folder permissions

Usually, NO ONE spends time in 2+OSes working the same files-for similar amounts of time.  Usually one ends up being a "backup".  My Win7 drive is basically a slave to my Linux drive.  Every now and again I just duplicate My Docs from Linux to Windows.  I spose if I was bored, I could do a cron/rsync to do it automagically.

---

### Post by handy on 2009-10-26
My set up is of no help to the OP, but I'll spit it out here anyway:

iMac running OS X & Arch, I have multiple partitions in Arch, two of which are in the Ext3 format, for the sole purpose of them being fully R/W accessible from OS X, due to the simple installation of *ExtFS for Mac*.  

It works like a charm. :)

I also have a FreeNAS setup on another box; but I haven't bothered to make it accessible from OS X, as I back up anything important from OS X, onto one of the Arch/Ext3 partitions, & the data on those partitions are backed up on FreeNAS

---

### Post by Paqman on 2009-10-26
I store all my data on a RAID1 NAS. We don't keep anything important on any single-drive machine. Doing it that way gives much greater protection to our data, is a lot more flexible, and means the data is available to any device on the network. 

I'd hate to have to store my data on a single machine after having lived with this setup for a while.

---

### Post by Danbo19 on 2009-10-26
I'm surprised no one has suggested dropbox yet. I use it to sync files between my windows partition, Ubuntu partition and my all-Ubuntu desktop. As far as simplicity goes nothing could be easier. You only get 2Gb free, which is plenty for my documents and papers for school. If you want more you have to pay, so depending on how many files you need to be synced between windows and Ubuntu you may not feel like paying for it when you can do the whole file server thing for free.

---

### Post by drumsticks on 2009-10-26
Be mindful that fat32 or ntfs does not preserve unix file and folder permissions.  Conversely, fat32 and ext2/3/4 does not preserve Windows file and folder permissions.  

As far as I know, there is nothing we can do about this permission (or ACL or xattr data).  Since I*spend 99.99% of my time in Ubuntu, I don't care much for Windows permissions, and use ext3/4 for my primary storage.

---

### Post by handy on 2009-10-26
> **Paqman said:**
> I store all my data on a RAID1 NAS. We don't keep anything important on any single-drive machine. Doing it that way gives much greater protection to our data, is a lot more flexible, and means the data is available to any device on the network. 

I'd hate to have to store my data on a single machine after having lived with this setup for a while.

Do you consider RAID-1 to be a safe way to store your data?

The word is, it is the fastest way to duplicate corruption...

---

### Post by Morty007 on 2009-10-26
Thanks for all the suggestions.

 I did an experiment this morning and went into Ubuntu and started to do a direcotry comparison using meld. (Which is absolutely fantastic.) I then copied info to windows and copied docs from windows to ubuntu. Worked fine. 

I don't know much about raid. It looks like my large files are just my pictures collection. So my thinking is copy everything over to windows except all my pictures and just leave that on the external drive.

---

### Post by AlanRick on 2009-10-26
Under Windows I always had a separate file partition (NFTS). So when I made the pc dual-boot with ubuntu I just stuck to keeping ubuntu data on this separate partition, too. The files really don't care which OS is accessing them.

I copy the files daily to my dropbox folder with a batch-job to make sure they're backed up.

---

### Post by handy on 2009-10-26
> **Morty007 said:**
> Thanks for all the suggestions.

 I did an experiment this morning and went into Ubuntu and started to do a direcotry comparison using meld. (Which is absolutely fantastic.) I then copied info to windows and copied docs from windows to ubuntu. Worked fine. 

I don't know much about raid. It looks like my large files are just my pictures collection. So my thinking is copy everything over to windows except all my pictures and just leave that on the external drive.

RAID is great for those that need such systems, BUT if the data is important, you always have a backup on a separate machine, & if it is really important the separate machine is at a different location.

---

### Post by Skripka on 2009-10-26
> **handy said:**
> RAID is great for those that need such systems, BUT if the data is important, you always have a backup on a separate machine, & if it is really important the separate machine is at a different location.

He who laughs last usually has at least 3 good backups.

---

### Post by The Real Dave on 2009-10-26
> **Morty007 said:**
> Ok, any good links on a setting up a file server? I'm googling samba right now.

Easiest and fastest way to set up a FileServer - [FreeNAS]("http://www.freenas.org"), I use it on mine, to share between my computers and OS's, and media stream. On my server, it boots from the CD, loads into RAM and then takes its config from a usb drive. That lets the harddrives spin down when not being used. Its a small, but powerful OS, and, seeing as its all administered through a WebGUI, simple to set up. It'll do software RAID, encryption, and stuff like active directory even. 

I also have a large <gag>vFAT</gag> partiton , the idea being that both OSs could read it. What a terrible idea that was.


[Hak5 video on FreeNAS]("http://www.youtube.com/watch?v=mgJNzyTSv6c") (Youtube, there's plenty of cool FreeNAS videos there)

---

### Post by handy on 2009-10-26
> **Skripka said:**
> He who laughs last usually has at least 3 good backups.

I have stuff backed up from OS X/Arch onto at least 1 other (sometimes 2) partition(s) on the same machine & all onto the separate FreeNAS box.  Particularly important info' is also on more than one DVD.

***[Edit:]** Some things I store in my email account also.*

---

### Post by Paqman on 2009-10-27
> **handy said:**
> Do you consider RAID-1 to be a safe way to store your data?

The word is, it is the fastest way to duplicate corruption...

I'm mostly concerned about hardware failure. Since most of the data a home user (ie: me and the wife) is going to store is read-only and has truckloads of error correction, data corruption is a pretty minor concern.

By contrast, the reliability of spinning hard drives leaves a lot to be desired IMO. To mitigate against faults on the RAID controller side I do take a periodic manual backup of the array onto a spare drive that's kept separately.

---

### Post by Nevon on 2009-10-27
As I have Windows installed on an NTFS drive, I can access that from within Ubuntu. As for the other way around, I just have to make sure to transfer my data from within Ubuntu to the Windows drive if I need it there. It's not ideal, but it works well enough for me.

---

### Post by Nerd King on 2009-10-27
Personally I put stuff I don't want to lose on my linux partition as I won't let Windows near it anyway. I put the files I need on both systems on the windows partition, but make sure I have safe backups on my external. My external is unplugged when I'm in Windows.

---

### Post by hessiess on 2009-10-27
Don't use Windows, but Subversion works well for syncing data across an arbetery number of computers, or multiple OS's on the same computer, though you would need another computer as a SVN server (assuming you are not running a VM).

---

