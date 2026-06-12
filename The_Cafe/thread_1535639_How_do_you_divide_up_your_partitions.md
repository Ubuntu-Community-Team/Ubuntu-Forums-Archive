---
title: "How do you divide up your partitions?"
date: 2010-07-21
forum: The Cafe
---

### Post by Nick_Jinn on 2010-07-21
Lets say you have a 1TB primary hard drive and also a second internal hard drive that you took from a laptop because your desktop has a special mount for it....thats something like 1232gb of storage.

Lets say you cant stand windows but you still need it for a class, might use it for gaming which has some large files and mods, and also maybe some photoshop/Wacom Bamboo work until support is a little better.

I like Mint but I also like Ubuntu Studio. Id like to expiriment with a few desktop environments including enlightenment. I might want to play around with developing some spin offs of puppy linux.



Regardless of what I want, how would you partition up your space? What tricks would you use for shared space? Shared /home folders? Keeping operating systems seperate? Fat32 vs NTFS? What else is recognized by Windows and Linux?

---

### Post by Wee_Guy on 2010-07-21
I would give each OS an appropriately sized partition (Ubuntu isn't going to need half a terabyte) to itself and then use the rest of the space for a shared /home partition. Alternatively you could split the /home partition and add another one just for backups. As far as filesystems go, although FAT32 can be read by most OSes, there is a 4Gb size limit for files, which could cause problems if a game has a file over 4Gb or if you intend to store videos on there. NTFS is probably fine.

---

### Post by Nick_Jinn on 2010-07-21
I was thinking the following.


180gb for XP (installed first)
232gb Fat32 shared folder for music and pictures and most storage.
120gb NTFS for large movie and game files
300GB Linux Mint
200gb Ubuntu Studio
40gb Swap (useful for USB OS sessions)
20gb Puppy Linux
>>about 100gb to play with other operating systems.

But I am somewhat interested in sharing a /home folder with some of the highly compatible systems...ones that wont screw up dependencies....are there? If Studio and Mint both use Gnome will this be a problem? It would be cool if I had room for something that used Enlightenment.

---

### Post by Wee_Guy on 2010-07-21
What about just combining the FAT32 and NTFS shares into one big NTFS share?
Also, I don't think any OS is ever likely to need 40GB swap unless you have very little RAM and run *loads *of virtual machines(and have *massive *hibernation files). See _[here]("https://help.ubuntu.com/community/SwapFaq")_ for info on swap.

Also, are you likely to need so much space in each OS? Wouldn't it be easier to have a much smaller partition for Ubuntu and Mint (maybe around 50GB) and keep all the data in the share partition, that way you can have a bigger share partition and thus more room for stuff.

---

### Post by Nick_Jinn on 2010-07-21
It might be good to have one giant partition, but there are still some linux systems I work with that read FAT32 and not NTFS.....I think. Is that universal yet, or is Ubuntu leading the way with that?

I could go with 500gb of NTFS and maybe just 40gb of FAT in case I need to transfer some files to something more compatible.....does Android read NTFS?

I have heard mixed things about sharing /home partitions. I guess its doable to make the NTFS partition the default download location for all files? Can games in windows run from a seperate NTFS partition? Can WINE in Ubuntu read and play games from my WINDOWS C drive?

I guess it does make sense to have one really big NTFS partition, though I cant really put one partition on 2 hard drives of unequal size.....the laptop drive is only 250gb.


When I use operating systems from disk they very often crash due to lack of room. If I am doing a lot of editing or even want to convert media, I am going to need tons of SWAP space......I would be using the swap space like a solid state hard drive for live CD sessions. I think I will need a large swap area. 

Thanks for the feedback though....How would you divide it up in total, including the 232gb of laptop hdd?

---

### Post by sidzen on 2010-07-21
Once a person wraps his head around it, LVM is the way to go ---
 p, li { white-space: pre-wrap; }  [http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)
 [http://www.ibm.com/developerworks/library/l-lvm2.html](http://www.ibm.com/developerworks/library/l-lvm2.html)
 
 [http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
 [http://ubuntuforums.org/showthread.php?t=1347375](http://ubuntuforums.org/showthread.php?t=1347375)

---

### Post by Wee_Guy on 2010-07-21
What about:
180GB for XP
100GB for Mint
100GB for Ubuntu
20GB Puppy Linux
Thats a total of 400GB for OSs leaving 624GB for  data.
100GB FAT32 share
524GB NTFS share

I think there might be a performance increase if the Swap is on a separate drive from the OS, so you could put 40GB Swap on the laptop drive and leave the rest of it free for exploring other OSs.

---

### Post by handy on 2010-07-21
**@Nick_Jinn:** *"Lets say"* sounds as though you are bored & are just amusing yourself on the forum. ;) I've been wrong before... Do the same thing myself all the time though. :)

I've used systems with a great variety of partition numbers, sizes & file systems; I found that in the end the difference in their performance turns out to be bugger all. I have had no problems with the reliability of the various file systems, though that topic is more than well documented on the net.

So I suggest that (if you are seriously asking) you just choose a partition scheme that suits your needs & one of the range of known to be reliable file system to satisfy your needs.

I satisfied my need to do something for the moment, I hope that the above helps you to some degree...

---

### Post by aeiah on 2010-07-21
id use the laptop hdd almost purely for backup, since it runs a bit slower than the 1TB and i like having a physically separate hdd for backups in case of failure. since i mostly use linux (well actually, i dont have windows at all but we'll say i do since you do) id format the laptop with a swap partition and an ext4 partition with the label 'backup' and use backintime for incremental daily backups of important areas.

the 1TB hdd would get a an ext4 linux partition (no point having a separate home partition in this case imho), an NTFS windows partition and a large NTFS storage partition. 

my windows install would have it's 'documents and settings' area set to use an area on the large storage partition (Drive E: or whatever), and in linux my ~/Documents, ~/Pictures, ~/Music ~/Video directories would be mount binded to the same location as their respective windows folders, so all my documents etc are available to both in their natural location.

whether you want to install your software to this NTFS storage partition or whether you wish to make the windows partition large enough for these is up to you.

---

### Post by aeiah on 2010-07-21
> **sidzen said:**
> Once a person wraps his head around it, LVM is the way to go ---
 p, li { white-space: pre-wrap; }  [http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)
 [http://www.ibm.com/developerworks/library/l-lvm2.html](http://www.ibm.com/developerworks/library/l-lvm2.html)
 
 [http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
 [http://ubuntuforums.org/showthread.php?t=1347375](http://ubuntuforums.org/showthread.php?t=1347375)

i spent 5 days, miles from home, trying to rescue data from a server that used virtual machine images on top of an ext3 data partition on top of LVM on top of software raid. i hate LVM with a passion (and the idiot who set it up badly). :p

---

### Post by The Real Dave on 2010-07-21
I'd use the laptop drive for backups personally, as one large NTFS partition, so that you can do backups from Windows and Linux.

I'd be careful how you partition the 1TB, seeing as it sounds like you'll be swapping distros a lot. Sharing /homes isn't a good idea IMO, because you'll always want to have one thing one way on say Mint and another on Ubuntu. it'll just get messy. 

I'd do it this way,

Laptop Drive
|
\
 Physical Partition - 250GB
    |
    \ 250GB - NTFS 

TB Drive
|
\
 Logical partition - 70GB
|   |
|   \ Ubuntu / - 15GB [ext4]
|   \ Ubuntu /home - 55GB [ext4]
\
 Logical Partition - 70GB
|   |
|   \ Mint / - 15GB [ext4]
|   \ Mint /home - 55GB [ext4]
\
 Logical Partition - 70GB
|   |
|   \ Empty Space - 70GB 
|
\
 Physical Partition - 715GB
|   |
|   \ Data Partition - 715GB [NTFS]
|
\
 Physical Partition - 70GB
|   |
|   \ Windows Partition - 70GB [NTFS]
\
 Physical Partition - 5GB
    |
    \ Linux Swap - 5GB [SWAP]


I presumed that Mint and Ubuntu will be your two distros that you stick with, and so deserve separate /homes for stability and security. 

15GB is plenty for a / in Mint or Ubuntu, seeing as you won't be hosting a massive website from /var/www or generating loads of logs. I created mine with 9GB and after a year there's more than 2GB free, and it's stayed like that for months. 

The unused space will make it easier to move the logical partitions, and to try out other distros. When installing other distro's here, particularly if you're just trying them, don't bother separating / and /home. 

The Data partition being in NTFS ensures you can read and write it from Windows and almost all Linux distros. Having smaller /homes for Mint and Ubuntu isn't a problem then, because you'll be storing almost everything on the Data partition. It'll help keep things tidy between OSes, trust me.

70GB again will be plenty for the Windows install, because anything large will be stored on the Data partition. Make sure that Windows only generates pagefiles (Window's version of swap files) on the 70GB partition to prevent wasting space on other partitions. I've left it below the Data partition so that it'll be easier to increase in size, if need be.

5GB of swap should be plenty, even if you are GIMPing on LiveCDs. How much RAM does your computer have? I've 1.5Gb with 1GB of swap, and never run into trouble, even when VMing, or GIMPing from a LiveCD ;) Rule of thumb generally is, for a light user, actual RAM amount minus 1GB, medium user, actual RAM amount, heavy user, <10GB, crazy/paranoid >10GB ;)

Hope this helps, and just for show, here's my main drive.

[[img]http://linuxexpresso.files.wordpress.com/2010/07/7-july-2010-gparted.png[/img]]("http://linuxexpresso.wordpress.com/")

---

### Post by samalex on 2010-07-21
I used to meticulously divide my drive into various partitions, but the last time I reinstalled I just created an 8 Gig partition for swap, 15 Gig partition to be encrypted (banking, passwords, etc), and the rest just mounted as root for everything else.  I'm backing-up my stuff to an external drive, so I don't really need /home split out anymore.  I used to do this so I could reinstall and leave the /home partition alone, but as long as I have back-ups it's not a huge deal anymore. 

Sam

---

### Post by K.Mandla on 2010-07-21
64mb /boot, ext2
128mb swap
4gb root, ext2

Whatever is left is /home, ext2.

---

### Post by Nick_Jinn on 2010-07-21
While I do enjoy the discussions I definitely feel like I am learning a lot. I never heard of LVM and I dont know enough about the debate between sharing and not sharing home partitions.

Both Ubuntu Studio and Mint will have similar settings. Other systems might have different settings or desktop environments. I want to play with Enlightenment a little more.

I may actually host a small website from my desktop, and I also download a lot of games and media tools.....I might go with 25gb partitions just to be safe....then 10gb partitions for my experiments. 


Thank you everyone for the input.


Is it pretty easy to bind the default locations to an NTFS location?



I do have 2 DVD roms......i imagine that if I was using Devede to convert videos into DVD videos I could easily eat up my 4gb of ram.

---

### Post by pinguy on 2010-07-21
[IMG]http://img80.imageshack.us/img80/1025/devsdagparted006.jpg[/IMG]

**Windows 7:** is ntfs with 35GB of space and mounted in Ubuntu as /windows
**Ubuntu:** is ext4 with 15GB of space and mounted as /
**Home:** is ext4 with 20GB of space and mounted as /home
**Documents:** is ntfs with what ever space is left and mounted in Ubuntu as /dos with short cuts and symlinks coming from my **Home** folder *(Ubuntu)* and **Documents** folder *(Windows)*. So all my Videos, Music and Downloads are setup the same in both OS's.

---

### Post by The Real Dave on 2010-07-21
> **Nick_Jinn said:**
> I do have 2 DVD roms......i imagine that if I was using Devede to convert videos into DVD videos I could easily eat up my 4gb of ram.

Nope. My Pentium IV with 1.4GB RAM handles it perfectly. It has 1GB of swap, which isn't used whilst converting.

---

### Post by handy on 2010-07-21
> **Nick_Jinn said:**
> While I do enjoy the discussions I definitely feel like I am learning a lot. I never heard of LVM and I dont know enough about the debate between sharing and not sharing home partitions. 

I like to use a separate /home, but when I've used multiple distro's on the same box I don't share /home. If you don't know what you are doing, you can easily have permission problems due to multiple distro's using the same /home. I find it much easier to have a separate /home & another larger storage partition that doesn't have any of the problems of shared ~. files. More knowledgeable users can know how to avoid such problems. Though I'd still use the same partition scheme if I knew more about permissions anyway. :)

I do the following on my No.1 box which is an iMac (which explains the small 200Mb fat32 EFI partition), I've attached a GParted image below.

If anyone is wondering why the /store is ext3 when /home is jfs, it is because I use software under OS X, that allows me to read/write to ext3 but it doesn't know how to access jfs. Though I'm now using a ReadyNAS box, which has obviated the need for my accessing the Linux partitions on the shared iMac drive.

---

### Post by aeiah on 2010-07-21
> **Nick_Jinn said:**
> 

Is it pretty easy to bind the default locations to an NTFS location?



yea. i did it on my girlfriends parents' dual boot machine. works just the same way as it would with a linux filesystem - you have to make sure the partition is mounted already in a normal way and then you can pick out specific directories that you want bound to different places. 

i have a few binds set up on mine for various reasons (owl and giantpeach drives got merged into a new 1.5TB drive called 'storage')

note the FTP binds routed to the guest account. you'd do a similar thing on each of your OSes if you wanted to keep the same Documents folder, but not the same settings in home

```


# 1.5TB storage
UUID=e517e737-5e59-4167-ab58-b272bc84c783 /media/storage ext4    defaults        0       2

# binds, mostly for xbmc, exaile & scripts
/media/storage /media/owl	bind	defaults,bind 0 0
/media/storage /media/giantpeach	bind	defaults,bind 0 0

# binds for ftp guest user account
/media/storage/television /home/guest/tv	bind	defaults,bind 0 0
/media/storage/film /home/guest/film	bind	defaults,bind 0 0
/media/storage/music /home/guest/music	bind	defaults,bind 0 0

# bind for nfs
/media/storage /export/storage	none	bind 0 0


```

my FTP is LAN only :p

---

### Post by Linux000 on 2010-07-21
I would run a small partition per OS(Win 7 will need a larger one), then seperate home partitions for the Linux OSes, a Seperate Documents for Windows, maybe 6GB of swap, and the rest set for File Storage. So it would look like this.

Laptop Drive - 250GB
-Windows 7 - 40GB
-Ubuntu Studio - 25GB
-Mint - 25GB
-Extended Partition
   \-Puppy Linux(with /home) - 15GB
   \-Swap - 5GB
   \-NTFS Files - Whats left Over(Little Less that 140GB)
 

Desktop Drive - 1TB
-Backups(Of Laptop Drive OSes) - 150GB
-Ubuntu(so if the Laptop Drive Goes, you still have an OS)(with /home) - 50GB
-Files - Whats Left Over(Little Less than 300GB)
-Extended Partition
   \-Ubuntu Studio /home -  100GB
   \-Mint /home - 100GB
   \-Win 7 Documents - 250GB
   \-Other OSes - 50GB

Here's what I have(500GB Laptop Drive)
*Windows is Hibernated, so Ubuntu Can't mount it


Also, I wouldn't share /home partitions across OSes, because the Configuration files for the OSes are in that folder and it could become a mess if Ubuntu tried to act like Mint and the configuration could mess the computer to the point of having to repartition it for use.

---

### Post by Nick_Jinn on 2010-07-21
Hmmm. Is there an Ubuntu live chat? I might need somebody to walk me through this.

---

### Post by Linux000 on 2010-07-21
Yes, irc is there for support, the server is irc.ubuntu.com , channel #ubuntu

---

### Post by oldfred on 2010-07-21
I like separate data partitions, NTFS for any data to share with windows and ext3 or ext4 for all other data. I only have 1GB in my /home since it only has hidden user settings. I have many 20-25GB system partitions and created a little script to edit fstab and link all my folders into each new install so all my data, firefox profile & thunderbird profile are the same everywhere.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on some of the comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Nick_Jinn on 2010-07-21
Thank you for the suggestions.

Windows is already on the TB hard drive though. You dont think there will be a performance dip if I run my primary operating systems from the laptop SATA disk?


I am mostly going for functionality with the partitions rather than speed gains, but I do worry about what kid of loads the laptop hard drive can handle......maybe leave Windows on the TB but Linux on the laptop hdd?

Can I have /root on the laptop and /home on the TB hard drive? Would I gain any speed by using both hard drives separately? Lose speed?




The final problem to deal with is Conflicts.......I discovered that you cant boot Mint and MoonOS at the same time....which sucks because Moon is kind of pretty for E17 (Another Ubuntu derivitive). I am not sure if Enlightened Gnome (Based on hardy) would also conflict.....it like crashes if they are both in grub. Anyone else dealt with this?

It may be necessary to split up a few systems to seperate disks.....or maybe keep their /root partition on pen drives and their /home partition on the internal drive?

---

### Post by Linux000 on 2010-07-21
If the laptop drive is old, running Windows from it might not be a good idea, but I see no problem with or load, it's just like running it in a laptop, you would loose speed when you copy from the Laptop to the TB, but not if you copy from the TB to the TB with your OS on the Laptop. Hope that made sense. I don't really see using the /root folder all that much, but I wouldn't put it on a flash drive that could be pulled out and give you mounting errors when you boot.

---

### Post by radddi on 2010-07-21
If I had a 1TB hard drive...

sda1: 30GB NTFS - Windows XP/7
sda2: 30GB ext4 - Ubuntu / drive
sda3: 100GB ext4 - Ubuntu /home drive
sda4: 800GB NTFS - Storage - movies, music, software, manga
free space: 64GB for experimentation (evil)

:popcorn:

---

### Post by Nick_Jinn on 2010-07-21
The laptop hard drive is brand new almost, Serial-ATA 250gb Western Digital Scorpio Blue. Class B. I dont have the RPM or cache.

The TB Hard drive is Samsung 7200 RPM, 32mb



Are both fine for gaming? I know the laptop hdd played Oblivion on the old computer and fallout, but I also dont want it to burn out early.



Right now I am running puppy linux from a USB drive. Is it normal for the screen to keep cutting out and going black for a few seconds?

---

### Post by chriswyatt on 2010-07-21
Deleted.

---

### Post by sidzen on 2010-07-22
> **aeiah said:**
> i spent 5 days, miles from home, trying to rescue data from a server that used virtual machine images on top of an ext3 data partition on top of LVM on top of software raid. i hate LVM with a passion (and the idiot who set it up badly). :p
  Somehow someone alwys manages to botch up a good thing!  II used to use SCSI Raid setups, so LVM (if set up properly) is a vast improvement.  Sorry to hear of your problems, though.:sad:

---

### Post by Nick_Jinn on 2010-07-22
I am probably going to try to put most of my linux distros on the laptop hard drive....its a pretty new and good quality hard drive, despite being laptop.....I just hope gaming from it doesnt burn it out. It should be better ventilated in there at least.


However, whoever said I wouldnt need more swap room is wrong. I do more than GIMPing. I tried to download another distro and burn it from my second optical drive and it stopped half way so I couldnt finish downloading it...let alone make a checksum image and burn it. 

What if I was going to edit a dual layer DVD from a live Ubuntu Studio DVD, and needed the original plus the results and then copy it to DVD?



Is there a way to put /home and root on different partitions?

How do you share /home (messy or not) without overwriting the existing data by reformatting it?

---

### Post by Dustin2128 on 2010-07-22
Personally, I'd give whatever was my main distro at the time a terabyte, with the rest left over for my constant distro experimentation. Windows, I'd have in a virtual machine with only as much space as it needs for the apps I'm running. Excellent deterrent to performing security dependent tasks (online banking) in windows simply because its already up.

---

### Post by Nick_Jinn on 2010-07-22
That sounds alright actually. The only thing I would be missing is a few games that I can theoretically still get working on my new system.

---

### Post by Sean Moran on 2011-01-07
> **Nick_Jinn said:**
> 

Is there a way to put /home and root on different partitions?

How do you share /home (messy or not) without overwriting the existing data by reformatting it?

I thought it preferable to resurrect a six-month old thread than start anew.  This is exactly what I've been thinking of writing about for the last couple of days so here is the place to write it.

Years ago it was always the go to setup Linux servers with separate /boot & /home partitions, and sometimes more, but I've spent the last 18 months installing my Ubuntu client desktop systems with the minimal requisite of two: root and swap.  All my data stays on other partitions that remain unaffected by the two or three hundred installs I've probably repeated since discovering Ubuntu in early 2009.

There was a very informative thread on this forum a couple of months ago about disk fragmentation, and the good advice therein was what got me thinking about keeping a separate partition for /home.  According to the thread, by keeping the more usually read-only system code (root) on a separate partition to the more frequently read-written user data (home), we can apparently reduce the degree of fragmentation to the system files, ergo maintain better HDD read speed = faster performance in theory. 

A bit of a new year's resolution that I decided to start specifying a separate /home partition when installing new distros.  To answer the questions quoted above, it starts at install time by selecting partitions manually, and setting both your root (/) and then your /home partition before proceesing with the installation.  The step to remember is to tick YES to format the root (/) partition, but if you already have data on your allotted /home partition, make sure to tick NO (edit: leave UNTICKED) to formatting it.  Ubiquity will still set the partition as your home partition without the need to format it, and that's where the fun begins.

In summary, I've now got this Karmic distro on /dev/sda2 and two Maverick distros on /devs/sda5 & 6 all reading from a communal home folder on /dev/sda7, as well as a lot more room on each of the three 8Gb root partitions.  No idea if the performance is any better but it's only been a few days and all three new distros are only using 50-60% of their 8Gb partitions, so too early to expect any deterioration by fragmentation.

The icing on the cake is that any time I want to run up a new installation, providing that the specified /usr/share/backgrounds file ends up in the right place, the first boot comes up with the standard desktop background, the standard panel layout, the same menu configuration, and even the preferences and bookmarks for Firefox and SeaMonkey.  This was an unexpected bonus.  

All three installs are somehow synced into that same /home/sean arrangement and so far there don't seem to have been any problems whatsoever with permissions.  Possibly because I'm using the same username throughout all distros, and NOT encrypting anything.  

I hope that Handy or anyone with more expertise than I might shed some light on what possible permissions hiccups I should be on the lookout for, as there are a gamut of different apps subletting real estate in this new omnipresent /home directory, and every chance that something is bound to go wrong sometime soon.

Please let me know if there's anything I should take into consideration, but in answer to the question probably answered long ago somewhere else: that's how you do it.

---

