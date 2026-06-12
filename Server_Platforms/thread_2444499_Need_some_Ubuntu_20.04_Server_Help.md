---
title: "Need some Ubuntu 20.04 Server Help"
date: 2020-05-31
forum: Server Platforms
---

### Post by prmmelp on 2020-05-31
[COLOR=#000000]I'm new to Ubuntu and I have installed the 20.04 Ubuntu Server on this machine. Once complete, I installed Cinnnamon Gui and I added drivers for my RocketRaid Hardware card which is currently sporting 2 - 6TB NAS drives, so 12TB on Raid 0.[/COLOR]
[COLOR=#000000]The Hardare is an ASUS B350 Prime board, Ryzen 7, gen 1, 1700x and 16gb, all repurposed but new case and new Raid Card+ drives.[/COLOR]

[COLOR=#000000]Anyways, now I need some help.[/COLOR]
[COLOR=#000000]I am new to server and my linux skills are probably 4/10.[/COLOR]
[COLOR=#000000]I need some decent guidance on how to simply setup this server so I can fileserve. That's pretty much all I want to do for now.[/COLOR]
[COLOR=#000000]I figured there would be a gui interface to set everything up, but it looks like it all has to be done through the command line.[/COLOR]
[COLOR=#000000]I can see the Ubuntu Server on the network, but I assume I have to provision things now for file serving.[/COLOR]
[COLOR=#000000]I installed Samba, but now I'm ready for some help.[/COLOR]

[COLOR=#000000]If anyone is willing to help me through this, I would really appreaciate it.[/COLOR]

[COLOR=#000000]Mel[/COLOR]

---

### Post by TheFu on 2020-05-31
There ain't no gui and most of the time if there is, it shouldn't be used.  That applies to most "server" things on most Linux OSes.

Did you search these forums yet?  Morbius1 usually does the Samba stuff pretty well.
[https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)

Or check the Ubuntu Server Guide?  
[https://ubuntu.com/blog/ubuntu-server-guide](https://ubuntu.com/blog/ubuntu-server-guide)
[https://ubuntu.com/server/docs](https://ubuntu.com/server/docs)
[https://www.techrepublic.com/article/ubuntu-server-the-smart-persons-guide/](https://www.techrepublic.com/article/ubuntu-server-the-smart-persons-guide/)

Samba is really for Windows systems.  For Unix-to-Unix file access there are better and more flexible options, though smb can be used between Unix systems too.  I run NFS for Unix-to-Unix and have a few Samba shares for very specific reasons (Wifi Android clients and 1 Windows laptop). Everything else uses NFS or some other protocol.

i really hope you aren't using raid0, but when you lose all that data, you've been warned.  RAID0 is a really, really, bad idea for anything that isn't a work area that gets completely cleared daily.  Rocketraid stuff is not high-end. Best to use that controller only as JBOD and use raid 1 for your situation if redundancy is wanted.  If redundancy is not needed, it is best to keep the disks separate, with separate file systems, but it really comes down to what you can easily backup.  Losing all the data on both disks would suck.  I&#8217;ve been there. Lost 80% of my data when 1 of 3 disks failed.

There are some rules of thumb about raid controllers in the Linux world.  Don't use motherboard raid and don't use cheap raid controllers.  The JBOD w/ Linux software raid is faster and more flexible.  I just upgraded a system with a cheap Promise RAID controller to a new OS. I'd moved everything critical to other systems before doing that. After the OS upgrade finished and rebooted, the new OS saw all the old storage, exactly where it was supposed to be.  Some of it ran much faster because of the much newer kernel. It was very slow on the older OS.  I've moved that external disk array between 3 physical systems over the last 12+ yrs. Because it is SW-RAID, never had any issues with it except physical SATA connections inside the array would become loose and a disk would be dropped.  Since that was solved with 90-deg SATA connectors, no issues that weren't a dead disk that needed to be replaced. The array rebuilt and all was good.

If you must have HW-RAiD, get 2 identical cards that come from the same vendor lot and include on-board battery backup. When one of the RAID cards fails, you'll still be able to access the data. RAID is for HA. If you are using RAID for some other reason, probably want to consider some other options.  Setting up ZFS with an SSD for a cache device and the back end storage on spinning rust would get you tremendous performance gains over spinning rust RAID0.  ZFS doesn't use HW-RAID controllers.  Basically, if the RAiD controller wasn't $350+ each, use it as JBOD.

A storage server doesn't need more than 4G of RAM, unless running ZFS w/ some advance capabilities enabled.

Often, when that amount of storage is used, it is for media player access.  There are other ways to share media than using samba if that is the plan. Could be worth looking into?

---

### Post by howefield on 2020-05-31
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2020-05-31
Please clarify all the devices / operating systems that will be connecting to your file server which will help determine if Samba is the right choice.

Keep in mind that in mixed environments, you could even setup NFS and Samba to point to the same location (with different share names).

LHammonds

---

