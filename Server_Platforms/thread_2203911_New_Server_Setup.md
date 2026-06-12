---
title: "New Server Setup"
date: 2014-02-05
forum: Server Platforms
---

### Post by jcslone on 2014-02-05
Hey everybody,

Ok so it's been a while (about a year and a half) since I've played with a Linux distro of any sort so I'm rusty and have a lot of catching up to do...

I want to build a server to house all my media (movies, music, photos) and subsequently stream it. I plan on using Plex to accomplish that portion since it offers everything I need and is released for Ubuntu.
The second portion of my project is a private file server (personal cloud if you will) from which I can back up all my mobile devices and computers to either by direct connection (the easy part) and remotely (I was thinking of using an FTP client for this portion but I am also looking into FreeNAS).

EDIT: After more research and talking to people who have used Plex this is the build I'm considering...your input, suggestions, advisements are all welcome :)

SERVER SPECIFICATIONS:
	-CPU: AMD FX-9370 Vishera 8-core 4.4ghz AM3+ ([http://www.newegg.com/Product/Product.aspx?Item=N82E16819113346](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113346))     $250
	-MOTHERBOARD: Gigabyte GA-900FXA-UD3 ([http://www.newegg.com/Product/Product.aspx?Item=13-128-514](http://www.newegg.com/Product/Product.aspx?Item=13-128-514))     $135
	-OS DRIVE: Samsung 840 EVO 120GB SATA III SSD   ([http://www.newegg.com/Product/Product.aspx?Item=N82E16820147247](http://www.newegg.com/Product/Product.aspx?Item=N82E16820147247))     $90
	-STORAGE DRIVES: Seagate Desktop HDD.15 ST4000DM00 4TB Drive (x6)     ([http://www.newegg.com/Product/Product.aspx?Item=N82E16822178338](http://www.newegg.com/Product/Product.aspx?Item=N82E16822178338))    $165 ea
	-GRAPHICS CARD: ASUS HD7770-1GD5 Radeon HD7770 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814121663](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121663))     $108
	-RAM: GSkill Sniper Series 8GB ([http://www.newegg.com/Product/Product.aspx?Item=N82E16820231460](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231460))     $85
	-CASE: NZXT Source 210 ([http://www.newegg.com/Product/Product.aspx?Item=N82E16811146075](http://www.newegg.com/Product/Product.aspx?Item=N82E16811146075))     $40
	-OPERATING SYSTEM: Ubuntu Server    
	-MEDIA SERVER: Plex   
	-FILE SERVER: FreeNAS   
TOTAL: $1698

Thanks everyone!

Josh

---

### Post by TheFu on 2014-02-06
Do not use FTP.  Use sftp. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) FTP is not secure and has a number of issues.

If you do run ZFS, then 8G is the starting point for RAM, but more is better. For that amount of storage, I think they recommend 32G of RAM.

---

### Post by Bucky Ball on 2014-02-06
*Thread moved to **Server Platforms**.*

---

### Post by jcslone on 2014-02-06
Thanks for the pointer to sftp. I should have said up front that I wanted a secure connection.

When you say ZFS I assume you're referring to the filesystem...I've only set up Ext3 before, why wouldn't I just want to stick with that?


aaaaaaannnndddd another hardware change (I swear to God it's the last!).

CPU: Intel Core i7-4770 3.5ghz Haswell
Motherboard: MSI B85-G41([http://www.newegg.com/Product/Product.aspx?Item=N82E16813130699](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130699)) 

Switched to Intel after doing more in depth research and checking up on benchmarking.

---

### Post by TheFu on 2014-02-06
You said you were running FreeNAS. That is BSD-based, not Linux.  The primary reason people run it is for ZFS, plus you have 6 HDDs spec'd and too much RAM for a simple Ubuntu-based server.   If you do not intend to run ZFS, don't bother with FreeNAS.  

If you do still intend to use FreeNAS, definitely go to the FreeNAS compatibility lists - **BSD compatibility is NOT the same as Linux compatibility.** Don't get burned.

Are you planning to add a disk controller? Something from LSI?

I'm confused why a Core i7? For a Linux-based media server an Atom or Celeron CPU would be fine and 2G of RAM would be fine. Check out the SuperMicro boards - more PCIe slots and better RAM.

---

### Post by thnewguy on 2014-02-06
> **TheFu said:**
>  If you do run ZFS, then 8G is the starting point for RAM, but more is better. For that amount of storage, I think they recommend 32G of RAM.

ZFS will run smoothly with 1GB of RAM in most cases. You only need more if you enable a lot of extra features, such as deduplication. Even then you can easily get away with a lot less than 8GB of RAM. I run ZFS on a couple of machines, all of them with 1GB of RAM or less and they don't use all the memory available to them.

---

### Post by TheFu on 2014-02-06
> **thnewguy said:**
> ZFS will run smoothly with 1GB of RAM in most cases. You only need more if you enable a lot of extra features, such as deduplication. Even then you can easily get away with a lot less than 8GB of RAM. I run ZFS on a couple of machines, all of them with 1GB of RAM or less and they don't use all the memory available to them.

There are many considerations for ZFS performance. The [recommendations for FreeNAS is 1G of RAM for every 1TB of storage managed.]("http://doc.freenas.org/index.php/Hardware_Recommendations#RAM")
A number of people have seen terrible performance with less than 8GB of RAM, even with minimal storage amounts, hence the minimum recommendation that 8G is the smallest amount of RAM for a ZFS system running FreeNAS.
> The sweet spot for most users in home/small business is 16GB of RAM. 

I'm certain that we'd all love to know the system configs that you are running, RAM, CPU, disks, controller and performance with ZFS. Real world numbers trump "recommended sizes" every day in my book.

---

### Post by jcslone on 2014-02-06
Ok just to clarify I have not bought/invested in anything yet...what I have posted is what I am considering at this point. I'm still open to suggestions.

Maybe some specific questions are in order...

1) If I am going to be running a RAID 1 setup, will the integrated RAID controller in the motherboard be sufficient or should I purchase a separate controlled? If so what is recommended?

2) If FreeNAS is BSD solution then what is the best way to go about setting up a file server with which I can backup/download to and from? (Need to be able to interface with it from Android devices)

I'm going with an i7 because the primary job if the server is going to be to stream (and if needed) transcode high definiton video and audio to multiple devices simultaneously. A single core CPU won't have anywhere near enough juice to handle that workload.

---

### Post by brokenhachi on 2014-02-06
FreeNAS has a plex plugin: [http://www.freenas.org/whats-new/2013/09/plex-on-freenas.html](http://www.freenas.org/whats-new/2013/09/plex-on-freenas.html)

also, if you're going to use freenas, there is no *extX* since it's unix based. You'll get the option of ZFS or UFS. If you decide to go with the ZFS do away with the raid controller, or get one that has integrated JBOD/IT/IR mode (ibm m1015/1115?), as ZFS does not play nicely with raid cards. ([http://doc.freenas.org/index.php/Hardware_Recommendations#RAID_Overview](http://doc.freenas.org/index.php/Hardware_Recommendations#RAID_Overview))

With FreeNAS you can create NFS and samba shares for the fileserver portion, and you can drop to CLI and install BTSYNC in a jail to sync backups from android devices to FreeNAS. ([http://blog.bittorrent.com/2013/06/17/bittorrent-sync-turning-your-old-computer-into-an-nas-drive/](http://blog.bittorrent.com/2013/06/17/bittorrent-sync-turning-your-old-computer-into-an-nas-drive/))

also the recommendation for drives in freenas/zfs is as follows:

1(or more) SSD for read cache (L2ARC) (MLC preferred)
1(or more) SSD for write cache (ZIL/SLOG) (SLC preferred, but expensive... :( low write latency MLC is ok)
the rest can be low performance high density drives

They also recommend installing the freenas on a usb stick, then using the HDDs as data storage. 


I'm just getting started in freebsd/ZFS, and its a whole new world of awesomeness.. if you're into that kind of thing!:biggrin:

---

### Post by jcslone on 2014-02-06
Ok so FreeNAS is an OS in and of itself (way for me to do my research before running my mouth lol)...

So for what I want to do is FreeNAS the best solution or can I accomplish what I want to do better/comparatively easier on Ubuntu? I also have zero experience with freebsd, would the learning curve (especially given what I want to do) be higher than on Ubuntu?

The clients that would connect to the server are Windows, OS X, iOS, and Android and possibly Chromecast (but that would be handled internally by Plex so I'm not worried about that part).

---

### Post by brokenhachi on 2014-02-07
FreeNAS is really simple to set up, and most likely you'll never *have * to use the command line, so you'll really not even notice its bsd. What clients connect doesn't really matter as everyone supports samba (CIFS), so you'll just need to create the samba shares. If you prefer learning and the command line maybe do it with ubuntu, build a headless server install the packages, edit the conf files etc. Building a fileserver/mediaserver is not difficult though so it shouldn't take much time. Granted, you may not learn very much.

If you're looking for the easier lower maintenance option, take FreeNAS, its all gui and super simple. Plus, ZFS is just *freaking awesome*. It eats ram like crazy though, so: The ubuntu server will be significantly cheaper. I have a media server running sabnzbd, vlc, btsync, etc etc running on a 4 (6?) year old dell laptop with 4gb ram and a core 2 duo. If you decide to go with freenas consider getting SSDs for the cache drives as I mentioned before. You can use cheap WD Greens for data drives or whatever is cheap.. you dont even need 7200rpm drives if you use the ssds for cache.

Definitely consider btsync for the backups from the mobile devices though!

---

### Post by jcslone on 2014-02-07
Then freenas it is! (Time is a premium when you have a newborn and two toddlers!). Much thanks for the advice I've gotten from all of you.

Josh

---

