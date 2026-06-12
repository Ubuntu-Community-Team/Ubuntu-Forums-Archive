---
title: "Making a home media server from &quot;Ubuntu Server edition&quot;?"
date: 2012-08-25
forum: Server Platforms
---

### Post by Templerun on 2012-08-25
New here and relatively new on Ubuntu also. I have been fooling around a bit(successfully) thanks for the so much help floating around. But sometimes too much of it gets me confused. Looking forward to building a Media Server from my old Quad Core system. Please suggest something on file system selection. Basically, I am looking at ...

1. Media Player ... directly connected to my TV, play out movies and videos(XVid, MP4's, mkv's, DivX etc formats).
2. Shunt out my bigger HDD's full of media files and create some kind of network storage with flexible RAID solution(Snap RAID comes to my mind).
3. Run Torrent application which should be able to communicate with RAID solution chosen/suggested.
4. Some place to spare and experiment with other destros also.
5. Bandwidth manager ... (comes later) as and when I connect this always on system to my main router and my other systems and phones connect to net thru this then.

Staring configuration ... Gigabyte G-33 mother-board, q6600 Intel CPU, 8GB of RAM few spare HDD's 500GB,1TB and 2TB. Graphix onboard to start with but I can add a dedicated one later if things work out smoothly.

The article I wish to follow is here ... [How to Build a Linux Media Server - A step by step guide]("http://www.havetheknowhow.com/default.htm") Please suggest any deviations, also if you will recommend changing the file format as I shunt out my HDD's from my main system or if it will work out as it is. In past I have tried Natty on a spare HDD thru GRUB and had no problems accessing my files stored on FAT.

---

### Post by LHammonds on 2012-08-25
Thanks for the link.  I'll be sure to have a look at it.

I am about to buy a $35 board called the Raspberry Pi which will be my media player box running Ubuntu Server on it and XBMC.  I will probably have one in each room and have them all connect to a central MySQL server (maybe a more powerful but still light Nettop PC).

I don't plan to make use of expensive or difficult-to-maintain RAID to protect my data.  I simply plan to have 3 copies of it.  On the MySQL server, it will be the primary data share that will have all my media.  Another machine (possibly one of the Raspberry Pi devices) will have external USB drives and will rsync (mirror) the contents of the main media server.  I will then have another copy that I will rotate offsite (at work).

Reference Thread: [Recommended small ARM systems]("http://ubuntuforums.org/showthread.php?t=2044244")

LHammonds

---

### Post by Templerun on 2012-08-25
The reason behind using SnapRaid ...

SnapRAID is a backup program for a disk array.  SnapRAID stores redundancy information in the disk array, and it allows recovering from up to two disk failures. 
 SnapRAID is mainly targeted for a home media center, where you have a lot of big files that rarely change. 
 Beside the ability to recover from disk failures, the other features of SnapRAID are: 

[LIST]
[*] You can start using SnapRAID with already filled disks.
[*] The disks can have different sizes.
[*] You can add disks at any time.
[*] If you accidentally delete some files in a disk, you can recover them.
[*] If more than two disks fail, you lose the data only on the failed disks. All the data in the other disks is safe.
[*] It doesn't lock-in your data. You can stop using SnapRAID at any time without the need to reformat or move data.
[*] All your data is hashed to ensure data integrity and to avoid silent corruption.
[/LIST]
I m not going gaga over it but this one is sounding right for me. The real test will come when I start using it.

---

### Post by LHammonds on 2012-08-25
RAID consumes your storage (about 40%) in order to provide that ability to recover from a failed drive.  It also takes away from performance unless you have a true-raid hardware controller.  RAID adds a complexity layer and can be a real pain or impossible to "restore" depending on the kind of failure(s). You need a drive to replace the drive that fails and should keep an extra handy for that reason.  RAID is not a backup option...it is an online-all-the-time option.

For home use, I simply do not think that it is all that useful/practical.

Media files rarely change and having an rsync job that keeps your media in sync with a remote system only needs to sync/copy whatever has changed since the last sync.  I like the idea that if the PSU goes out and fries everything in the PC/server, it won't affect my secondary system or my offline backup.  I also like the fact that a restore will not involve anything complicated or proprietary at all.

LHammonds

---

### Post by Templerun on 2012-08-25
LHammonds I liked the idea of "*You can stop using SnapRAID at any time without the need to reformat or move data*" if it gets too much for me then I can fall back. Plz suggest something on the other points I am looking at. That topic was a bit old, I have come across some more topics which suggest using XBMC.

---

### Post by rubylaser on 2012-08-25
> **LHammonds said:**
> Thanks for the link.  I'll be sure to have a look at it.

I am about to buy a $35 board called the Raspberry Pi which will be my media player box running Ubuntu Server on it and XBMC.  I will probably have one in each room and have them all connect to a central MySQL server (maybe a more powerful but still light Nettop PC).

I don't plan to make use of expensive or difficult-to-maintain RAID to protect my data.  I simply plan to have 3 copies of it.  On the MySQL server, it will be the primary data share that will have all my media.  Another machine (possibly one of the Raspberry Pi devices) will have external USB drives and will rsync (mirror) the contents of the main media server.  I will then have another copy that I will rotate offsite (at work).

Reference Thread: [Recommended small ARM systems]("http://ubuntuforums.org/showthread.php?t=2044244")

LHammonds

You'll be much happier with a lighter, purpose built distro than Ubuntu Server for the RaspberryPi + XBMC (like [Openelec]("http://openelec.tv/")).  Otherwise the interface will be VERY slow :)

An HP Microserver makes a great, low power server and will hold at least 5 hard drives easily (more if you want to get creative).  Also, software RAID isn't too tricky, and is very easy to maintain (or SnapRAID + mdhffs or Unraid if you're really against software RAID).  I'd suggest you give mdadm a try, it's really pretty easy and very stable.

I'm not trying to knock your plan, I've just been using XBMC for years on ION boxes and even a RasberryPi, recently.  Also, I've had software RAID servers at home for at least 7-8 years, and it's literally never let me down (always have a backup though :) )  I would really contest the speed line in your last post.  A software RAID array can be very fast if properly tuned, and it's not hardware dependent at all.

---

### Post by Templerun on 2012-08-25
Well! As I said initially ... I am still quite new to Ubuntu but I can get along with it bumping around. What I have in my mind right now is to use Ubuntu 12.04 server as my base OS and the use XFCE as GUI when I need it. XBMC or some other software to enjoy my Multi-media. Since I already have an old system to spare I will use that after re-installing some hardware which I salvaged while building my new system. The main idea behind it is to shift my media files, rest of the functionality can come later. If it can have a RAID option well & good. Anything on bandwidth manager? Once system is fully functional I would like it to be the main file storage and bandwidth distributor for other systems. Plz give some inputs, it will take me some time to do it but I am all in for it now.

Initially, I will be having it connected to my spare port on router, later it will have the direct/sole feed of internet with DHCP disabled on router. Net here is not express and has caps so, the need of managing the bandwidth across other connected systems/tablets/smart phones.

---

### Post by rubylaser on 2012-08-25
Typically, you'd manage bandwidth at your internet gateway (router,firewall, etc).  On my home pfsense box (an old very low power usage PC Engines WRAP box running off a CF card), it's very easy to see my entire LAN's internet usage in a moment. 

[IMG]http://img.skitch.com/20120826-6b6q1e6cu6992tfhncccbqah3.jpg[/IMG]

If you're capped per month, monitoring at the router is the only way to ensure you're not over running your cap.

---

### Post by Templerun on 2012-08-25
No rubylaser! I intend to control individual bandwidth per connection. Keeping the major part with myself ofcource ;) The mac-list way, I saw a link on it but can't find it now. It was very descriptive about sharing @ differential speeds. I will update it here when i find it. If you can suggest something, I can try that also.

Edit: Check this ... [http://rbtech.blogspot.com/2011/12/crashplan-active-bandwidth-control.html](http://rbtech.blogspot.com/2011/12/crashplan-active-bandwidth-control.html)

---

### Post by rubylaser on 2012-08-25
Sorry for trying to help... You said you you where looking for a "bandwidth manager" or distributor for other systems.  What you've posted here is not the same thing. QoS can easily accomplish the same thing with your traffic specifically torrent traffic without the need for a Mechanize script.  This crashplan example is to work around the limitations of their upload client (read the last line of that article and the post even mentions that QoS could have been used).

---

### Post by Templerun on 2012-08-25
Yes! I will have to tinker it a bit for my use ... we have both daily caps as well as monthly caps. If ISPs can do it, we can too on a lower scale ... is what I had in my mind.

---

### Post by Templerun on 2012-09-14
An update and help required ...

Done so far, started the building process, I am using 3 HDDs 1TB, 500GB & 3TB ... 1TB and 500GB have some data on them. 1TB HDD has now Ubuntu on it after partitioning. I am doing some round robin between my windows system and Ubuntu. 1st the DVD-RoM them the HDDs. So, here it goes ...

1. Ubuntu server on 1TB on partition remaining.
2. Installed XFCE desktop and XBMC on desktop.
3. Connected my blank 3TB HDD and formatted it using Webmin and made ext4 Linux partition.
4. It never showed up on desktop or Wemin so I mounted it as Home2
5. Successfully transferred some data on Home2(3TB) from my Windows system using FTP and some more using Team Viewer - File Transfer mode(2GB+ files). FTP had a problem doing files over 2GB.
3. Rebooted the system and it went into DMI pool update and after several reboots and checking BioS I found that my 3TB HDD is being shown as 2TB. But when I check it thru Webmin it still says 3TB but not mounted.
4. As I said about round robining ... my idea was to transfer the data from 500GB HDD before I made that also into Ext4. The data on 1TB I will reconnect into Windows system and copy it there before transfering that also on 3TB.

Now, the problem ... what is happening with 3TB HDD? I need to be sure if I have done it the right way before finally trashing my data on other HDD's(nothing is lost as yet). Also, I tried XBMC it said something about OpenGL and never started. Playing thru VLC, the frames look not so great(low resolution and shaky). I think some problem with G33 onboard grafix chipset driver. If it can be fixed then no problems else I can attach my nVidia card later.

This is what has happened so far, please let me know where I have gone wrong here and if I need to change something before moving ahead.

---

### Post by Templerun on 2012-09-14
More on 3TB disk ...

After skipping during loading I reparted it using GParted it was showing as BSD, converted into Linux. No data could be written on it so CHModed it using Webmin and was able to write/copy on it. Again back to square one after reboot. Can someone suggest me a foolproof way to get it working ... Links I am working on right now>

[http://knowledge.seagate.com/articles/en_US/FAQ/218575en](http://knowledge.seagate.com/articles/en_US/FAQ/218575en)
[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

I think it is the Bios issue here more or less. Help needed to use the full disk as a single large partition to store my all major stuff. I am not going to boot from here.

Another Update: Normal reboot no problems, hard reboots(Total shutdown) the 3TB HDD fails to mount on Home2.

---

### Post by SeijiSensei on 2012-09-14
First, let's make sure you installed the amd64 version of Linux to avoid any file/memory size issues.  Now check that the BIOS sees the drive at its correct size.  You should be able to enter the BIOS (probably with F2 during boot) and have it list the attached devices.  Does it see the drive as 3 TB?

If so, let's try using fdisk from the command prompt.  Let's assume the 3TB drive is /dev/sdb.  Start with "sudo fdisk /dev/sdb".  Now type "p" to print the partition list.  You should have one partition that fills the entire drive with type "Linux".  Is there any unallocated free space?  If so, and there is nothing on the drive worth keeping, type "d" to delete the partition.  Now type "n(ew), p(rimary), enter the number "1" and hit Enter twice to select the defaults for start and end.  Is it any bigger than before?  Then designate the partition type as Linux with "t(ype)".  Enter 83 for the type, then "p" again.  It should say "Linux". 

If it looks like what you want, type "w(rite)" to save the partitioning data to the drive, then "q(uit)".

Now make an ext4 file system on the drive with "sudo mkfs -t ext4 /dev/sdb1".  Then mount the drive to /home2.  How big is it?

---

### Post by Templerun on 2012-09-15
Thanks! I tried everything I could as my knowledge allows. I almost wrecked my Win setup also trying to figure out if I could set it up there. I am now trading my 3TB in and will pick up 2x2TB instead and a few more things which I had laid off as of now. Will update soon as how things are going. Lil bit of tinkering around I was able to start my XBMC also but system freezed after that. All I added was some Java updates ... icetea6,7 basically.

---

