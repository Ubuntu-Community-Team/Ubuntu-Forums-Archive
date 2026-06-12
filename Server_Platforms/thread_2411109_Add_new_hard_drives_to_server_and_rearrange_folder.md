---
title: "Add new hard drives to server and rearrange folders"
date: 2019-01-24
forum: Server Platforms
---

### Post by seifer2k on 2019-01-24
Long story short, I built a server using Xeon E5450 (LGA771) on a MicroATX LGA775 motherboard.  Works flawlessly.  I chose Ubuntu Server because I don't have $1,000 to get Windows Server 2016, nor do I want the massive overhead of the GUI from that.  The server was built with 2 jobs:

1. FILE SERVER
2. PLEX MEDIA SERVER

Both are running fine.  I used SAMBA and LOTS of Google searching, as I've NEVER used linux before.  The Hard Drives are set up:

1.  500GB Seagate Barracuda = /dev/sda2
2.  3.0TB Western Digital GREEN = /dev/sdb1

I'll assume, for the moment, that sdA refers to the first HDD and sdB refers to the second HDD, and that it follows that sda1 and sda2 are references to individual partitions on the drive, as I can find NO reference to anything sdb2 or later.  Please correct me if I am mistaken on any of these details.

I mounted the 3TB hard drive as /data and inside it has folders:

DATA
-MEDIA  #SAMBA share folder so I can add media to PLEX server, subdivided by originating storage, then by show or line item.
--MOVIE
---Bluray
---DVD
--MUSIC
--TV
-SHARE  #SAMBA user share folders for individual use
--USER1
--USER2

What I'm looking to do is to ADD a new 4TB Western Digital RED hard drive and then restructure the file system so that

3TB WDgreen = /data/SHARE
4TB WDred = /data/MEDIA

In preparation for this, I'm putting together a procedure, step by step, so I don't forget anything.  I'm also picking your brains to make sure I CAN do something simple and that I'm not making any false assumptions before I attempt this.

1.  Shut down server.
2.  Install 4TB drive.
3.  Restart server.
4.  Stop SAMBA service.
5.  Stop PLEX service.
6.  UNMOUNT 3TB drive.
7.  Create /data folder.
8.  MOUNT 3TB drive as /data/SHARE.

At this point, I'm assuming that the mount point exists as the top of the file structure so /data was a pointer to the root of the 3TB drive, showing two folders:  MEDIA and SHARE.  Having changed that so that /data is now a folder in the original file structure and /data/SHARE is now the pointer to the 3TB, it would show /data/share/share and /data/share/media.  If I am correct, I will proceed.

9.  MOUNT 4TB drive as /data/MEDIA
10.  MOVE contents of /data/share/media to /data/media.

I need a fully-recursive command-line that will take EVERYTHING in the /data/share/MEDIA folder and move it to /data/MEDIA so that it will move all of the folders and data OFF of the 3TB and onto the 4TB.  Otherwise, moving everything one file at a time via command-line is going to take A LONG TIME.  I have 389 movies, 28 TV shows, 173 Music artists, etc.  Roughly 2TB of data needs to be transferred this way.

11.  MOVE contents of /data/share/share to /data/share.

This way I don't have nested redundant folders.  ALSO, this returns all of the data and folders to the original folder structure, allowing me to simply...

12.  Start SAMBA service.  (without having to make any changes to the config file at all).
13.  Start PLEX service.

PLEASE tell me if I'm making any wild assumptions and whether this is doable.  Please keep in mind that with Ubuntu Server, I HAVE NO GUI and I can ONLY USE COMMAND LINE (I swear, some people forget this and tell me to point and click).  If you need any more information, I'd be happy to provide it.

---

### Post by oldfred on 2019-01-24
Your large drives must be gpt partitioned.
Are you using ext4 for format. If so you need to give yourself ownership & permissions.

You can use cp -a to maintain settings or rsync with multiple parameters.
I use multiple flash drives for backup and just use rsync to copy many folders to same location on flash drive.
I also use rsync to copy data back to my other system.

Each of my flash drives has a file with a script/bash to copy data. These are just a few of the lines to copy to my 128GB flash drive.
Add the n parameter to make it in test mode to see if you get errors.
```
rsync -aruvP --delete /mnt/data/Notebooks  /media/fred/data128
rsync -aruvP --delete /mnt/data/OfficeFiles  /media/fred/data128
rsync -aruvP --delete /mnt/data/Projects  /media/fred/data128

```

Some of my scripts I have updated to make sure I am using sudo, to make sure I have the mount point, and other error messages.
For details on parameters I am using see the man page, but there are many parameters.
man rsync

---

### Post by TheFu on 2019-01-24
Xeon is overkill for what you are doing.  Way, way, way, overkill, unless you have lots of 4K content and need to transcode it down for other devices.  People run a Plex Server on a Raspberry Pi v2.  Plex doesn't need much RAM either.

No need for samba, unless you want to use it for some Windows clients, perhaps to drop files over into plex's libraries.  Plex doesn't use it to stream content.

If you want to move a directory, just move the directory. mv is the command. That will take everything that is a child object of that directory with it.  BTW, best to use a native Linux file system for all these disks - reasons.  A mv within the same file system is instantaneous.  Across file systems requires the time to copy everything over and delete the original.  If anything bad happens during a large mv, it can be messy.  People often choose to use rsync to perform recursive copies that will run for a long time.  rsync is efficient if it needs to be restarted for any reason. It really shines for network transfers.  Not so much for local disk-to-disk transfers due to some assumptions which make sense for small files, but do not make sense for large media files.  I always have to check the rsync manpage to figure out the options to make local sync fast.  rsync is one of the most amazing commands on any Unix system.

If you have something already mounted to /data, then that directory already exists.  A "mount point" is just an empty directory. Actually, it doesn't strictly _need_ to be empty, but any contents would be hidden after a partition is mounted over it.  So you only need to create the new subdirs under /data for any new mounts you want.  **mkdir /data/SHARE /data/MEDIA**  Then modify the /etc/fstab to mount the partitions to those directories.  This assumes you've already partitioned and made the file system desired.  I'd use ext4, unless there was some specific reason to use other.

You'll need to tell plex that the specific media locations - TV, Movies, Music, Photos, are in different places. Not a big deal, use the web interface for that.  As the collection gets larger, there are some plex settings that I turn off to reduce the storage wasted.  When the library metadata eats 100G, all sorts of things start slowing down.

Stopping and starting services is trivial. The preferred method has changed over the last few years and I must have missed where you said which release was being used.  I generally still use **sudo service plexmediaserver stop** type of commands.

BTW, there are lots of reasons NOT to run Windows servers - performance is the main reason. [https://www.phoronix.com/scan.php?page=article&item=jan2019-win-server&num=1](https://www.phoronix.com/scan.php?page=article&item=jan2019-win-server&num=1) 
Easy of management is the other.  Unix systems can trivially be managed en-mass with F/LOSS tools.  2 or 2,000, doesn't make all that much difference.  

The learning curve for Unix admin is steep, but it seems you are doing fine. 

I can't really help much with Samba.  Barely use it here.  I prefer NFS, but most of our network is Unix systems and NFS is th best way for storage to be shared on a network, assuming you don't need much security.

---

### Post by mastablasta on 2019-01-25
> **seifer2k said:**
>  Please keep in mind that with Ubuntu Server, I HAVE NO GUI and I can ONLY USE COMMAND LINE (I swear, some people forget this and tell me to point and click).  If you need any more information, I'd be happy to provide it.

well midnight commander works in CLI... :p

---

### Post by darkod on 2019-01-27
I dont know how far you got but what you are trying to do is not done like that. You should use this storage extension and pass to LVM (in fact you should have had lvm from the start).
Add the new 4TB disk as physical volume for lvm. Create the vg and lv, for example /dev/vg/data.
Then mount it on temp mount point, move all data from current /data and thats it.
Once done with that and mounted /dev/vg/data as /data, you can format sdb1 and add it to the lvm too. That will give you one big 7TB vg and you dont have to calculate whether share or media will be bigger or smaller.

---

### Post by TheFu on 2019-01-27
If the OP uses LVM to concatenate or stripe 2 disks, please ensure that a 100% backup that you can restore exists, before and after setting this up.

darknod, I've shied away from suggesting LVM concatenated LVs since most people don't seem to backup their data. Data recovery of LVM LVs after 1 disk fails is not intuitively obvious. I love LVM and use it all the time. It brings fantastic flexibility to storage management, for the price of a little more complexity. LVM is a great tool, if you have your backups already handled.  Otherwise, caution is suggested.

With LVM, the OP could put both disks into a single VG, but still keep separate LVs for data and share, but only allocate sufficient storage to the LV, as needed.  Leave the extra storage inside the VG, but unallocated.  Then, as needed, quickly adding 200G to either LV, as needed is a 10 second thing. Effectively instantaneous, while the file system is live.  LVM flexibility.  With a little effort, is it almost as easy to reduce an LV size, but only with ext4 as the file system.

And there is another option instead of LVM + ext4, use ZFS.  ZFS for data storage merges all the LVM does with a file system and has a more simple interface.  ZFS on 64-bit Linux has been pretty good for 10 yrs now, but only for data, not for boot or the OS.

And there are other options, but those become more experimental and less solid, IMHO.  Many people swear by them, but my data is more important than pretty much anything else on the computer.  I'm unwilling to risk it with a less-than-great file system or with extra layers that appear to merge file systems, but don't.

---

### Post by seifer2k on 2019-01-29
Ok, let me try to respond to as many people as I can with a few simple answers.

Yes, I used EXT4 file system on that 3TB drive before I used it.  I wanted to use whatever the native file system was for Ubuntu and that's what the 500GB primary hard drive was formatted as for the OS install.  In fact, it took me a while to figure out how to delete the existing NTFS file system in order to change it in the first place, so that was an adventure.

People claiming I went overkill with a Xeon... it's 2008 Xeon E5450 quad-core 3.0-GHz processor with NO hyper-threading, so 4-cores/4-threads. It's effectively a Core 2 Quad Q9650, just in a different CPU package (LGA771 instead of LGA775) and with ECC support enabled (which I don't use).  It also runs cooler (80-watt TDP vs the Q9650's 93-watt TDP).  I also started ripping all of my media to my Skylake-based gaming rig originally so everything was encoded in m4v containers with h.264 encoding.  Sure, it will transcode quickly, but I had no idea of that at first.  I have 3 smart TVs, my Playstation 3, and a couple of PCs around the house, so I wanted something that would be able to handle at least two simultaneous transcodes at the same time, if necessary.  And I had no idea what format or container it needed to direct-stream to those TVs.  I have since learned that it can direct-stream just about any h.264 video to the TVs without having to transcode, so that's a good thing.

I also built the server as my home file server.  The 3TB WD Green came out of a 3TB MyCloud USB3.0 enclosure that used to be hooked up to my router.  The router itself used SAMBA, so that was a good place to start for file sharing, as I didn't have to learn anything new for the Windows computers in the house.  And my parents are in their 60s, so learning new technology is like drilling teeth.  It's better to just not, if you know what I mean.  Anyway, that MyCloud thing has a USB-to-SATA adapter that was starting to FAIL to properly spin up the hard drive, so I couldn't get data off of it anymore in a reliable manner, but putting it inside an actual computer system gave it PROPER power and it spins up 100%, no issues.  That's why I re-purposed it.

The problem is... I've already filled the drive up over 2TB...so having almost 75% fill rate makes me nervous, about either using the file server itself to add more files or by adding new media to the PLEX server, hence my desire to obtain a new drive (4TB).  Also, my heavy use of the PLEX server lately makes me want to move all of the media to a WD RED (NAS) hard drive.

The REASON I haven't explored stuff like LVM (which I had never heard of until mentioned in this thread, by the way) is because I was attempting to keep the running software on the server to a minimum.  It only have 2 sticks of 2GB DDR2-800 memory and a 4-core/4-thread processor @ 3.0 GHz.  The less running, the better as far as I'm concerned.  Also, it would add complexity to the system that I am still currently (what I would consider...) very unfamiliar with.  The good news is that when I log on, I am presented with:
[ATTACH=CONFIG]282351[/ATTACH]

Running df:
[ATTACH=CONFIG]282352[/ATTACH]

And this is my cheat sheet file I created so far:
[ATTACH=CONFIG]282353[/ATTACH]

What I understand is the Windows OS and ecosystem.  I understand hard drives, the file system, the registry, networking, just about everything you'd want to do with Windows, I can do it.  (insert Microsoft Certified Windows 7 System Administrator certificate here)

For Linux?  My only experience with Linux was Ubuntu back in 2007.  I experimented with it for about a week and found that while I could surf the internet perfectly fine, about 75% of my games wouldn't run without installing program after program to EMULATE Windows, so I just went back to Windows XP.  Hell, I'm better working in Mac OS X than I am with Linux, and even in THAT I'm still hopelessly clueless.  Thank God my Google-fu is strong.

Which leads me... here.

So... it sounds like LVM is NOT what I want to do, because I want to make sure that ALL of my media for the PLEX server IS ON THAT 4TB drive I install, not floating around somewhere that I cannot pinpoint, or stripped between volumes.  I have no intention of running a RAID here.  I want to PHYSICALLY SEPARATE the media files from the share drive files by doing this.

Thanks for the help so far, though guys.  It helps me learn what the system is doing behind the screen and helps me understand what kind of options I have to look at.  So please keep the suggestions coming.

EDIT:  Oh yeah, someone asked about permissions on the drives.  The quick documentation I was able to find when I was first attempting to format and mount the 3TB drive had me do a chmod 777 command.  Looking at the attributes, the /data folder appears to have FULL read/write permissions for ANYONE with access to the server.   Since there's nothing on that drive other than share folders and media data, that wasn't a huge concern for me, but I know it's not best practice.  But isn't it a little late to be able to fix that?

On the SAMBA shares, the SAMBA accounts limit any user EXCEPT ME from accessing any folder other than the one that was shared to that user directly.  If my father logs in with his account credentials (saved to his Windows computer already), ALL he gets to see is his share folder.  He's not allowed anywhere else.  MY account, however, has been giving total access in case I need to fix something, transfer a file myself, or even to access the /data/MEDIA folder so I can drop in new content that I finished encoding (like, I've bought the 1st season of The Orville and already posted it to the server between the OP and this reply, so yeah, it works really well this way).

---

### Post by seifer2k on 2019-01-29
So new pictures for the chmod stuff, here's the result of two "ls -l" commands.  First was "ls -l /data" and the second was "ls -l /".

[ATTACH=CONFIG]282354[/ATTACH][ATTACH=CONFIG]282355[/ATTACH]

Did I cover everything?

---

### Post by oldfred on 2019-01-29
For terminal commands, just copy & paste to forum.
If longer use code tags, which are easy to add with forum's advanced editor and # icon. 
I use quote icon in Quick replay and change from quote to code many times.

For ownership & permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
I do this on my data partition. I used to think I was making it the same as /home default, but /home default is 644 and I am changing to 664.
Also I use -R or recursion which can be dangerous. Only run on your data, never on a system folder.
       sudo chmod -R a+rwX,o-w /data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /data

I have my data partition folders linked into /home. And I sometimes use sudo when I should not or something that makes root owner or permissions not what I want. So then I rerun the above commands to make all my data consistent.

---

### Post by TheFu on 2019-01-29
> **seifer2k said:**
> Ok, let me try to respond to as many people as I can with a few simple answers.
Good plan. Thanks.

> **seifer2k said:**
> 
Yes, I used EXT4 file system on that 3TB drive before I used it.  I wanted to use whatever the native file system was for Ubuntu and that's what the 500GB primary hard drive was formatted as for the OS install.  In fact, it took me a while to figure out how to delete the existing NTFS file system in order to change it in the first place, so that was an adventure.
ext4 is a good choice lacking any other information. There are at least 20 other "native Linux" file systems, each for a specific purpose.  For example, if you use SSDs, might want to use F2FS.  If you are interested in file systems, they ARE very cool, xfs, f2fs, zfs are each good for specific purposes that many people have.

> **seifer2k said:**
> 
People claiming I went overkill with a Xeon... it's 2008 Xeon E5450 quad-core 3.0-GHz processor with NO hyper-threading, so 4-cores/4-threads. It's effectively a Core 2 Quad Q9650, just in a different CPU package (LGA771 instead of LGA775) and with ECC support enabled (which I don't use).  It also runs cooler (80-watt TDP vs the Q9650's 93-watt TDP).  I also started ripping all of my media to my Skylake-based gaming rig originally so everything was encoded in m4v containers with h.264 encoding.  Sure, it will transcode quickly, but I had no idea of that at first.  I have 3 smart TVs, my Playstation 3, and a couple of PCs around the house, so I wanted something that would be able to handle at least two simultaneous transcodes at the same time, if necessary.  And I had no idea what format or container it needed to direct-stream to those TVs.  I have since learned that it can direct-stream just about any h.264 video to the TVs without having to transcode, so that's a good thing.
Ah ... sorry for assuming Xeon meant "new Xeon".  I've been retiring all my 2010-ish systems recently.  h.264 is well supported by almost all streaming devices. h.265 is starting to show up, especially with 4k content where the added size reduction matters even more.  In the USA, ATSCv3 for broadcast and likely CATV will be switching to h.265 encoding.  The timeframe for that change with broadcast TV was 2021, but as with all govt standards, that is slipping, which is good for people who have ATSCv1 tuners (MPEG2 encoding).

I use raspberry pi v2 and v3 for TV/Kodi playback devices.  My plex server is a 5 yr old Pentium and will transcode 1 hidef stream to something else. My default video storage format, h.264, doesn't require any transcoding, unless I'm away from home and using plex over a VPN and want to use less bandwidth.  Raspberry Pi devices have hardware support for h.264 video and with a $2 paid license, mpeg2 HW support (live TV).

It is kinda amazing the different ways that people solve problems based on their experiences.  I chose cheap + F/LOSS. There is no one, right, answer.

> **seifer2k said:**
> 
I also built the server as my home file server.  The 3TB WD Green came out of a 3TB MyCloud USB3.0 enclosure that used to be hooked up to my router.  The router itself used SAMBA, so that was a good place to start for file sharing, as I didn't have to learn anything new for the Windows computers in the house.  And my parents are in their 60s, so learning new technology is like drilling teeth.  It's better to just not, if you know what I mean.  Anyway, that MyCloud thing has a USB-to-SATA adapter that was starting to FAIL to properly spin up the hard drive, so I couldn't get data off of it anymore in a reliable manner, but putting it inside an actual computer system gave it PROPER power and it spins up 100%, no issues.  That's why I re-purposed it.
Opinion:
Connecting storage to any internet router and trusting them to be secure is a bad idea. Those devices are constantly having issues, even with just the routing parts.  Sure, the storage will work, but then there is all the other people, services and bugs which let hackers with almost no real skills gain access to the storage too. It is easy, via google, to find how to hack pretty much any router that hasn't been patched this month.  Average people don't have much hope of being secure using commercial, home, routers.

> **seifer2k said:**
> The problem is... I've already filled the drive up over 2TB...so having almost 75% fill rate makes me nervous, about either using the file server itself to add more files or by adding new media to the PLEX server, hence my desire to obtain a new drive (4TB).  Also, my heavy use of the PLEX server lately makes me want to move all of the media to a WD RED (NAS) hard drive.
I've had a few Red WD drives fail.  I haven't seen any better results compared to other HDDs.  The only viable difference seems to be based on the provided warranty.  If you look at the backblaze reports for disk failures over the years, there is something about 3TB disks which cause every vendor to have reliability issues.  I don't have anything against WD - it is more about the 3TB size which I think requires extra caution, extra backups, and planning for failure.

Being in their 60s doesn't relate to computing skills at all. It is just what their vocation was. ;)

> **seifer2k said:**
> The REASON I haven't explored stuff like LVM (which I had never heard of until mentioned in this thread, by the way) is because I was attempting to keep the running software on the server to a minimum.  It only have 2 sticks of 2GB DDR2-800 memory and a 4-core/4-thread processor @ 3.0 GHz.  The less running, the better as far as I'm concerned.  Also, it would add complexity to the system that I am still currently (what I would consider...) very unfamiliar with.  The good news is that when I log on, I am presented with:

LVM isn't for everyone.  2G is more than enough RAM for a file server or plex server running Linux, assuming no GUI.  But 2G does mean that using ZFS wouldn't be recommended.

posting images isn't necessary here. Please copy/paste the text and wrap them in code tags.  Text is 1,000 smaller than an image.

Your "server commands" is where we all start.  In 18.04, the use of "service" is deprecated for **systemctl**.
df output that isn't for real partitions is just funk to get in the way.  The loop devices are useless unless you are working a snap-specific issue.
**df -hT |egrep -v 'loop|tmpfs' **is more useful.
I like the -h (human readable) option on many commands.  df, du, sort all have the -h option.

> **seifer2k said:**
> 
[ATTACH=CONFIG]282351[/ATTACH]

Running df:
[ATTACH=CONFIG]282352[/ATTACH]

And this is my cheat sheet file I created so far:
[ATTACH=CONFIG]282353[/ATTACH]

You can find 1-page _Linux Command summary PDF_ files easily.  90% of the commands are shared with Unix and haven't changed much the last 25+ yrs.  Admin commands do change from time to time.  Some are really stable and consistent for 20+ yrs, but others seem to change every 2-4 yrs when a team decides to "fix" problems that 3% of users have.  systemd (systemctl) is one of those.  resolvconf is another. That's more opinion. Sometimes progress is really progress too.

> **seifer2k said:**
> 
What I understand is the Windows OS and ecosystem.  I understand hard drives, the file system, the registry, networking, just about everything you'd want to do with Windows, I can do it.  (insert Microsoft Certified Windows 7 System Administrator certificate here)
Many things seem to be similar between Windows and Linux, even when they are not.  It is a liability, often.

> **seifer2k said:**
> For Linux?  My only experience with Linux was Ubuntu back in 2007.  I experimented with it for about a week and found that while I could surf the internet perfectly fine, about 75% of my games wouldn't run without installing program after program to EMULATE Windows, so I just went back to Windows XP.  Hell, I'm better working in Mac OS X than I am with Linux, and even in THAT I'm still hopelessly clueless.  Thank God my Google-fu is strong.
Be careful using google to find too many answers.  At the early stage of learning, it is easy to find bad advice from sites written by non-experts.  In the beginning it is best to get a book and work though it, in order, because 1 skill builds on another. Jumping into being an admin adds to the necessary background.

> **seifer2k said:**
> Which leads me... here.

Good place, especially for discussions where you can see multiple different opinions.

> **seifer2k said:**
> 
So... it sounds like LVM is NOT what I want to do, because I want to make sure that ALL of my media for the PLEX server IS ON THAT 4TB drive I install, not floating around somewhere that I cannot pinpoint, or stripped between volumes.  I have no intention of running a RAID here.  I want to PHYSICALLY SEPARATE the media files from the share drive files by doing this.

There are good reasons to use LVM even if you don't want to ever cross different HDDs. It does add complexity and for someone relatively new, the added complexity is best avoided.

> **seifer2k said:**
> Thanks for the help so far, though guys.  It helps me learn what the system is doing behind the screen and helps me understand what kind of options I have to look at.  So please keep the suggestions coming.

Bingo. Exactly why we are here.  I'm less about the exact command to run and more about the "why" and bigger picture choices.

> **seifer2k said:**
> EDIT:  Oh yeah, someone asked about permissions on the drives.  The quick documentation I was able to find when I was first attempting to format and mount the 3TB drive had me do a chmod 777 command.  Looking at the attributes, the /data folder appears to have FULL read/write permissions for ANYONE with access to the server.   Since there's nothing on that drive other than share folders and media data, that wasn't a huge concern for me, but I know it's not best practice.  But isn't it a little late to be able to fix that?

chmod 777 is for either people who don't understand permissions or is just really lazy and doesn't care about security.
You can always fix permissions for Linux file systems.  NTFS and FAT-whatever permissions are set at mount-time, but on Linux file systems, permissions can be modified at any time. I'd write a little script, but basically, it would be a **chmod -R o-w /data**   if you want to allow plex to control the files (with deletion possible, then I'd add my userid to the plex group, change the group for everything to be 'plex' and set the groupid bit on all directories.  Unix permissions are very elegant. Every popular OS uses the Unix permissions model, except 1.  Learning it to an intermediate level is not a waste of time.  

Permissions are critical to Unix backups too. The data is only 50%, but without the owner, group and access permissions, you can't get back to a working system.  Unrelated, but you can safely ignore all use of the tar command that you see for backups. Nobody, anywhere, should be using tar for backups today or in the last 20 yrs.  They really need to stop teaching it for that purpose.  Tar is like zip. Good for small needs to move stuff around. It was designed when 50MB was huge.  Attempting to use tar for 1G and larger is ill-advised for many, many, reasons.  There are just better choices the last 20 yrs.

When you go to learn the permissions, create some directories and files under /tmp/ and go crazy where you can't harm the system.  Use 3 userids, 2 groups and at least 2-3 levels of subdirectories.  Try out every different possible combination of 32-bit permissions. See what access is restricted and what isn't.  Check out 711 (octal) permissions on a directory, very useful, sometimes.  Octal is commonly used for permissions because it is usually quicker than using the longer constructs, but not always.

> **seifer2k said:**
>  On the SAMBA shares, the SAMBA accounts limit any user EXCEPT ME from accessing any folder other than the one that was shared to that user directly.  If my father logs in with his account credentials (saved to his Windows computer already), ALL he gets to see is his share folder.  He's not allowed anywhere else.  MY account, however, has been giving total access in case I need to fix something, transfer a file myself, or even to access the /data/MEDIA folder so I can drop in new content that I finished encoding (like, I've bought the 1st season of The Orville and already posted it to the server between the OP and this reply, so yeah, it works really well this way).

I can't tell if you have an issue with samba or not.  I use NFS, not Samba, almost always.

---

### Post by TheFu on 2019-01-29
I see that oldfred provided a chmod command too.

There are different ways of looking at chmod.
* what permissions do I want to set EXACTLY.
* what permissions do I want to ADD.
* what permissions do I want to REMOVE.

If all the files and directories have 777 permissions, then the shortest command to remove write to anyone outside the group, while keeping read access would be to remove write for the "others" , hence, chmod -R o-w /data   ---> 775 permissions would result.  Not ideal for data files like videos, music, photos which don't need eXecute permissions, but it is a quick and easy chmod command.

If you used samba to copy over files, then samba permissions as configured for the share in the smb.conf file would control the permissions.  Samba doesn't follow the Unix rules and Windows doesn't care.  It is a complexity.

---

### Post by seifer2k on 2019-01-29
Thank you for the replies.

As to posting pictures instead of text, I've never met a single forum on-line that let me use pre-set TAB stops (like I was typing in Microsoft Word), so spacing out columns of data never works.  That's why I just took a quick screenshot with JPG file format to keep the file sizes down.  I used the Snipping Tool in Windows to limit the picture to only the terminal window.  I have 1440p and 1080p displays and that's a lot of useless picture.

If you're going to try to teach me to use permission commands like CHMOD, it would be nice if someone broke down the SYNTAX for me instead of giving me specific commands for a specific example.
Let's see....  I see "drwxrwxrwx" as a list of assignable permissions.  From what I can tell just by looking at it, R is read, W is Write, and X is Execute, as in to run programs from that location.  Since the SHARE and DATA folders do not contain ANY kind of executables and I certainly don't want anyone trying to run any kind of program from the Share Drive's location, I will assume that X should be blanked out with hyphens, like this:  "drw-rw-rw-".  I've also noticed the repeating pattern of three groups of "rwx".  This tells me they are for different access levels.  I assume Administrator, group, user, but honestly I have no real idea.  But I understand the command "CHMOD 777" means, from 0 being --- to 7 being RWX, as an octal code of three bits that assign permissions to a folder or file, that that's what it's doing:
0 - 000 (---)
1 - 001 (--x)
2 - 010 (-w-)
3 - 011 (-wx)
4 - 100 (r--)
5 - 101 (r-x)
6 - 110 (rw-)
7 - 111 (rwx)
and that the three digits represent each access group level in the permissions list: so say I did CHMOD 745, it would do "d(rwx)(r--)(r-x)" respectively.  So I understand this much.  It's the three groups I don't know about, hence my wish to not want to mess with this command too much.

Concerning SUDO... So, like, I get that putting SUDO in front of a command is to access administrator-level privileges in doing the command.  I would love to stay away from that as much as possible, but most commands I've found on-line so far always include it, so I had figured there was good reason to include it.

For example, trying to NANO a file like /etc/samba/smb.conf will give me errors trying to save changes to the document unless I do it with SUDO.  I assume the file is write-locked behind admin permissions to keep other programs from making changes to the file.  I like that, but it's something I have to remember to work around.

I am having ZERO issues with SAMBA.  I got it set up the way I needed to and it appears to work flawlessly.  All three users have full access to their folders and all their data is present.

---

### Post by oldfred on 2019-01-29
The link in Post #9 has lots of explanation of permissions.

re sudo:
       [URL="http://xkcd.com/149/"]http://xkcd.com/149/


[/URL]

---

### Post by seifer2k on 2019-01-29
Ok, so I had a look at the link in post #9.  Lots of useful info that tracks with what I "assumed" (a.k.a. logically deduced) about the command.  Yet there's still a few questions I have.

drwxr-xr-x  2 root root  4096 Jan 12 06:44 bin
drwxr-xr-x  3 root root  4096 Jan 12 06:44 boot
drwxrwxrwx  5 root root  4096 Dec 8 01:13 data
>  drwxrwxr-x  5 heath heath  4096 Dec 8 01:13 media
>  drwxrwxr-x  5 heath heath  4096 Dec 8 01:12 share
-rw-r--r--  1 root root    42 Dec 7 22:33 deb

Not sure what the 2/3/5 is in the list here.  I even see the /etc folder with a 94, and the /lib folder with a 21.

I know that /data was created AFTER the system was installed and running, yet the DTG on the listing above shows a later date for /bin and /boot.  So what's the deal with the DTG?  It can't really show the last time the folder was changed, because I've been adding media almost daily for over 3 months, yet the date on /data/media still shows December 8th.  I dropped files on it only 4 days ago.

Where it says "root root" or "heath heath" (because my given name is Heath and that's my account name), which one's the USER account and which one's the GROUP?   And why does the folder have a group anyway?  I get from the listing that each directory and/or file has an assigned OWNER (user account) and an assigned GROUP.  The Owner of the file/folder is pretty self-explanatory.  But can't multiple different groups have different permission levels to any one folder/file?  We do that in Windows.

Also, what the h*ll does "OTHER" mean for permissions?

Very good that I read that FOLDERS need EXECUTE permissions or they disappear from the file system.  I'll be very careful about that.

---

### Post by TheFu on 2019-01-29
So, we don't usually explain permissions much in the forums because it comes up ALL-THE-TIME. Saying the same thing over and over is a waste.  Plus, it is easy to miss/forget important items.  We get busy, sidetracked. Hence the link to the Ubuntu Help page with a full, careful, explanation about permissions.

We use "code tags" to paste pre-formatted text here.  It works perfect for output from **ls -aFl**.  Here's a few from my Plex TV/ directory:
```
drwxrwsr-x   2 thefu plex  4096 Oct 22  2015 Traveler/
drwxrwsr-x   2 thefu plex  4096 Apr 13  2017 Victoria/
drwxrwsr-x   3 thefu plex  4096 Oct 18  2016 Westworld/
```
See how nice that lines up, thanks to code tags?
* Permissions
* Count of objects inside this object
* owner
* group
* size
* date
* object name (file, directory, link, device, and a few others are possible like named-pipes.

I hope I suggested following a book to learn this stuff, since 1 skill builds on prior skills.  Jumping too far in based on skills from Windows is a mistake and leads to frustration.

From the teaching you to fish, every command on Unix has a manpage.  Most configuration files also have manpages.  The manpage for** ls** explains what each column is, but because there are many, many, options. I love the -F option for ls.  From the manpage:
```
       -F, --classify
              append indicator (one of */=>@|) to entries
```

What is the "other" part of permissions?   In some textbooks, they say "world", but that isn't correct.  It really is "other" - any userid that isn't either the owner or a member of the group.  Sometimes, we want everyone to have access to a directory except 1 group.  So permissions of drwx---rwx make perfect sense.
By default, in Ubuntu, every userid is also created with their own group.  So, my userid, thefu, also has a group setup, thefu.  The 'id' command will show you the current groups for your userid.  You can get the groups for other userids too.  Dealing with users, groups is usually taught in the first few days of any beginning Linux class.  I teach those concepts before permissions, which happens in the 4th class.

Directories don't need execute permissions always, but in general, it is helpful.  Don't forget that permissions have 3 different groupings, so as long as 1 of those has execute, the directory can still be useful.  Without execute, they aren't hidden, just seeing what is inside becomes impossible. It can be useful.

Get a good intro book, free, no-hassle, here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  LPI has training material links for all skills too.  [https://wiki.lpi.org/wiki/Free_Training_Materials](https://wiki.lpi.org/wiki/Free_Training_Materials)

My considered "how do I learn Linux" article: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - mainly links to excellent articles, but in a specific order to be most useful.

---

### Post by seifer2k on 2019-01-29
I appreciate the links to useful guides to read.  Like others have mentioned, you can find a lot of useless dross on the internet, outdated and whatnot.  So, thanks.

EDIT:  Downloaded that intro book and am going through it now.

---

### Post by TheFu on 2019-01-30
Actually, you should begin with the 2 articles BEFORE reading that book to clear up immediate differences between Windows and the Windows-world compared to Unix/Linux and the Linux world.  Those are fairly short reads, but very dense with useful information for a Windows-centric background.

---

### Post by seifer2k on 2019-01-30
RANT

The CLI document seems very useful for my needs.  The other link to lots of articles written wasn't helpful at all for me, actually.  The one that I found most interesting was the one that wrote out that getting help with Linux if you're a new user will be like jumping into the middle of a jungle full of tigers and lions without any weapons and saying "good luck making it out alive."  That basically, if you're brand new to using Linux and want to ask a question, the experts at using Linux will roll their eyes and say "go read a book", which is completely not helpful to the new person but understandable for the experts when it comes to human nature - nobody wants to answer for the seven-thousand four-hundred thirty-second (7,432) time to do the same damned thing just because the other guy is new.

Problem is, that behavior turns most new people off from using Linux and wanting to learn more.  And some experts in the forum just don't care.  I don't know if you WANT new people to get into using and learning Linux or not.  But if you do like the idea of new people coming in and learning something cool, it would stand to reason you'd be a bit more open to answering questions instead of copy/paste "read this" posts.

(rest of rant deleted)  Ok, I don't wanna p*ss off everyone on the forum or the people who actually DID try to help me, so I'm going to cut the rant short.  I typed out roughly 3 pages of talking about Customer Service standards....but you guys ARE NOT Customer Service, and I cannot expect you to behave as such.  So for that, I apologize. But I'm not some green computer-illiterate kid off the street.  I've been an IT Professional for the last 15 years, and I don't make that claim lightly like a lot of people today do.

Besides, I DID get my two big questions answered enough for me to be able to do what I want without me screwing up the server.   And even if I did screw it up, I could always wipe and re-install everything.

I asked if the MOVE command was recursive, and it turns out it is.  Which is nice, because the move commands in DOS/Windows tend to NOT be recursive.  It'll take time for all the files to be moved, but it'll move.
I already mounted one hard drive.  I can partition/format/mount a new one and it shouldn't be any harder than the last time.

EDITS:  God, my grammar and punctuation was horrible.  I'm STILL correcting the text over and over... unnecessary comma-splice here, run-on sentence there...

---

### Post by mastablasta on 2019-01-31
> **seifer2k said:**
> RANT

The CLI document seems very useful for my needs.  The other link to lots of articles written wasn't helpful at all for me, actually.  The one that I found most interesting was the one that wrote out that getting help with Linux if you're a new user will be like jumping into the middle of a jungle full of tigers and lions without any weapons and saying "good luck making it out alive."  That basically, if you're brand new to using Linux and want to ask a question, the experts at using Linux will roll their eyes and say "go read a book", which is completely not helpful to the new person but understandable for the experts when it comes to human nature - nobody wants to answer for the seven-thousand four-hundred thirty-second (7,432) time to do the same damned thing just because the other guy is new.

Problem is, that behavior turns most new people off from using Linux and wanting to learn more.  And some experts in the forum just don't care.  I don't know if you WANT new people to get into using and learning Linux or not.  But if you do like the idea of new people coming in and learning something cool, it would stand to reason you'd be a bit more open to answering questions instead of copy/paste "read this" posts.



i started off with ZX Spectrum and then got a second hand PC with DOS. and i learned to use form various people who showed me how to do things there, install programs, copy files etc... but that was about it. there was a limit to what i could learn from people around me. and then everyone said just use norton. then i got a second "hand book" about DOS. it had all commands explained in easy to understand way with various example. i really learned a lot from there. there was no internet for us mortals back then. same thing with any OS. for basic use and desktop use someone can just show you around with it, answer to your questions in few sentences or few pictures. but for more complex things it gets tricky if you don't know the background. i met plenty people that use Andorid, not many know how to root it or for example enable developer mode. they dont' have ot know that.

back to CLI Ubuntu linux - much like original dos it comes with man pages for every command. many times you can find the answer there. no need to poke around the web. 

finally about the community here - we are trying to follow the Ubuntu CoC. many of us are not even experts in computers or system developers. the answers should perhaps be mor eto the point but sometimes, as i mentioned previously it is better if the user no only get's the command but also learns what it causes and what the backgroudn it and how it works. and that stuff is best explained in documentation on the web or specific tutorials. 

a tip - often Debian has better documentation that Ubuntu (explained in a better way), so it is a good idea to look there as well.
also Ask Ubuntu is meant for question - answer type of response. you will notice that in forums a debate is often developed afterwards. but not in ask ubuntu.

---

### Post by seifer2k on 2019-01-31
Yeah, I can see that.  I've rooted only one Android phone before and I forgot it wipes the phone.  My father wasn't happy at all that he lost contacts, but yeah.  He's always asking me to do basically illegal things, like "Can't you play a song on YouTube and then use an audio cable to hook it up to your computer and record it?"  And I'm like "You mean, like steal the music?  Last I checked, that was illegal.  You know you can just buy the song for $1 off iTunes and have it 30 seconds later, right?"  Like, there are ways to do things...and there are CORRECT ways to do things.

Like when I came here, I wasn't looking to become an expert at Ubuntu.  My impression of Linux/Unix was that by now it should be super-stable and my server is supposed to be a "set it and forget it" kind of thing, so I wasn't intending to learn everything about it... just enough to set it up properly, which has already been done assuming I never mess with it again.  It has literally two jobs:  FILE SERVER (Samba) and MEDIA STREAM SERVICE (Plex).  But since I wanted to add a new big hard drive in the future, I wanted to have my procedures down first so I don't screw up what is already humming away and working perfectly (a.k.a. the CORRECT way to do things, which is almost never spelled out in all these documents on-line, hence why I came here).

And I like the fact that you guys pointed me towards a good guide for using the CLI for a lot of the relevant tasks.  But pointing me to pages that mostly just repeat over and over "Linux is not Windows so stop trying to make it be" wasn't useful to me.  And I wanted to RANT big time when those pages even admitted to forum users that behave badly because they see it as little kids trying to worm their way into a big kid's group, so to speak.  It's kind of like when someone asks you for a shortcut to being able to do something and you take it as an affront to everything YOU had to go through to learn all this stuff and how dare this punk kid come up and expect to use you as a shortcut to learning all the stuff properly over years the way you did?  You know, that kind of attitude some people get.  And part of having that attitude is absolutely justified, but reacting badly to other people is never justified.

But I did finally get down to where they discuss the file system and how it works (generally), so explaining that directories are also files that just have special properties sort of explains why I have to mount a drive at a specific file location, such as [FONT=arial]/data[/FONT].  In Windows, the files and the file structure for each hard drive is stored on each hard drive.  One of my big questions at the OP was to ask if I unmount the drive and remount it at a different folder location, will that keep everything UNDER that location intact?  The file structure, directory structure, etc.  If I unmount /data and remount it as /data/share, will all the folders under go with it and make /data/share/share and /data/share/media.  Nobody's yet answered that question, nor has any of the linked data files or articles published here in this thread.  So it looks like I'm just going to have to DO IT and find out for myself, and then post back here the results.  If I lose all my data, I'm going to be pissed that I just lost 3-4 months of work ripping DVDs and Blu-rays.  This server IS my backup source.  It's WHY I have a SAMBA share in the first place.  I don't have any USB hard drives or other backup sources.  It's also why I'm considering getting a couple of hard drives and actually attempting a RAID 1 mirror.  But for THAT, I'll have to dig into a lot more documentation on Ubuntu Server, because that's going to be complicated as hell without installing a RAID controller.  I DO have empty expansion slots...

---

### Post by SeijiSensei on 2019-01-31
Actually building a RAID 1 from two drives with mdadm isn't that hard.

Suppose you have two drives which the system labels /dev/sdd and /dev/sde, and you want to create a single filesystem duplicated on the disks.  First, I'd start with 
```
sudo fdisk /dev/sdd
```
then use the commands n)ew, p)rimary to create a single partition that encompasses the entire disk which will be named /dev/sdd1.  Then use the t)ype command to set the partition type to "fd" or "Linux raid auto".  (The command "l" will list the types available.)  Now write your changes to the hard drive with w)rite, and proceed to follow the same steps for /dev/sde.

Now we'll make an array from these:
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdd1 /dev/sde1
```

You'll now have a RAID 1 called /dev/md0.  Format it as ext4 with

```
sudo mkfs -t ext4 /dev/md0
```

then mount /dev/md0 somewhere in the directory structure, let's say "/bigdata".  Edit /etc/fstab (as root with sudo) and add the line

```

/dev/md0     /bigdata     ext4     defaults     0 0

```

By setting the partition types to "fd" Linux will automatically recognize the array members at boot and act accordingly.  The entry in /etc/fstab will insure it is mounted at boot.

You might need to install mdadm; I'm not sure which versions it comes with by default.
```
sudo apt install mdadm
```

---

### Post by TheFu on 2019-01-31
The LVM code which supports different RAID levels is exactly the same as mdadm.  Using LVM for the SW-RAID management would provide some flexibility.
In the Linux world, software RAID has been preferred over hardware or FakeRAID for about 15 yrs. 

I didn't try to answer the question about moving mount points around because I missed it. Simple as that. Yes, you can umount a partition/LV and move it without impacting the data on the same system.  When moving to different systems, the userids and groupids are likely different, which will impact the permissions.  The uid/gid are just simple numbers, usually below 2000 and it is just that number which provides the access to the owner and group.  It is stupid, elegant.

---

### Post by seifer2k on 2019-01-31
So what you guys are saying is that software-run RAID is reliable?  I know it's kind of a touchy subject in Windows, but I sort of figured Linux would be a lot more robust in this regard.

If I do decide to try to implement a RAID for redundancy, I may just go with your suggestion for LVM, as added flexibility in the future that I do not yet know about or anticipate is a good thing.

And if I'm going to be dealing with more than one hard drive for mass storage, as the server is intended to do, it would make a lot of sense to collect them all under a single folder - /data.  That way, each drive has its own folder underneath /data that I can identify readily and easily.  So Media would be the raid and I can get a 2nd 3TB drive and then.... well sh**, I can't use that as a RAID without wiping the drive, so I'd have to move all of the SHARE folder data again.  I'd probably just copy it to my 3TB on my Windows 10 gaming rig here.  It's got plenty of space and the data's only roughly 500GB in size anyway.

Sorry.  You guys just have me thinking about data redundancy when you started talking about running data backups.  At first, I thought this server WAS the backup.  Now I can see that it being a file server really does kind-of ask for RAID mirroring.  If I had a hardware RAID controller, I'd even consider RAID 5 with a hot-spare.  But I'm not doing anything serious on the server at all, so maybe that's just overkill.

Oops.  Lost my train of thought and started rambling.  I do that sometimes.

Sounds good.  Thanks for all the info.  You guys have been a big help so far.  Sorry about the rant earlier.  I didn't mean to come off as arrogant or anything, though I'm pretty sure by now that I did.  I apologize for that.

---

### Post by SeijiSensei on 2019-01-31
An old adage that always proves true: "RAID is not a substitute for backups."

The argument for hardware RAID presumably relies on performance.  Having specialized firmware on a hardware RAID card offloads that task to the controller.  With software RAID the code runs in main memory.  In practice however much of a performance hit software RAID imposes, I can't see it. I've built software RAID devices for well over a decade and never experienced any problems not of my own making ;)

---

### Post by seifer2k on 2019-01-31
Well, I'm wondering if I'm just simply overthinking everything.  I tend to do that sometimes.

Like, it's just a simple home file-server.  Nobody keeps anything super-important like tax returns on it.  It's usually stuff like my MP3 backup (which I do via the PLEX server, not the file share, installers for purchased software, pictures, things like that.  If the house burned down, nobody would care about the data on it, to be honest.  I also have all my MP3s on my Windows 10 rig and my iPhone, so like, 3 copies.  My father has music on the file server, his primary laptop, and his iPhone AND his iPad, so 4 copies.

Nobody's running CAD.  Nobody's doing Bitcoin mining.  Nobody's really doing anything taxing for the servers.  The hardest thing it does is transcode media from 1080p down to either 720p or 480p for streaming.  That's literally it.  And as people pointed out earlier, since I have everything in h.264 encoding contained in .m4v and .mp3 files, the task is relatively easy to perform on a 4-core Xeon E5450 @3.0GHz and with 4GB of RAM (that only uses ~740MB idle).  The server is overkill for what I'm asking it to do and I like it like that.

Probably why I built a gaming rig with an i7 instead of an i5, 16GB when I probably could have gotten away with 8GB, a 980ti when I could have bought a 970 with what I was playing, etc.  I wish I had a 1080ti right now instead, though.  Future-proofing.

---

### Post by SeijiSensei on 2019-01-31
Without the on-the-fly transcoding, you could run a server off a Pentium box, and you probably wouldn't see much difference from the client end.  My office server provides Samba/CIFS and NFS access to its files, including my video archive, DLNA access to the video archive, a local DNS server, an email server, and a Postgres SQL server.  It hardly breaks a sweat.  Most of the time, most of these applications are idle.  Put the firepower where you can see it, at the workstation.

I'm not sure I understand why you're transcoding anything.  Most everything I have is in 1280x720 ("720p") H.264-encoded in the Matroska container.  If I wanted to upscale to 1920x1080, I'd let the TV or other display device do it.  I have some 1080p content, too. I just stream it with NFS or DLNA and, again, let the display device control the size.

---

### Post by seifer2k on 2019-01-31
I have 389 movies broken down with some overlap on the Blu-rays and DVDs where I owned both and ripped both:
128 Blu-ray files (1080p)
59 Downloads (a few are 720p or 480p rips of iTunes copies where I couldn't rip the Blu-Ray discs.  The rest are admittedly downloaded off the internet and in all honesty, I should probably delete)
262 DVDs

I also have 29 TV shows with multiple seasons per show.  Most are DVD but True Blood and Avatar: The Legend of Korra are both Blu-ray sourced, so they're both at 1080p.  I think I also ripped The Animatrix as a TV show with 10 episodes, and that was also part of my Matrix Blu-ray pack, so that's 1080p as well.  I did rip the 3 movies in both Blu-ray and DVD quality, since I own both versions.

The thing is, when I set up the Plex server, I had no idea how much CPU power would be required for transcoding, so I took a MicroATX LGA775 system I had laying around and looked up the most powerful CPU it would support, bought it, and set it up.  It already had a Pentium Dual-Core E5400 2.7GHz processor in it, but like I said, I didn't know how much I would need and I wanted to be able to transcode AT LEAST two streams simultaneously, just in case.  I maxed the system's memory out by buying 2 sticks of 2GB DDR2-800 off Ebay and they work fine.  I ran a full MemTest x86 run on it to be sure.  So now it has a Xeon E5450 3.0GHz Quad Core with a Scythe Byakko offset tower heatsink.  It looks a lot like a smaller version of the Cooler Master Hyper 212 Evo.  It comes in at 130mm tall with a 92mm fan and has at least 3 copper heatpipes.  Keeps the 80-watt quad-core nice and cool.  I have another Scythe Byakko cooling my mom's Q9650 in her Win10Pro desktop in the other room.

The only time transcoding happens is when I'm away from home and trying to stream a 1080p video file.  It automatically throttles the data-stream down to 480p equivalent to save on bandwidth.  The DVDs will obviously stream directly without transcoding.

The only time I've seen any throttling on my server was once.  I did a remote log-in to the server and it reported a full 4.0 under CPU utilization.  That's 100%, so not knowing what the hell was going on (as I haven't ever seen it break 1.0 yet or since), I attempted a restart command.  The system took a lot longer to shut down than normal and then hung on POST because of a CPU FAN error.  That made me very worried and I shut it down and opened it, but couldn't see anything wrong.  I turned the system back on and the CPU fan started perfectly fine and the system BOOTED normally.  I haven't had an issue with it since.  That was over two weeks ago.

---

### Post by mastablasta on 2019-02-01
> **SeijiSensei said:**
> An old adage that always proves true: "RAID is not a substitute for backups."

The argument for hardware RAID presumably relies on performance.  Having specialised firmware on a hardware RAID card offloads that task to the controller.  With software RAID the code runs in main memory.  In practice however much of a performance hit software RAID imposes, I can't see it. I've built software RAID devices for well over a decade and never experienced any problems not of my own making ;)

also if proprietary raid controller has a failure and you can't get a replacement part you could end losing the raid array. i read somewhere it is not easy to just move the drives to another controller and mounting it.

RAID is actually mean to keep the server working even if one or more drives failed. it doesn't actually protect the data. if you get error in your data (corrupted data) the error is then mirrored on the second drive. which is why i am seriously considering disassembling the raid array i setup on the backup server. i actually do not need it.

you need original drive on PC and a good backup program / script that will create backups on the server. these backup must have versions. for added safety you could also run a file system with snapshots option such as ZFS or BTRFS. these are good to protect the os and files in a way if it get's corrupted you can restore to previous state.

anyway on my windows PCs (which have now all but disappeared) i installed Areca. Areca created short scripts which i then ran as tasks on daily, weekly, monthly basis. It uses SSH key to connect to server via sFTP and then transfer the data there. i can restore individual files or the whole "folder image". i setup a similar thing at work, only there i back it all up to a USB flash drive. far from ideal, but at least it's something. alternative option they left me with is kind of lame (manual DVD backup).

---

### Post by seifer2k on 2019-02-02
Well, all of the desktop computers in my house that get used regularly have all been rebuilt by me with SSD boot drives and much larger spinning hard drives for mass storage.  The smallest storage drive I have in a system is 1 TB.  The boot SSDs are usually around 250GB.  I've set all systems like this to do an image backup of the boot drive to the storage drive every Sunday (or the first boot up after if it misses because it was powered off at the scheduled time).  It's already saved me twice on my main gaming rig, as I was able to just restore the last image and all programs and files were intact and working.

Individual file backups can be made to the Ubuntu file server.  That's why it's there.  The WD Green hard drive is stable like a rock in that system.  It was spotty at best while in the USB enclosure.  And I chose to use SAMBA as my file sharing app because the router was using SAMBA to do the file share with the USB drive and while the hard drive was working, it worked perfectly fine.  I already knew it worked with Windows 7 and 10 systems, so any question about OS inter-operability had already been addressed before.  And the guides I found on-line on how to set up SAMBA shares were well written and the commands were easy to understand.  The procedures were laid out well and I was able to follow them to the letter.  The shares I have work and they work as intended, so the ideal thing to do would be to not mess with them at all, if possible.

And I think doing RAIDS would be overkill except for a RAID 1 (mirror) if I decide later to add new storage drives.  That way if a hard drive fails, I haven't lost my data, just one of the drives.

---

