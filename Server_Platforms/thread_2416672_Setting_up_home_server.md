---
title: "Setting up home server"
date: 2019-04-13
forum: Server Platforms
---

### Post by winecurmudgeon2 on 2019-04-13
I'm ready to set up a home server -- been using an NAS, which is cumbersome and too complicated for what I need: Backup, share music and some videos using Plex, plus switch from Dropbox to Nextcloud. So a couple of questions:

1. How much power does the computer for the server need? Is an ARM or Pentium/Celeron processor enough? How much RAM?

2. What's more cost efficient? Buying out of the box or putting together a Raspberry Pi or Intel NUC?

3. What's the advantage of running Ubuntu server vs. Xubuntu, which I run on the rest of my computers?

Thanks for your help.

---

### Post by TheFu on 2019-04-13
> **winecurmudgeon2 said:**
> I'm ready to set up a home server -- been using an NAS, which is cumbersome and too complicated for what I need: Backup, share music and some videos using Plex, plus switch from Dropbox to Nextcloud. So a couple of questions:

Congratulations. When you setup a server, you have the control.

> **winecurmudgeon2 said:**
> 
1. How much power does the computer for the server need? Is an ARM or Pentium/Celeron processor enough? How much RAM?

It depends.  These things are different types of services, so it is best to keep nextcloud in a separate, logical, server. I've been running nextcloud for about 2 yrs. All was fine until about a month ago after a normal update broke file sync.  I don't use file sync much, but considering that this is the core feature for nextcloud, it isn't good. In short, keep nextcloud in a separate virtual machine or separate container or on separate physical hardware.  Which is completely up to you and your skills.

How much CPU and RAM is needed depends on which nextcloud addons are enabled and whether you use plex to transcode during playback for 10 devices, 5, 2, 1, and what the source media might be. I'm addicted to the Plex video chat addon.  Lets me  video chat with family while I'm travelling.  I also need plex to transcode h.265 1080p videos to h.264 720p video on 2 devices in the house. I use Raspberry pi v2 systems that only handle h.264 video in hardware decoding.  We don't have any 4K video, but I'd bet that would at least double the CPU requirements for each stream.  If those things are used concurrently, a more powerful computer is necessary. Plex claims that 2000 passmarks are needed for transcoding each stream (I think). That depends on the source and what your playback devices can handle.

NFS is an tiny consideration. For it, you'll want USB3 or SATA connected disks and at least GigE networking.  Only use samba/CIFS if you have Windows clients.  Nextcloud can access NFS storage no issues.  I use read-only mounts for nextcloud to access media files.  I'd rather not have some internet service open to the world where bad people can delete all that data.

Backups need to be on a different system.  Physical separation of backups from any production computers is needed. Period.  Use "pull" backups, never push.  Don't mount backup storage onto any client. Backup tools should use client-server network architecture, not networked storage sharing. Many reasons for this.  Check out rdiff-backup or BorgBackup as solutions.

> **winecurmudgeon2 said:**
> 
2. What's more cost efficient? Buying out of the box or putting together a Raspberry Pi or Intel NUC?
NUCs are way, way, way, way, overpriced.  I wouldn't use a Pi for anything NAS, much less where real storage is needed.  There are better SBCs for just a little more money that have SATA or USB3 and real GigE networking.  But if you need plex to transcode anything, forget ARM.  Around here, you can get a 65W Ryzen 5 1600 for US$80.  Get an $80 motherboard and $80 in RAM and you have an impressive, computer for under $300.  Use old case, disks, keyboard, GPU, and whatever else you need to build the box.  It will be cheaper than a NUC and 2x faster with room for storage.  Put this "server" with a power cord and network cable into a closet somewhere, only access it over the network.

> **winecurmudgeon2 said:**
> 
3. What's the advantage of running Ubuntu server vs. Xubuntu, which I run on the rest of my computers?

Internet-facing systems should never have a GUI. It opens too many attack vectors.  If it is on your LAN and only on the LAN, then it doesn't matter much, unless you go with SBCs.  An SBC needs all the CPU it has just to do the normal services. Adding a GUI on an already limited computer will take 50% of that processing power away.

> **winecurmudgeon2 said:**
> 
Thanks for your help.

If you insist on using an ARM/SBC, check out Odroid-N2 and Rock64Pro boards.

About 5 yrs ago, I built a NAS+plex+VM server for $126.  It was build using used parts I had lying around, but a new CPU+MB+RAM.  There was a $99 CPU+MB combo deal here for an Pentium 3258.  It is still going and handles the same stuff you want nicely.  Completely unintended, but even my nextcloud virtual machine happens to be running on that Pentium with KVM hypervisor today.  I moved it from another system sometime last year. With Intel CPUs, often they have onboard iGPUs, which saves that code, but makes CPU upgrades in the future nearly impossible.  With AMD, the AM4 motherboards support a very wide range of CPUs from very low end to fairly high end.  A CPU swap can make a huge diff in 2 yrs, if you want to start really cheap today.

And just so you know, I have never signed up for any plex account and don't use any paid plex clients, yet can access all the media from any internet connection in the world.  The only reason I'd sign up for a plex account would be if I wanted to share media with family. Most people wouldn't setup a SOCKS proxy to access plex media like I do with ssh or setup a full VPN, which I've done.  Either work fine, but the VPN is much easier to use from tablets/Android and the ssh-SOCKS is easier from laptops when travelling.  But how much effort you want to put into this depends on your stance with privacy.  

The same secured connections are needed to access Nextcloud.  I don't trust it to be generally available over the internet. Lots of bad-guys out there trying to hack email, web, and any other service they can find.

I can share my experiences with different nextcloud addons. Most "just work", but a few require some complex setups by clients which were worse than other solutions I'd already had working for a decade. Contacts, calendaring, are to examples where nextcloud sucks.


IMHO.

---

### Post by winecurmudgeon2 on 2019-04-14
Thanks for all this. I appreciate the trouble you went to.

---

### Post by mastablasta on 2019-04-15
Depends what you will do and how many user will be using it. I decided to go with HP Proliant Microserver. Bough a new, yet older model, so it was quite cheap and came with ECC ram (for extra data protection).  It seems like an overkill and underutilised. if i went at it again, i would use a Pi or similar board. it seem t would be more than enough for my needs.

---

### Post by slickymaster on 2019-04-15
*Thread moved to **Server Platforms**.*

---

