---
title: "Ubuntu Home Media Server Project"
date: 2013-05-20
forum: Server Platforms
---

### Post by ally_uk on 2013-05-20
Hi guys I have some spare hardware ( Dual Core AMD Shuttle ) and a 2 terabyte hard disk I was thinking about setting up a Home Media Server. I have a few goals which I want to achieve I have listed them below.

* Be able to download torrents, Management of torrents can be accessed remotely by use of web management.
* Stream Media to household computers ( two windows 7 boxes, and a PS3)
* Media interface setup on shuttle something like XBMC? 
* Shares setup so I can transfer files from Windows 7 boxes to Shuttle
* FTP setup on Server
* Some form of backing up the media rsync, crontab, 

What is the best approach I am willing to get my hands dirty :) has anyone configured something similar? I will document everything I do and hopefully can produce a write up. Does anybody have any links to get me started? are there any other important services I am missing? 

Many Thanks

---

### Post by grunge09 on 2013-05-20
Try this link and see if that helps

[http://www.havetheknowhow.com/default.htm](http://www.havetheknowhow.com/default.htm)

---

### Post by papibe on 2013-05-20
Hi ally_uk.

A few thoughts:
[LIST]
[*]All services can be set up on a Desktop or Server edition, then It's a matter of:
[LIST]
[*][*]personal preferences regarding how comfortable do you feel using the terminal; and 
[*][*]the resources you have, since the Dekstop will use more RAM, and a bit more processor time.
[/LIST]
[*]I only see the need to stream to restricted devices like your PS3. I would set up either NFS or a samba share for a computer.
[*]XBMC: I can see two set ups here.
[LIST]
[*][*]Server as a media repository: the media files are on on the server, which is in out of the way, and the computers closest to the TV/Stereo would be the ones running XBMC; or
[*][*]You have only one HTPC, which is both the server and the media player. In this case you would probably want to make sure the server has enough resources to play HD video (enough RAM and a modern vIdeo card).
[/LIST]
[*]There are several FTP solutions like vsftpd, and proftpd. If you keep the scope only to your home network, any would be a valid options.
[*]For backups: there are several rsync options, even if you want to include Windows machines (see this [thread]("http://ubuntuforums.org/showthread.php?t=2142799") - from post #6 and forward). Depending of how many machines do you have, you may want to take an extra step and consider BackupPC as a more centralized enterprise solution.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by LHammonds on 2013-05-20
If a 2TB disk is all you have, don't look at it as if you have 2TB to play with.  If you want backups, you need to cut that in half...maybe even less.  You've seen my thread on how I setup LVM and grow the LV+FS as needed.  You might want to start small and bump up the partitions as you need them.  You might just want to have 1 or 2 backups of your partitions and/or you might want to have versioned backups of the data files.  It all requires space and if you only have a single drive, it will need to reside on that drive.

Keep in mind that drives eventually fail so you might want to setup an external drive that you plug-in every once in a while to have an offline backup you keep in the safe or at a family members house that is far enough away that a natural disaster won't wipe out everything you have all at once.

**EDIT:** I have a Raspberry Pi configured with Linux on it to run XBMC and will be setting up another to serve as the MySQL backend and data storage device that all XBMC clients will use when connecting to the central repository.

LHammonds

---

### Post by ally_uk on 2013-05-20
I will be using Ubuntu Server I am pretty comfortable with the command line, I am thinking of going down the route of having the Shuttle as the Media repository which will be serving up files to other clients in a ideal world I guess I want to be able to log onto one of the clients and Fire up XBMC and access any media from the server. Also I guess I would have to have some kind of Samba share setup if I wanted to be able to transfer files to and from the server via the Windows Clients.

On the server it will be run headless what is the best torrent client? I have head people mention transmission is it anygood and does it come with a web management? 

LHAMMONDS in terms of partition the disk what would be the best approach? I am comfortable with LVM I have set it up before following your guide I was just wandering how you would split up the disk and if there would be anyway of having some form of redundancy.

---

### Post by LHammonds on 2013-05-20
> **ally_uk said:**
> I am thinking of going down the route of having the Shuttle as the Media repository which will be serving up files to other clients in a ideal world I guess I want to be able to log onto one of the clients and Fire up XBMC and access any media from the server.
In order to keep each XBMC client from re-indexing and downloading all the info/art from the Internet on each system, you will need to setup a MySQL database server and have the XBMC clients connect to it.  That way, when the 1st XBMC client hooks up and examines the media and grabs the extra info, the 2nd XBMC client that connects to the database/share will make use of what has already been collected rather than duplicating the effort/storage.  You don't "have to" setup a MySQL server but that is the way to avoid duplicated data and faster setup of each client.

> **ally_uk said:**
> LHAMMONDS in terms of partition the disk what would be the best approach? I am comfortable with LVM I have set it up before following your guide I was just wandering how you would split up the disk and if there would be anyway of having some form of redundancy.I would configure it exactly how I have it documented.

If you decide to later add some other feature/service, the partitions will be ready to take on whatever you need and allow you maximum flexibility.  I use this exact setup for every server I roll out.  In this case, I would have a LOT of unused space in the LVM.  I would only extend the partitions as I need them.  I would make use of my script to automate the allocation of partition space and tailor it based on expected growth.

For example, if you want a large media folder such as /mnt/media/, I'd create an LV called "media" much like how I create the "bak" LV/partition.  The initial size would be just big enough to hold the data I plan on putting there right now.  I would then calculate how large my backup would be and expand the "bak" partition to comfortably fit the 1st backup.  After I make my 1st backup of the entire system and maybe just a data backup, I would then figure out how many backups I want to exist on the drive at one time and adjust the "bak" partition size to fit it.

I would then adjust the sizes when calling the "check-storage.sh" script from crontab to match my expectations for minimum free space and how much space would need to be expanded by.  If you create another partition from what I have documented (such as /mnt/media), be sure to add the code inside the script to handle the new partition and its LVG mapper path.

Make sure you run the "back-parts.sh" script to get a copy of your partitions after you have it configured the way you like....then copy them somewhere safe so you can restore the entire system if necessary.  Don't forget to add any partitions to the script that is not part of my "default" partition layout that matches my documentation (such as /mnt/media)

One thing you can do is keep your media "sync'd" to a backup folder and then create (versioned) archives from the backup copy.  On my Minecraft/CraftBukkit server ([link to scripts in thread]("http://forums.bukkit.org/threads/how-to-setup-a-trickd-out-craftbukkit-server-1-3-1-r2-0.100406/#post-1355136")), I use rsync to copy my data files to a backup folder (cb-rsync.sh) and later, I use another script to create an archive off the backup folder (cb-archive.sh).  You can do it in a similar way or use one of many other methods.  Maybe you just cannot afford to keep multiple archives because of the shear size that video files can get.  You might prefer doing a differential backup where your archive only contains the data that has changed since the last backup.  This means you have one archive this is a full copy of everything and subsequent backups are just the difference from the last backup.  You would need to create a new full backup every once in a while or a simple restore could be very irritating having to parse a ton of differentials.  Just know that this particular part of backing up data has a thousand solutions and it all depends on what you want.

LHammonds

---

### Post by papibe on 2013-05-20
> **ally_uk said:**
> On the server it will be run headless what is the best torrent client? I have head people mention transmission is it anygood and does it come with a web management?
I'd recommend transmission-daemon. It is particularly designed to work on a headless server:
[LIST]
[*]It is a service that can be start or stop.
[*]It has a command line client.
[*]It has a web GUI to load, pause, stop, remove and see the status of your torrents.
[*]It has the ability to run scripts when a torrent is completed.
[/LIST]
There are other alternatives, but I'm not very familiar enough with them to recommend any of them. I've played a little bit with the earlier versions of utorrent server (closed source but free), and it was promising back then. It may be worth take a look at it.
 
Just my thoughts.
Regards.

---

### Post by Cheesehead on 2013-05-20
> **ally_uk said:**
> * download torrents, Management of torrents can be accessed remotely by use of web management.
Both deluge and transmission can do this. Deluge also has an optional ncurses interface, for those times I wish to ssh in from outside my firewall.

> **ally_uk said:**
> * Stream Media to household computers ( two windows 7 boxes, and a PS3)
* Media interface setup on shuttle something like XBMC? 
Mediatomb does this very well for me. Web interface.

> **ally_uk said:**
> * Shares setup so I can transfer files from Windows 7 boxes to Shuttle
* FTP setup on Server
I use sshfs for this. The client GUI sees the desired server directory as a mountable drive. Very easy to set up on the client. On the server, it's simply setting up users.
You can also use Samba for this, but that was much more than I needed.
 
> **ally_uk said:**
> * Some form of backing up the media rsync, crontab, 
I use rdiff-backup for this. The initial setup took a few minutes of head-scratching, but after that completely automatic.

---

### Post by xicarusx on 2013-06-08
I have a similar setup and have had one for the past 4 years or so.

I use transmission daemon. I use the WEBGUI to control.

I use PS3mediaserver as a daemon also.

I use the PS3 or xbox 360 as the media interface, and leave the box headless in the network closet.

I setup samba to share certain folders such as /srv/media/video using a username and password login to transfer files to the server.

I don't use FTP since I have SSH setup as it is a headless server. I just use WinSCP and transfer some files that way also.

I use rsync and crontab to make backups to a 2TB external USB drive. 

I also have a PXE Boot Server setup with tools for bootable diagnostics, live linux, av scanners, and a few other things for my in home pc repair business.


All of those things are straight forward to setup, except the PXE server that can be time consuming, but I have a special script I made to do it. If you keep it simple it shouldn't be hard to do or time consuming at all.

---

### Post by ally_uk on 2013-06-10
Thats kool do you have a guide / instructions on how you setupd your server

---

