---
title: "Ubuntu linux server vs. Infrant ReadyNAS"
date: 2007-02-01
forum: Server Platforms
---

### Post by puffarthur on 2007-02-01
Hi guys,

I have an Infrant ReadyNAS X6 server on my home network, maxed out with 4 hard drives. I am running out of room on that server, and the problem is that Infrant's NAS products max out at 4 hard drives. I was debating whether to install new, larger hard drives in my Infrant X6, or use an old computer to make an Ubuntu-powered server, transfer those 4 raided hard drives and add more hard drives on top (and eBaying my Infrant X6). I am thinking the latter option would be a bit cheaper and allow me more room for expansion, but more technically challenging. I only have a small amount of experience with Ubuntu (installing it, running Automatix), and I was wondering how difficult this project would be? If it is going to be too difficult and time-consuming, I would rather just buy new hard drives and save my time and effort.

I basically need the server to be a large capacity NAS, FTP server, and print server, and possibly run a bittorrent client. If I go with the build-it-myself option, I have both an Athlon A64 3000+ and a Sempron 64 3000+ at my displosal, and I can use either 512MB RAM or 1GB RAM, but I would prefer to use the Sempron with 512MB RAM if possible. Would that be enough to do the things I want over a gigabit connection with that? Also, does anyone know if I have to reformat those Raided hard drives, or can I just transfer them into an ubuntu server without losing data?

I'd appreciate any advice :)

---

### Post by elst on 2007-02-01
Your hardware is more than adequate, but I wouldn't use a general-purpose operating system like Ubuntu for routers or a large NAS, because these are facilities that you want to work all the time. A standard OS has more "moving parts" than a specialized one, and there is also the temptation to tinker...

An alternative approach is to use one of the specialized distributions that you can load on to a PC to turn it into a NAS, such as OpenFiler.

---

### Post by puffarthur on 2007-02-01
Thanks for the input, elst. I did consider using a NAS-specific build like FreeNAS or OpenFiler, but as I understand they do not do printer serving (FreeNAS doesn't for sure, not so sure about OpenFiler). I also thought running Ktorrent would be nice, since I can control it remotely via webgui from my laptop wherever I am. Maybe I can find other things to offload to the server later on. And the temptation to tinker... is a good thing in my opinion hahaha.

Overall how would you rate the difficulty of this kind of project, for someone who has only a small amount of experience in linux and ubuntu? Easy, Intermediate, Hard? One day project or week long project?

Also, can anyone tell me if I can just transfer my 4x raided hard drives (RAID 5) from the Infrant X6 to the Sil 3114 RAID 5 on my Asus K8N-E Deluxe motherboard? I have no experience working with RAID except for letting my Infrant X6 set it up for me.
*edit* The good people over at the Infrant forums have informed me that I can migrate my RAID 5 (actually X-RAID) hard drives to any linux OS that supports md (raid driver) and lvm2.

---

### Post by elst on 2007-02-02
> **puffarthur said:**
> 
Overall how would you rate the difficulty of this kind of project, for someone who has only a small amount of experience in linux and ubuntu? Easy, Intermediate, Hard? One day project or week long project?


It really depends on how much experience you have of networking. Most services have sane defaults that will work on a private network, but if you aren't familiar with networking then you'll have to do a little learning in that area in order to enable remote access to services on your home network. 

If this stuff is new to you I also ought to add the usual warning about FTP - it's inherently insecure, and you should use the file transfer capabilities of SSH instead. SSH actually provides a suite of functions, and you'll find that many experienced users use SSH for most remote system access on both public and private networks.

---

### Post by puffarthur on 2007-02-02
Thanks again for your help, elst. As you guessed, I am not well-versed in networking, and the most I have done is set up a wireless router with WPA-PSK and maybe setting some static IPs and ports for computers and apps, and use FTP for webmastering. This SSH thing sounds interesting, I'll read up on it sometime. I'm willing to learn more about networking after I finish my USMLE exam in June, when I have time to set up this server.

One more question: I am thinking about running software RAID on linux, is that easy to set up? I want to transfer 4 disks set up in RAID 5 in my Infrant, is there a way to prep an ubuntu machine (it will have 6 sata ports) to accept the RAID array? I've never done a RAID migration before. Thanks.

---

### Post by elst on 2007-02-02
> **puffarthur said:**
> Thanks again for your help, elst. As you guessed, I am not well-versed in networking, and the most I have done is set up a wireless router with WPA-PSK and maybe setting some static IPs and ports for computers and apps, and use FTP for webmastering. This SSH thing sounds interesting, I'll read up on it sometime. I'm willing to learn more about networking after I finish my USMLE exam in June, when I have time to set up this server.

One more question: I am thinking about running software RAID on linux, is that easy to set up? I want to transfer 4 disks set up in RAID 5 in my Infrant, is there a way to prep an ubuntu machine (it will have 6 sata ports) to accept the RAID array? I've never done a RAID migration before. Thanks.

If you are familiar with terms like ports and IP addresses then you should be OK - folks who aren't  sure what NAT and DNS are about can muddle through on private networks, but will come unstuck when they try to set up remote access. 

FTP is unsafe partly because it passes all data in plain-text, including your username and password. If you are specifically interested in Web servers, then keep an eye out for references to "WebDAV" - this is an extension to HTTP that allows for file uploading. IIS, Apache etc. have supported it for years, but client support has been slower coming. WebDAV enables you to upload to Web servers without a separate service, and use the SSL support in the server to protect the whole session.

I don't do much with software RAID, but as the name implies it's dependent on the system kernel, so I'm not too optimistic about your chances of being able to transfer disks from Infrant's proprietary XRAID to regular Linux. It's worth reading up on this, and the Logical Volume Management facilities. You can use LVM to do some cool stuff if you set your storage up for it.

---

