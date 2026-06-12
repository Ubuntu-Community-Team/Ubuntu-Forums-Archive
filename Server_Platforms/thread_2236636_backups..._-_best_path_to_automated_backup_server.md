---
title: "backups... - best path to automated backup server?"
date: 2014-07-28
forum: Server Platforms
---

### Post by mastablasta on 2014-07-28
so, to continue my "was hacked thread": [http://ubuntuforums.org/showthread.php?t=2235645](http://ubuntuforums.org/showthread.php?t=2235645)

I am searching for personal backup solution (automated). I've been searching for it for a while now. I am thinking maybe it is time. 

what I am interested here is what software solution to use as well as what hardware solution.
I intend to backup the website, pictures and home videos. I do not need any video streaming or anything like that. what I do want is an energy efficient, good "bang for the buck" and quiet box. the issue is also the setup.
so:

1. what software is best to be used (owncloud? or just basic server and rdiff or rsnapshot) and how to set it up (software RAID or some type of rsync?) - I have 1 windows xp, 1 windows 7 starter/Kubuntu (dualboot), 1 Android device (perhaps this one could pass with manual backup), 1 RPi and 1 Kubuntu Linux on LAN. And then outside of LAN we have 2 Kubuntu Linux and 1 windows XP. The Linux will stay on LTS if that matters. the computers are not on all the time so I am thinking weekly automated backups.

2. i was thinking of putting the server software on USB flash drive. is that a good idea? logs and such would be on disks.

3. hardware - what hardware to use. I was chekcing out Atom boards, but when i put it all together it is not much cheaper or is even more expencive than the HPProliant Microserver N54L with 4GB ram. The server's CPU does need more power and has USB 2.0 ports (which could potentially add even more external disks) as well as DVD drive (where one could potentially add 4 additional 2.5" drives later on). It seems to be quiet and does still hove a fan. would something fanless be better? i have onyl one bedroom apaprtment and have ocmputer sin living room. i plan to modify bedroom into kids room and use living room as our bedroom, so quiet is good at night...
would it be better to use Synology NAS? they are a tad more cheaper but those that are chepaer seem to have less disk options and a much weaker CPU.

4. what disks to use? i was thinking (for starters) 2 x 2TB disks from different manufacturers. One could maybe be more durable yet slower NAS version. does size matter? is it better to have smaller drive?
at the moment we have about 350 GB of digital data on my end and probably about half of this amount outside of LAN. BUt it is regulary increaseing and we haven't did much HD videos or higher resolution pics (5Mpixel at the moment).

5. network setup - the ISP provided me with modem/router with 4 network ports and a wi-fi dongle for wi-fi connection. 1 network port is occupied by TV communicator. 2 are used by deskotp PCs. and 1 is used by RaspberyPi which is acting as a media center.
I have a small 8 port switch and a fresh upacked wifi router (forgot the brand at the moment but supposedly it is a good one). i was thinking to setup a switch on a connection where RPi and new server would reside. I think it might be more energy efficient. Or would it be better to add a router here?

The backup server/NAS would go immediatelly behind the TV. is that a good idea? would there be any electornic interference?

one problem is that there are a limited number of electricity sockets in the room. but i guess same socket should handle a bit more plugged in devices as they all don't take much voltage and power.
If i could i would store the server in the "storage room" but getting all the cables there might be an adventure. Two armoured concrete walls to get throough on the shortest route... the other option could be to use Wi-fi but Wi-fi is not as realiable as cable, it often just doesn't work for some reason (perhaps this would work better if i used the unpacked router?!) and others could listen more easilly to it. Opinions on this option? Wifi would then be either via USB dongle or if i occupied a PCI Express x1 place (but then i could never add 4 more drives in DVD drive emtpy space).

---

### Post by TheFu on 2014-07-28
You described a bunch of things, but not some of the most important things - 
* how much daily-change data?
* how much never-change data?
* budget?

Your signature has Redobackup - why not select that? How is it deficient?

-- update --
I do 3 different types of backups and have described them here and [elsewhere]("http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview") at length already, so won't be repeating the details.
* OS config, personal settings and personal daily-change data (NOT the OS)
* Never-change data
* Mandatory OS images (Windows-only).
Those 3 things are handled differently, but in the end, about 20 servers are backed up in less than 1 hour total nightly with 60-120 days of backup points and it all fits into less than 500G of storage.  Er ... except the "never-change data" which gets mirrored to specific storage as needed or weekly.

I've never found a way to backup Windows besides images.  There is daily-change data there, which is backed up using a Linux CIFS mount, but the OS and applications get an image. Also, I try to load apps using ninite-only - it is like having a package manager for Windows, but the available applications are limited.  For images, I use partimage, but clonezilla or ddrescue or fsarchive would be other usable options. This takes about 26GB of storage.

For some of the servers, even with 120 days of backups, we use** less than 26MB** (yes, that is correct) of storage.  It contains all the information to rebuild the server from a fresh install in about 30 minutes total time. Our RTO and RPO are 24 hrs, but I prefer to do better if it doesn't cost anymore money or effort.  Those terms are used by professional DR people (which was my prior job) - you can read about them on wikipedia.

---

### Post by mastablasta on 2014-07-28
> **TheFu said:**
> You described a bunch of things, but not some of the most important things - 
* how much daily-change data?


At the moment it's about 25-30 MB per day. Depends on the day and if we do any trips or not. Like i said it's a 5Mpixed digital camera at work and mostly 640x480 short movies it makes. if we used HD or tablet it would be much mor. it made over 1Gb for 10 minutes. but i guess i could just compress that with handbrake so it won't be as much.

well since arround 2010 we generated about 50 GB of data. lately we generate more, cause my wife is photographing the kids a lot. 

OS are backed up manually. they don't need additional backup IMO. i mean i have for win 7 factory reset backup, then i have the whole disk image... the windowx XP disk was starting to go bad so i backed it all up as well  and that disk actualyl still works. just has problem starting up. nothing much to backup there actually.

i don't know how much data the external backupers would have. they do have a higher res camera but don't make as many pictures.  there is also the HD camera with DVD recording. i thing they move those to another DVD and possible hard disk i am not sure. anyway those could add up. but again it is not used as much. 

things would change drastically if we bought an HD cam sometime later on...
data volume also tends to increase iwhen we go for holidays (logicly)

> 
* how much never-change data?


I am actually worried mostly about this "never-change" data such as familly videos, pictures.

the changing data would be possibly from webhost. even there at the best of times there was about  2 MB per week data uploaded and added. not much. pictures took the most space. i expect this to return in about 6 months.

> 
budget?


i was thinking 350-400 EUR incl. hard disks. -- up to 200 EUR for the box
to use as little energy as possible would be nice too.

> 
Your signature has Redobackup - why not select that? How is it deficient?


it's just a GUI frontend for partclone :
> Remember that Redo Backup is simply a front end, and that Partclone is the actual program doing the work

 it's designed for manual backup. you boot into live sesion and perform a backup by creating bit-by-bit disk image or backup up a folder. it's easy to use and is good if you need to backup disk before partitioning for example. Or to move the whole system to another computer etc.

---

### Post by TheFu on 2014-07-28
I don't feel like doing calculations.  Your data amounts seems negligible to me.  Buy 1x 4TB USB3 HDD, connect it up to an existing system and call the hardware done. No need to make this too complicated. It is for backups, not the primary storage after all.  All these files need to be retained on other storage devices.

I don't see the need to make image-based backups for any Linux. To me that seems like wasting 4G of backup storage and the time to make it during every backup session.

To me, photos/videos are not change-daily data.  They get modified once, then never again.  If you want greater protection for those never-modified data files, use parity tools to fight bit-rot.  I've had success with par2 enabling recovery from optical media when some of the data was corrupted.  I stopped using optical media a few years ago - 4TB HDDs are relatively cheap as backup media, though I do not trust them for primary media yet.  I haven't seen any bitrot on the backup disks, so do not use parity there.  rsync is my backup tool for this data.  2 copies - primary and the backup. That's it.  We're talking many TBs here.  I travel, vacation about 6 times yearly and [take lots of photos]("http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival").

So - I like **rdiff-backup** for linux backups of daily-change-data, as you know. I think I've converted over a few of the forum moderators too. Lots of reasons, mainly because for 30-60 days of backups, it requires just 10-20% storage than the original source. Plus it is highly efficient on time and network bandwidth and runs over ssh. The backup area doesn't make use of any proprietary data formats - gzip is it, so it is always YOUR DATA in the backup area. The main thing it lacks is encryption.  The target storage needs to be a Linux file system. THAT is important.  The most recent backup looks like an rsync mirror, which I love, love, love. It is only older versions of files where using the rdiff-backup script (it is python) for restores is easier.

The other alternative is duplicity, but it is still beta according to the developers.  I've played with duplicity and found it very frustrating. I don't think it is ready for production use.

Since you'll be living with this solution for a few months at least, only you can decide which is best.  

I've switched from ZIP, to tar.gz, to  rsync, to rbackup, to rsnapshot, to back-in-time, and finally to rdiff-backup over the last 20 yrs.  Been using rdiff-backup for about 5 yrs and don't have any plans to change. It just works ... er ... almost always. When it fails during a backup about once a year across 20 systems here, I know and can manually run the backup (1-4 minutes) again for that 1 machine.  2 times in 6 yrs, the backup area for a system became corrupted and refused to have another version added. I move the top level dir over and start with a fresh backup directory. That has always solve the issue.  I've seen commercial, high cost, backup tools report failures for almost every backup over years, so having a solution that only reports a failure when it is real it nice.

---

### Post by mastablasta on 2014-07-29
hmm but what about others that are not at my home? they would need to connect to my desktop PC when the PC is on and move the files then to external disk connected to the PC. at the same time I wouldn't be able to do much else since the PC I have are not really some modern machines. best CPU I have is a dual core Celeron (1.2GB ram, 50 GB disk for OS/apps/games & 750 Gb for data only) the other one is single core Athlon (4GB ram, now 1 Tb disk for OS & games/apps - haven't formatted the whole thing yet after moving to it from smaller disk and another 1TB disk for pictures, videos and various downloads - Linux images, program downloads...). if you do any copying on disk you can't do almost anything else while stuff is being copied. the netbook doesn't fare much better  in terms of speed or operational capability while copying the files. but then again that one doesn't have many stuff to backup.

 not to mention that if we bought a new camera (on wish list) the never-change data would increase quite a bit. HD videos take space as well as better pictures. I am not sure hwo much videos made by HD cam that reords to DVD would make. I think 30 minute video takes up about 2 GB.

 what we have at the moment is that we download the pictures to one PC, unplug the camera and then download them on the other.

edit: I wonder why tapes are so expencive (drives and cartridges..)?!

---

### Post by mastablasta on 2014-07-29
I've been reading the helpful articles from TheFu and looked some of the presentation. I think I am looking for this:
> For incremental data backups, I try to push all the data on Windows to a Linux file server and use Linux backup tools


in some way to put the data to server (the bonus would be that it is shared among other family members and access could be limited) and have it then copied to yet another disk inside the server. would that be a good idea? let's say they want to access or view my pictures they could then do it on server at the same time it would serve as backup. or is that a bad idea.

I am still no clear if it would be good to have server connected via Wi-Fi?!

---

### Post by mastablasta on 2014-08-06
OK so server over wi-fi might be a bad idea. I did however find that I can get encrypted internet connection via electrical wires relatively cheap. and no drilling involved. I could move it to storage room that way. and let it work there. 

so now the things I am looking at still are:
- is it a good idea to run server off a USB stick
- would I need a UPS? although electricity is rarely out. 
- what disks to use. I see guides suggesting to use standard Seagate disks while other suggest that they should be NAS disks for sure. I was thinking would a combination be good? one NAS (red) one normal blue disk. the normal disk would be server and keep data family members would drop on server while NAS would keep the backups form this data. since verisoned backups take a bit more space that would mean that 3TB backup disk should used for 2TB data disk, right?

---

### Post by TheFu on 2014-08-06
> **mastablasta said:**
> OK so server over wi-fi might be a bad idea. I did however find that I can get encrypted internet connection via electrical wires relatively cheap. and no drilling involved. I could move it to storage room that way. and let it work there. 

so now the things I am looking at still are:
- is it a good idea to run server off a USB stick
- would I need a UPS? although electricity is rarely out. 
- what disks to use. I see guides suggesting to use standard Seagate disks while other suggest that they should be NAS disks for sure. I was thinking would a combination be good? one NAS (red) one normal blue disk. the normal disk would be server and keep data family members would drop on server while NAS would keep the backups form this data. since verisoned backups take a bit more space that would mean that 3TB backup disk should used for 2TB data disk, right?

USB stick?  Not so much. CF is what I've seen.  The issues are performance and wear patterns and having it fail. I suppose if you were religious about having image backups and were ready when the flash fails, that could be fine.  OTOH, a key thing that servers do it log things. Logging writes to the file system - lots. That will cause many millions of write cycles that flash just isn't prepared to handle, IMHO.  I wouldn't.

UPS - YES!!!!   All my systems are on a UPS. Power flickers here about 3 times a year and we don't really have outages.  I don't put monitors or printers on a UPS.  All phone and network equipment is also UPS/battery, so those work if the power is out too.  Plus there are plenty of portable devices with a screen that can be used to ssh into my systems if necessary.

I've been burned by Seagate multiple times. Never plan to buy another disk from them the rest of my life.  You may not recall, but when 750G disks became popular and there was a huge data-loss issue with Seagate drives, their management lied repeatedly for over a year about it - I think that was around 2007 - I was running multiple storage arrays at home with Seagate drives ... which continued to work great for 7 yrs (they still work, if I hadn't pulled them out because I was afraid of failures).  Last year, Seagate had 2TB HDDs cheap - 40% less than the competition, so I bought a few.  These came with 1 yr warranties.  Just over a year later, 1 failed.  IME, HDDs either fail at the start of their lives or they work 5 yrs, then start having issues.  This has cemented my dislike of Seagate management.  "Fool me once ...."  Don't let the cheap prices trick you. There is a reason they are cheap.

The last HDDs I bought was a Hitachi, but I run Toshiba, WD as well.  There are a few "red" drives in an array here.  Think I'd rather have "black" ones for better performance.  The Hitachi's are primary media and the Toshibas are backup for media (for the most part).  For running an OS and for versioned backups, WD-black or Red are used. I avoid having important data on cheap green/blue HDDs. Our data is worth the $30 more for a better quality disk and to avoid the hassles cheap disks often have.  Look at the warranties - if a company refuses to warranty a HDD for 5 yrs, why trust your important data to it?  USB HDDs often only get 90days of warranty. Why is that?

Versioned backups aren't needed for everything - certainly not for most large media files.  Versioned backups for about 20 systems fit on this:
```
/dev/sde3             577G  480G   68G  88% /Backups
```
All are at least 30 days, many are 60, 90, 120 days of versioned backups.  Basically, 1.1x to 1.2x the original storage is needed - not 1.33x more.  I hope that makes sense.  Also - there are some old pre-OS upgrade backups in that /Backups/ storage, so 100G is used just because it is available.

Media files are stored elsewhere and backed up differently to avoid needing 20x the storage just because I rename a file or move it to a different directory over time.

---

### Post by mastablasta on 2014-08-07
> **TheFu said:**
> USB stick?  Not so much. CF is what I've seen.  The issues are performance and wear patterns and having it fail. I suppose if you were religious about having image backups and were ready when the flash fails, that could be fine.  OTOH, a key thing that servers do it log things. Logging writes to the file system - lots. That will cause many millions of write cycles that flash just isn't prepared to handle, IMHO.  I wouldn't.

Yeah I was thinking that logs could go to hard disk. and they are basically the major thing that gets writes and rewrites in server. the HP Microserver has a USB plug inside the box. I believe it is there just so one can run the OS from USB stick. 
> 
UPS - YES!!!!   All my systems are on a UPS. Power flickers here about 3 times a year and we don't really have outages.  I don't put monitors or printers on a UPS.  All phone and network equipment is also UPS/battery, so those work if the power is out too.  Plus there are plenty of portable devices with a screen that can be used to ssh into my systems if necessary.

Even with more static data? I am thinking this is a home server that probably won't have much frequency and users. and all that a cheaper UPS would do is turn it off safely (they last 8-10 minutes). so someone would have to go and boot it anyway. if electricity went out and there is no UPS data could potentially get corrupted but i am thinking they would be corrupted either only on main disk. or only on the backup disk if files were just being transferred to it when the power is cut.

in windows checkdisk would solve and fix this kind of issue. is there no Linux tool that would do the same on reboot?

the server would not be "critical". I mena if it's offline for a couple of days (let's say I went on holidays when the power went out) then it's offline.

> 
I've been burned by Seagate multiple times. Never plan to buy another disk from them the rest of my life.  You may not recall, but when 750G disks became popular and there was a huge data-loss issue with Seagate drives, their management lied repeatedly for over a year about it - I think that was around 2007 - I was running multiple storage arrays at home with Seagate drives ... which continued to work great for 7 yrs (they still work, if I hadn't pulled them out because I was afraid of failures).  Last year, Seagate had 2TB HDDs cheap - 40% less than the competition, so I bought a few.  These came with 1 yr warranties.  Just over a year later, 1 failed.  IME, HDDs either fail at the start of their lives or they work 5 yrs, then start having issues.  This has cemented my dislike of Seagate management.  "Fool me once ...."  Don't let the cheap prices trick you. There is a reason they are cheap.

The last HDDs I bought was a Hitachi, but I run Toshiba, WD as well.  There are a few "red" drives in an array here.  Think I'd rather have "black" ones for better performance.  The Hitachi's are primary media and the Toshibas are backup for media (for the most part).  For running an OS and for versioned backups, WD-black or Red are used. I avoid having important data on cheap green/blue HDDs. Our data is worth the $30 more for a better quality disk and to avoid the hassles cheap disks often have.  Look at the warranties - if a company refuses to warranty a HDD for 5 yrs, why trust your important data to it?  USB HDDs often only get 90days of warranty. Why is that?



Well we had similar issue with WD (green). burned. although before I always got WD. I think there are only two companies now anyway. WD and Seagate. the rest are OEM products. so not much choice here. I got a Seagate blue now for system disk. we will see how long it lasts. the one I bought had good reviews & performance tests online. Red ones are usually slower which is why I think they could serve as second disk for the backup.

> 
Versioned backups aren't needed for everything - certainly not for most large media files.  Versioned backups for about 20 systems fit on this:
```
/dev/sde3             577G  480G   68G  88% /Backups
```
All are at least 30 days, many are 60, 90, 120 days of versioned backups.  Basically, 1.1x to 1.2x the original storage is needed - not 1.33x more.  I hope that makes sense.  Also - there are some old pre-OS upgrade backups in that /Backups/ storage, so 100G is used just because it is available.

Media files are stored elsewhere and backed up differently to avoid needing 20x the storage just because I rename a file or move it to a different directory over time.

So basically I probably wouldn't even need versioned backup for media files. I could just get two disks of same size. one a more reliable backup red disk and the other one could eventually be blue disk.

then all I would need is partition for other backups (and server logs) which would be versions and the partition on second disk for these would need to be about 20% bigger. maybe a boit more to have some free space on partition. 

hmm would make sense if they had 1 TB and 1.5 TB drives. but usually they just have full numbers these days. so if one drive is 1 TB the other one has to be bigger and can only be 2 TB drive then.

---

### Post by TheFu on 2014-08-07
You don't have to use the entire drive space on the main disk(s).
Don't forget to refresh the bits on the HDD occasionally to avoid bit rot. I've seen it happen after a few years and started using par2 to address it. You might want to research snapRAID too.

For me the data backups that need to be versioned are only 20G or less per system. For many servers, it is under 1G (these are not file servers, of course).  The backup areas really aren't that much to worry over.

---

### Post by mastablasta on 2014-08-08
i am researching snapRaid. looks interesting option from what i read.

in the mean time i figured otu it might not be possible to use TP-Link TL-PA4010KIT or similar electric adapters well. while i have a free socket in living room the storage room has only one electric socket and that one should be  used for server as well. any ideas if these things work with other stuff plugged in?  imean manual says no an dit porbably does create some interference. so the only solutions would then be the unsafe wi-fi :(

---

### Post by TheFu on 2014-08-11
Some other options for media storage [http://zornsoftware.codenature.info/blog/why-i-ditched-raid-and-greyhole-for-mhddfs.html](http://zornsoftware.codenature.info/blog/why-i-ditched-raid-and-greyhole-for-mhddfs.html)

---

### Post by mastablasta on 2014-08-11
oh yes. sounds interesting.

I also found a nice interface for webserver I need to try out: [http://ajenti.org/](http://ajenti.org/)
but that's later to be decided.

I am also checking more hardware. I wonder why they do not have many fanless servers available? I mean those that are available are either single drive servers or some with powerful CPU which I probably do not need.

checking the ITX boards - you basically don't get any better setup or cheaper if you buy board and put the server together. most small boards that could possibly be used in fanless design do not have enough SATA plugs. strange. if fanless I could keep it in living room solving my issue with connection. as it seems now either keep fan based server in living room and have wired internet (via switch or router) or put it in the storage room and then have wireless connection (not so reliable and much less secure).

I am thinking for start 2 disks will be enough. one disk will have 2 partitions - one smaller (up o max 30 GB) for versioned backups of webserver and similar files that change a bit more often. the other one for data files that don't change (media files). these are just copies of original files kept on desktops. the copies would be accessible by others with access to server and in such way this data is shared). the second disk would just represent a mirror of this backup disk. either with copying or some nightly sync or that snapraid. when the disk get's filled the second disk would be installed with same principle. it should be a while before we fill two disks like that I think). the disks would be from different manufacturers in case any one has serial issue. I don't know how much data other family members have exactly at the moment. i am sure they do not have as much as we do. since we make most photos and videos I believe. so a 2 TB disk should be OK for next 3 or 4 years and then we can add another one... by that time server hardware will need to be changed anyway (8-10 years is the living time, right?). if space get's increased a lot, then older data that is not accessed often could be moved to external USB 2.0 drives. while the newish stuff get's internal sata drive.

---

### Post by TheFu on 2014-08-11
When looking for hardware, I start here: [http://www.pricewatch.com/motherboard_combos_with_memory/](http://www.pricewatch.com/motherboard_combos_with_memory/) and start watching slickdeals and bensbargains for deals.  I have a fanless XBMC box, silent, APU-based - $150 from a few yrs ago. Don't think anyone can build something similar for that price anymore. The build is on my blog somewhere, if interested. Recently put 14.04 on that box - all is well.

Be certain that you transcode the videos.  My camera creates MOV 720p movies and if they are transcoded through **handbrake** on the high-profile, the resulting mkv/mp4 file is 70% smaller without any perceived change in quality. That is worth it.  It is also possible to compress most of the images 75% without seeing any loss in screen viewing ... but I don't do this. Only have 100G of images here.

I'm handling replication with **rsync** - manually. Of course there are scripts, but they must be run manually. Not at the point where I trust myself to automate this or any storage too to handle the replication.  

Looks like HDDs don't have enough competition. Just checked the prices and they've gone up. Too much corporate consolidation.

---

### Post by mastablasta on 2014-08-12
You can buy this stuff so cheap in USA. I am not sure what is wrong here with most of EU. do they add extra taxes or what?

I know they have a nice,small fanless media box for 140 EUR. but these are all small boxes for single disk. where are builds that can accept 4 disks? I checked sinology NAS and they have a weak CPU, very low RAM and they have a fan. energy consumption Is not all that impressive considering the weak CPU.

edit: found the link: [http://openelec.tv/forum/41-supported-hardware/67662-review-cheap-celeron-1037u-mini-pc-in-1037ua](http://openelec.tv/forum/41-supported-hardware/67662-review-cheap-celeron-1037u-mini-pc-in-1037ua)

and they do not have many boxes with these Celerons. I am not sure why. they have good energy consumption descent GPU...

---

