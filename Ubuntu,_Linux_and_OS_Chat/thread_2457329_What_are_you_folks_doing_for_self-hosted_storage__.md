---
title: "What are you folks doing for self-hosted storage?  Recommendations wanted."
date: 2021-01-30
forum: Ubuntu, Linux and OS Chat
---

### Post by uacnt83982803 on 2021-01-30
I am not sure if this is the best place to post this, so pardon if I landed this in the wrong forum.

I have been struggling trying to settle on a solution for self-hosted backups and media storage.  Currently, I have a cloud provider (secure) that I trust but capacity is limited (I was an early adopter so got a free account with decent storage, but not enough for everything).  If I have to pay for a cloud service, that's fine but then the data is still on someone else's computer.  I have photos and data on my laptop, some on my existing cloud storage, and a bunch of photos on A*****.

Ideally, I'd like to have enough capacity that I can start saving all of my videos and movies to whatever this solution will be, so that I can access them within my LAN using my Ubuntu and Windows PC's and Android phones and tablets.  I'd estimate my current data volume at about 200GB but that's without any movies, etc.

From what I've read, a NAS with Openmediavault would probably be a good idea.  Then the question becomes, what NAS?  I don't want something that has to tie to the internet (such as WD's Mycloud).  I want it to be standalone (within my LAN, that is) and if I have to access the data from outside the LAN I understand the best way is a VPN into the LAN or SSH.

I toyed with the idea of building a NAS using a Raspberry Pi 4.  Looks good and the price is right, but then that's something else I have to manage.  And, whatever NAS I use, I'll *still* need to be backing it up (it's a given, no problem with doing it).

There's always the simpler option of external hard drives, tied to one of my PCs (probably Ubuntu).  I could share it, but then speeds will be slow and it won't be any good for media viewing other than opening pictures.

So, I'm really interested in what some of you are doing along these lines.  Sorry for the long post but I wanted to give an idea of what my needs are.  Thanks in advance for any feedback.

---

### Post by SeijiSensei on 2021-01-30
I back up my local machines and remote servers at Linode to a [4 TB external USB drive]("https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817") overnight. I don't know why you're worried about speed from the backup device; presumably you would be using the original copies of the files not the backups.

Also, as a test, I just watched a few minutes of a 720p Blu-ray rip over the network from the external drive. Had no issues with performance.

---

### Post by uacnt83982803 on 2021-01-30
Thanks for your input.  Yes, speed of backup functions isn't important.  It's speed for viewing media that is important to me.

---

### Post by TheFu on 2021-01-31
Viewing media doesn't usually stress any computer with GigE networking hardware.  It isn't like you'll be using USB2 connections, so pretty much any media can be played fine over a wired network using any spinning disks today.  Even USB2 connections are fast enough for a single stream of 4K video, provided the networking is solid.

---

### Post by CelticWarrior on 2021-01-31
> **TheFu said:**
> Viewing media doesn't usually stress any computer with GigE networking hardware.  It isn't like you'll be using USB2 connections, so pretty much any media can be played fine over a wired network using any spinning disks today.  Even USB2 connections are fast enough for a single stream of 4K video, provided the networking is solid.

+1

Exactly, tried and tested successfully.

---

### Post by TheFu on 2021-01-31
My home-built NAS is a $100 CPU+MB combo from 2014, a dual core G3258 w/ 8G RAM.  It has about 32TB connected, runs Plex, mpd, Calibre, and NFS services. It also runs a kvm virtual machine with Nextcloud, ZNC, and Wallabag. Nextcloud is handy sometimes, but most of the NFS storage is provided to it and plex for read-only access. They can't change or delete any content.
```
$ inxi -Fz
System:    Host: istar Kernel: 5.4.0-64-generic x86_64 bits: 64 Desktop: N/A
           Distro: Ubuntu 18.04.5 LTS
Machine:   Device: desktop Mobo: Gigabyte model: H81M-HD3 v: x.x serial: N/A
           BIOS: American Megatrends v: FA date: 12/01/2014
CPU:       Dual core Intel **Pentium G3258** (-MCP-) cache: 3072 KB
           clock speeds: max: 3200 MHz 1: 1421 MHz 2: 1269 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.20.8
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1200@59.95hz
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8168
           IF: eth0 state: down mac: <filter>
           Card-2: Marvell 88E8001 Gigabit Ethernet Controller driver: skge
           IF: eth1 state: up speed: 1000 Mbps duplex: full mac: <filter>
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Info:      Processes: 230 **Uptime: 7 days** Memory: 1931.1/**7413.7MB**
           Client: Shell (bash) inxi: 2.3.56 
```check
It is very stable, though the Realtek RTL8111 is crap, drops packets, so I replaced it with a $10 (in 2005) cheapo GigE NIC. I really need to swap in an Intel PRO/1000 NIC that is laying around here, but I seldom reboot that box.  I don't use RAID on it, but about 50% of the storage is a periodic mirror.  OS backups are network based to a different system.

It is a server, not a desktop, not a playback system either.  For playback, I use raspberry pi v2 or v3 systems or Android tablets for video. For audio, I use mpd (mostly), but sometimes I'll pull audio files to a tablet using nextcloud and play them using local apps and storage. Music and audiobooks need completely different playback apps.

This system doesn't run any VPN, but my VPN has complete access into the LAN - or it used to a year ago - which was the last time I checked. We've been hold up here almost a year now - with just 5 grocery trips into the world. Anyways, I don't know if the VPN still works. Don't have any way to really validate it from home.

I'm not a fan of the all-in-one storage server idea. To me, they are too constraining, inflexible.  But I can understand why someone would seek out a total solution like FreeNAS (or whatever the name is today). They see a list of features that appear to be 1-click installs, and hear lots of zealots who love their version of it.  Guess I'm a zealot too - just for using the flexibility of Linux, which has no limits. But it is harder since the skills to make good choices on an unbounded solution take time to learn.

BTW, I'm looking at replacing Plex Server with Jellyfin. Going by DNS query counts, Plex Server is the 3rd most privacy sucking device on my LANs. Jellyfin appears to do all that Plex does, but it is 100% F/LOSS.

---

### Post by C.S.Cameron on 2021-01-31
I have a 1TB internal SSD and couple of Seagate 4TB external drives for data, TV, Movies and OTR, they are getting full, so I recently added a 4TB 3.5" with external enclosure for overflow, I could not find another Seagate locally here in Southern Provence. Have four old 1TB drives for back up of backup. I have quite a few drives back in Canada with old operating systems and other backup on them. Internet is expensive here at ~ 1500 RS, ($12) for 100GB/Mo. I normally copy the movies and TV to a USB flash drive for viewing and my Old Time Radio and Texted to Speech e-books to MP3 player for listening.

---

### Post by CatKiller on 2021-02-01
> **TheFu said:**
> I'm not a fan of the all-in-one storage server idea. To me, they are too constraining, inflexible.  But I can understand why someone would seek out a total solution like FreeNAS (or whatever the name is today). They see a list of features that appear to be 1-click installs, and hear lots of zealots who love their version of it.  Guess I'm a zealot too - just for using the flexibility of Linux, which has no limits. But it is harder since the skills to make good choices on an unbounded solution take time to learn.

Similarly, I appreciate that there are reasons why people would like the flexibility of rolling their own and the opportunity to develop their skills, particularly if they're already coming from a systems administration or network administration background, but I wouldn't want that for myself. Luckily, it's a diverse field with a spectrum of options. 

Picking some parts out of the OP:

> **uacnt83982803 said:**
> Ideally, I'd like to have enough capacity that I can start saving all of my videos and movies to whatever this solution will be, so that I can access them within my LAN using my Ubuntu and Windows PC's and Android phones and tablets.  I'd estimate my current data volume at about 200GB but that's without any movies, etc.

I want it to be standalone (within my LAN, that is) and if I have to access the data from outside the LAN I understand the best way is a VPN into the LAN or SSH.

I toyed with the idea of building a NAS using a Raspberry Pi 4.  Looks good and the price is right, but then that's something else I have to manage.  And, whatever NAS I use, I'll *still* need to be backing it up (it's a given, no problem with doing it).

The solution I went for, which I think would tick all the OP's boxes, is a straightforward appliance. Synology in my case.

You get centralised storage accessible over the LAN using a variety of protocols, including DLNA. Backing up the data to cloud storage or a local cold copy is a one click affair. Maintenance can be done through a web browser if you don't want to use an SSH terminal (although that's an option). Security updates and drive monitoring happen automatically out of the box, with status lights. Services like media transcoding or BitTorrent are just checkboxes.

One could replicate all of that functionality themselves in a less-good case, at higher cost and with sufficient knowledge. If the learning and the control are the reasons for undertaking the project then an appliance wouldn't be an attractive option. If it's the end result that's the important thing, then rolling your own is a less attractive option. Swings and roundabouts.

---

### Post by uacnt83982803 on 2021-02-01
I agree with the ease of use by using a packaged NAS solution.  I'm just not crazy about routing access from the internet, through Company X, into my network.  For one thing, it relies on them staying in business, for another thing it relies on me having an internet connection.  If I'm going to do that, I'll just use a hosted cloud provider.  Don't get me wrong, that's a great solution for many people, it's just not my preferred strategy.

I decided to take a 2-pronged approach:
1. Obtain a large, USB 3.1-connected external drive.  On its way here now.  I'll encrypt it with LUKS to protect it.  To this drive I'll copy all of my critical data, photos, etc. including pulling down all of my photos on A*****.   That solves the immediate, and more pressing, issue of owning my own storage for critical data.
2. Next, I'll work on a NAS solution that I can keep 100% inside my network which will allow me to handle media, etc. and sharing between PCs.  Since #1 above will have been accomplished, there's less time pressure.  I'm considering building a NAS using the Raspberry Pi platform.

---

### Post by CatKiller on 2021-02-01
> **uacnt83982803 said:**
> I agree with the ease of use by using a packaged NAS solution.  I'm just not crazy about routing access from the internet, through Company X, into my network.

Getting security updates from Synology is no different to getting security updates from Canonical. The rest of the traffic stays on your LAN.

---

### Post by yaminb on 2021-02-01
I have a synology DS 213. A very basic NAS I got years ago.
It's worked great for my needs and you don't need to have an account with synology. There is an account option you can use, I think it's mainly if you want to access it from the internet. I haven't configured that.

I really can't compare it to other packaged NAS. It's the only one I've owned and runs in a closet in the basement for years. 
It can do a whole lot more than I use it for. I basically just use it as a shared drive and all my PCs/laptops/TV have access to it.
The only 'app' I use is DsDownload, which helps with downloads so I don't need to have my PC on for it.

---

### Post by TheFu on 2021-02-02
Raspberry Pi systems are weak at I/O.  This is too keep the costs down, but you'll discover whether this method is sufficient or not for your needs only by testing it out.  Worst case, you have a nearly silent media playback device that connects into the NAS you end up using.

Raspberry Pi is fine for ssh, but noticeably slower for full VPN software use. Whether that is too slow for your needs or not would greatly depend on the ISP connection speed in your location.  20 Mbps - probably fine.  100+ Mbps - no way, but if you can live with 20 Mbps VPN, that's fine too.  20 Mbps != 20 MBps

There are a number of relatively cheap, lower-power using, x64 systems sold in the world today which have SATA3 connectors and run Ubuntu Server (they don't have video). There are many reasons to avoid USB connected primary storage. USB is great for backup storage.

I did see a 2-disk NAS for $170 yesterday - without disks.  Didn't look at it too closely.  Definitely on the lower end.  I know of an AMD GX-series embedded device (no GPU) for $140 with 1 SATA3 port and 2 USB3 ports and multiple Intel GigE NICs. A GPU cannot be added. There are probably slightly different models that have a GPU, I just don't know about those. The machine is designed to be a router, not a NAS.

---

### Post by uacnt83982803 on 2021-02-02
> **yaminb said:**
> I have a synology DS 213. A very basic NAS I got years ago.
It's worked great for my needs and you don't need to have an account with synology. There is an account option you can use, I think it's mainly if you want to access it from the internet. I haven't configured that.

I really can't compare it to other packaged NAS. It's the only one I've owned and runs in a closet in the basement for years. 
It can do a whole lot more than I use it for. I basically just use it as a shared drive and all my PCs/laptops/TV have access to it.
The only 'app' I use is DsDownload, which helps with downloads so I don't need to have my PC on for it.

Thanks.  I did look at the Synology options last night.  I just need to verify that you can log in locally, even without an internet connection.  Sounds like you are saying the answer is yes.

For various clients (Ubuntu, Windows, and Android) what filesystem is best?   Or does the NAS handle all of that when you configure it?  As always, I appreciate everyone chiming in and sharing your knowledge.

---

### Post by CatKiller on 2021-02-02
> **uacnt83982803 said:**
> For various clients (Ubuntu, Windows, and Android) what filesystem is best?   Or does the NAS handle all of that when you configure it?

The filesystem doesn't matter to the client, it's only of interest to the NAS itself. The clients are going to see a network protocol, like NFS, SMB, or whatever. I think my NAS is using btrfs internally, but it was so long ago that I set it up that I'd have to check to know for sure.

---

### Post by TheFu on 2021-02-02
File system choice is an "it depends" question.  

TL;DR - use ext4.

Client access over a network connection doesn't force any specific file system to be used. Choosing a non-native Linux file system would be a mistake often.

It depends on the 
[LIST=1]
[*]type of storage, 
[*]how much storage, 
[*]whether you want to add storage later and 
[*]force it to be included in the same file system or not (dangerous). 
[*]It depends on whether this is primary or 
[*]backup storage too.  
[/LIST]
Primary storage, you may be willing to use a more complex volume management solution, but for backup storage, you don't want to be confused as you restore it.

I always use LVM + ext4, but I **never** (ok ... maybe that isn't 100% true), but very seldom span file systems across different physical storage devices and only do that if my backup storage for that area 100% **is** on a single device.  So, I would span data areas across multiple disks if those were, say 100G, but no way would I span 2x8TB USB3 disks into a single file system. This is because I don't have and don't plan to have (in the next 5 yrs), a 16TB single HDD.

But in a work situation, I've created 50TB spans for single file systems using 50 1TB HDDs. That was because we had tape backups that would easily deal with 50TB.  For file systems over 20TB, I'd change from ext4 to xfs.

For flash-based data, I'd closely look at f2fs.  But I'd need to run some performance tests on my system to see what the truth was.  There is always a real-world difference between what the box claims and reality.  Sometimes an 80% difference.

Depending on what you plan to do in the future, ext4 + lvm could be replaced by ZFS.  There is much less help with ZFS available due to the complexities and probably 70% of MS-Windows knowledge would be useless with ZFS. It is a different way of managing storage.

I would never use any Windows-file system. That would be a terrible idea for a Linux-based NAS for many reasons.
I would never use btrfs either. There seem to always be strange issues and for my needs, btrfs has some faults that require disabling some of the best parts of that file system.  Plus btrfs lies to Linux tools df and du.  That is unacceptable to me.  I want the truth, always.

Before picking any commercial NAS, beware that you want NFS support, not just CIFS/Samba.  Also, the idea of what a "login" means different things to different people. Many commercial NAS devices only provide a web-app interface.  Sometimes they do really odd things like running BRTFS on LVM, which makes very little sense to do. LVM is for volume management.  BTRFS has volume management built-in. Why have 2 volume managers in the storage SW stack?  I can't think of any good reason - except to make things complex so typical home users have to call for support when something bad happens. Billing by time and materials is good work if you can get it.

IMHO.

---

### Post by yaminb on 2021-02-02
> **uacnt83982803 said:**
> Thanks.  I did look at the Synology options last night.  I just need to verify that you can log in locally, even without an internet connection.  Sounds like you are saying the answer is yes.

For various clients (Ubuntu, Windows, and Android) what filesystem is best?   Or does the NAS handle all of that when you configure it?  As always, I appreciate everyone chiming in and sharing your knowledge.

Yep. You don't need a internet connection for the synology NAS.

I'm not exactly a NAS expert, but I chose the defaults that synology has.
I used synology hybird RAID. So I use 2  4TB drives, but get 4 TB capacity with backup. I've had 2 drives fail in the years, and it's been a seamless process to replace the drive and not lose anything.
In terms of formatting, I think it uses ext4 by default, but it really doesn't matter.

To 'share' it over the network, I enabled both SMB and NFS. Maximum powers!

---

### Post by TheFu on 2021-02-02
For your consideration: [https://category5.tv/feature/mynas/](https://category5.tv/feature/mynas/)

The DAS they used is 2x the cost of my Mediasonic ProBox (esata), but supports usb3.1r2 (10 Gbps).
They are using an odroid SBC, which at the time was a better price/performance than any r-pi.

---

### Post by DuckHook on 2021-02-03
@uacnt83982803

Late to the party here, but I'm going to lay out my infrastructure and you can pick and choose the pieces that make sense for you (or reject the whole thing altogether).

I don't believe in paying much for NASes. I've assembled mine from castaways and other people's junk. When it comes to NASes, I'm a cross between Scrooge and WALL&#8209;E. The only thing I'll spring real coin on are good HDDs because they are critical to reliable NASes. The rest of the equipment can be second rate, but the HDDs must be best in class and are worth dropping an extra nickle for.

[list=1]
[*]Main NAS is a rehabilitated My Book Live (now discontinued). As a rule, such "appliances" are a gawdawful investment. The OEMs who make them always drop support for them after three or four years at which point they become malware magnets. There must be hundreds of thousands of these things out there with ignorant/irresponsible owners who have been totally pwned by botnet farms. However, the big saving grace about this specific model—and only this model—is that its firmware can be nuked and completely replaced with OpenWRT. Doing so will not only resurrect the NAS, but convert it into a modern, supported, FOSS&#8209;compliant device that is maintained by a strong and vibrant community. Its other benefits are that it just sips power (mine consumes about 15 watts), is passively cooled (silent) and is so ridiculously simplistic that it is perforce quite reliable. I replaced the original HDD with a 10TB enterprise model. If that's not enough for you, the biggest enterprise&#8209;level HDDs these days are 18TB.
[*]This NAS is so cheap (bought mine used on eBay for US$89) that I bought two. The second has been modified identically to the first. It runs a cron job every night to mirror it to the main NAS. Should the main one go down, I can just switch my network pointers to the "mirror" and Bob's yer Uncle.
[*]Third NAS is another resurrected oldie: an HP Media Vault (again, long discontinued) I had lying around that I gutted and replaced with a cheap used mini ATX board/Celeron CPU combo. Total price with 8GB RAM was under US$100. This one has a small SSD for the OS and a 3TB HDD for Nextcloud, which I run within an unprivileged LXD container for security reasons. It's capable of running with passive cooling, but I don't like the resulting HDD temps (I try not to run them above 40°C) so I added some spare 40mm fans and now it runs around 38°C at full tilt. Power consumption is about 40 watts. The SSD is new but HDD was salvaged from one of the above My Book Lives.
[*]Fourth NAS is an old 32-bit thin client. Ubuntu doesn't even support 32-bit after Bionic, so in a couple of years I guess it'll be moving on to Debian. But for now, it still runs Ubuntu server nicely. This primitive thin client has no HDD, just a small first gen 32GB SSD inside, but it's easily enough to hold an OS. I've attached a number of external USB drives to this puppy for further redundancy and backups. It doesn't have enough oomph to run anything really important, but that's not its purpose: it is for peace of mind. Energy consumption: 25 watts.
[/list]
So, hard drives aside (because the sky's the limit when it comes to storage) all four NASes combined come in at about $300. For that, I get quadruple redundancy, high resiliency, decent capacity and my own 3TB cloud. And the most gratifying thing is that all four devices together consume less than 100 watts! Reusing old stuff can be awesome. It does take some planning, research and dedication, and you are buying into a bit of sysadmin, but it needn't be expensive and for those of a certain persuasion, it can even be fun.

A final word on HDDs. The most expensive part of my NASes was the storage. As mentioned, I didn't skimp on the HDDs. The 10 TB disks are Seagate EXOS Enterprises @ $300 each, so one HDD alone = my entire NAS infrastructure. Since I have two, combined with the USB backups, etc, storage comes to over $1000. If you spring for 18TB HDDs, the cost is even higher, but then, storage is always where the money goes.

---

### Post by mail-2o on 2021-02-21
Great discussion thanks but so wide ranging from the minor to major.
 
As a mere hobbyist I'm gratified to hear that so many use Nextcloud as it is my NAS of choice, but I do wonder about alternatives. It is relatively simple to set up - even for me, and has one great advantage for those with relatively modest requirements such as photo backup and just a few videos for a Plex box. It also has a good notes/calendar function and there are some Nextcloud apps available for 'phones etc. It seems to run, out of sight, out of mind for the most part, cheaply on RPis.

Having had 2 Nextcloud instances fail this week (yes unusual, but partially self induced) I do appreciate that all the files are also on my laptop, desktop and another machine, so it is simply backed up.

---

### Post by TheFu on 2021-02-21
> **mail-2o said:**
> Great discussion thanks but so wide ranging from the minor to major.
 
As a mere hobbyist I'm gratified to hear that so many use Nextcloud as it is my NAS of choice, but I do wonder about alternatives. It is relatively simple to set up - even for me, and has one great advantage for those with relatively modest requirements such as photo backup and just a few videos for a Plex box. It also has a good notes/calendar function and there are some Nextcloud apps available for 'phones etc. It seems to run, out of sight, out of mind for the most part, cheaply on RPis.

Having had 2 Nextcloud instances fail this week (yes unusual, but partially self induced) I do appreciate that all the files are also on my laptop, desktop and another machine, so it is simply backed up.

Nextcloud isn't a NAS. It is an access protocol.  On your LAN, if you use Nextcloud for system-to-system access for streaming media, you'll be very disappointed.  Best to use NFS, if possible. 2nd choice would be SMB/Samba, if the client cannot support NFS.  For streaming media, NFS seems to be better and prevent stuttering.  It isn't like Plex is going to connect to Nextcloud to stream media.  Also, when using NFS, prefer the OS-level mounts, not the NFS access provided by a GUI (Kodi does this).  NFS that goes through the Kodi GUI is measurably slower and uses much more system overhead than a normal NFS mount in the /etc/fstab. 

Think of nextcloud for human file access mainly.  SeaFile would be another option to keep files copied on a local device and on your remote server. Nextcloud has many more addons than the other options. Please only use nextcloud over a VPN when remote.  The calendar and addressbook support in nextcloud is nice for many families. I always found it lacking compared to Zimbra, but nextcloud is 100x easier than Zimbra to setup and run. Zimbra is easier to use, however and supports normal protocols and federated calendars.  I connect to a few public calendars through zimbra and my multiple clients all get access to those in addition to my normal, private, calendar.  I never miss knowing about any holidays, for example. Tomorrow is George Washington's real b'day. Next Monday is Pulaski Day in Chicago. ;)

---

### Post by SeijiSensei on 2021-02-21
> **TheFu said:**
> Best to use NFS, if possible. 2nd choice would be SMB/Samba, if the client cannot support NFS.  For streaming media, NFS seems to be better and prevent stuttering.
I find DLNA just as stutter-free as NFS even over wifi. I prefer NFS, but there are fewer clients.

---

### Post by TheFu on 2021-02-21
> **SeijiSensei said:**
> I find DLNA just as stutter-free as NFS even over wifi. I prefer NFS, but there are fewer clients.

Oh- sorry. I use dlna for videos on the LAN too. 

My video storage and DLNA server is the same machine.  DLNA video clients include kodi/osmc on Raspberry Pis, vlc on android.  Real computers use NFS for video playback.
I do use nextcloud on android systems for ad hoc file access.

But for everything else, it is NFS for file access on he LAN for real computers. To me, a real computer runs a full Linux, supports nfs, and has a keyboard.  A chromebook is close, but last time i checked, did not support nfs.

---

### Post by DuckHook on 2021-02-21
> **mail-2o said:**
> …I'm gratified to hear that so many use Nextcloud as it is my NAS of choice, but I do wonder about alternatives…
> **TheFu said:**
> Nextcloud isn't a NAS. It is an access protocol…
It's not even a protocol. It's a platform, like Google Drive and One Drive and whatever Apple calls theirs. Too abstracted from fundamentals to be a protocol.

@mail-2o This is a murky but important distinction: when we try leveraging platforms to do the job that appliances are designed to do, then we ask for all sorts of trouble. You ran into one yourself when the "cloud" crashed. It happened to me this weekend too, though mine has been giving trouble ever since I've been test&#8209;driving it (a couple of months now).

The problem with platforms is that they are layered, ungainly and complex. Consider: to run Nextcloud, we start with Linux. Then we layer a huge ecosystem of database, webserver, and PhP on top of that. If you are like me, then it runs within a container or VM to fend off the scumbags. Then we hork Nextcloud on top of all this. But we're not done yet. In order to make it useful, we add yet more apps, services, gadgets and doodads. The end product is this Rube Goldberg contraption that looks real purrty, but is absurdly complex and fragile for something as simple as backing up. I suppose that if we leave its maintenance to a massive trillion dollar company like Google, then we can count on some reliability, but trusting our own? Unwise.

Contrast to TheFu's solution. His backups require… Linux. That's it. Well, I suppose that he is technically adding NFS to it, but NFS is such a primitive foundational protocol that it may as well be part of the OS. Very little to go wrong.

I would say that if your use of Nextcloud as NAS has been fruitful, then you've been lucky. Counting on luck is not a good strategy for backups. Instead, convert one of those RPis to a much simpler dedicated CLI backup appliance with a decent USB drive for storage. Your life will be simpler, sweeter and more secure.

---

### Post by TheFu on 2021-02-21
Just to clarify ...

There is no NFS in my backup chain. Networked storage (dav, cifs, samba, nfs) is a liability for secure backups, IMHO.

Nextcloud is an untrusted system to me.  Untrusted means never put anything into it I expect to access later.

---

### Post by kevdog on 2021-02-24
I just run FreeNAS (which is now called TrueNAS core).  TrueNAS runs on top of FreeBSD.  TrueNas Scale will be available likely in 2022.  It will be TrueNAS running on top of a Debian base.  I believe they went this way so they could leverage Debian's hypervisor (KVM) instead of FreeBSDs hypervisor (Bhyve).  Additionally it will offer a Rancher like setup if you need to run containers with high availability.  If looking for a backup solution which pushes your knowledge and you can learn a lot of great things, I'd recommend TrueNAS.  I've learned a lot.  For the casual user, I'm not sure it would be the best backup solution since it does require some periodic maintainence.

I'm currently running Nextcloud within a FreeBSD jail within TrueNAS core.  Nextcloud is kind of a trick beast.  It's interface definitely isn't the snappiest and I'm guessing because of its reliance on a php backend.  It offers a lot of features, but thats probably part of the problem -- does a lot but doesn't excel at any one feature.  It tends to break for me at least commonly with upgrades, which requires some troubleshooting and some various looking at forum posts on the Nextcloud forum or TrueNAS forum.  It's usually a variation of the same type of problems over and over again, so after debugging it for the like the 20th time, you get pretty good and efficient at solving the issues with Nextcloud. If I were to start from scratch, I really consider dockerizing the entire setup rather than installing all the individual pieces.

---

### Post by DuckHook on 2021-02-24
> **kevdog said:**
> If I were to start from scratch, I really consider dockerizing the entire setup rather than installing all the individual pieces.
That's an interesting and valuable take on things. I've gone the opposite route, at least in this one regard: I've found that the individual pieces give me a fineness of control that I missed using their scripted install.

I agree with you on the container part though. Docker would be a good way to go. I use LXD, but they are the same principle. I've also considered a VM, but I'm using old HW and would be worried about the resource hit. A jail doesn't seem quite secure enough to me. Maybe it's my paranoia acting up again.

---

