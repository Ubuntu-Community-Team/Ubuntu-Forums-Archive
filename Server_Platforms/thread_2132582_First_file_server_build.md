---
title: "First file server build"
date: 2013-04-05
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2013-04-05
I've decided to upgrade my NAS as it's nearly at 90%, so rather than buying a bigger NAS I thought I would build a server: I could then manage and automate a few other tasks, mainly simple shell scripts to sync various folders/devices. 

It'll be storing media files which will serve XBMCbuntu, and I thought I would install MythTV backend on to it with a TV card. So I can stream live and recorded TV to the XBMC. I have no previous experience of MythTV or even using TV cards.

It will also serve media to Windows machines, which I currently do with Samba from the NAS.

I may also eventually add some kind of network printer, although not really researched this yet.

This is my first attempt at building a server and as I'm fairly familiar with Ubuntu (low to intermediate knowledge) and google agrees that Ubuntu Server would be the best option. 

I'm just wanting confirmation before I go ahead and wipe my Hard drives and install Ubuntu Server. I'm assuming this is all simple stuff for a server to handle. Are there any considerations I should look into first, I haven't worried about security yet as the server will be inside my existing network. Although I would like to be able access the server remotely outside of the local network.

---

### Post by darkod on 2013-04-05
I have no experience with MythTV but for the rest it sounds ideal for the job. I have ubuntu server 12.04 LTS running on HP Proliant Microserver at home. Making it possible to configure programs/tasks on it is definitely worth it. I also moved from a WD network disk to Ubuntu server with the Microserver. You can so much flexibility compared to the limited firmware on NAS devices.

---

### Post by tgalati4 on 2013-04-05
I presume that you have read the community documentation on servers:  [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by Derlux on 2013-04-05
I have done this a couple of months ago, but then started without any knowledge about linux, but getting a server up and running is fun to do. It has some learning curve though.
The things you say it can handle easily. Google does give allot of information and the link that tgalati4 gave is really usefull. Just look everything up you want to do becouse somebody must have done it before :)

It will take some time but I´d say go for it.

Getting it ready for xbmcbuntu is really easy with samba to set up the file share for it.
I hope this helped to make up your mind ;)

---

### Post by spynappels on 2013-04-05
Remember too that you can do one thing at a time, set up the Samba share first, when you're happy with how that works, add the next service etc. 

And don't forget to take backups!

---

### Post by AmbiguousOutlier on 2013-04-09
Thanks for the comments, I'm taking it all on-board. I've been doing a lot of reading especially because I'm waiting for one more component to arrive before I can start building.

One of the very interesting topics I've been reading up on is all about file systems. My file server will have a single 500GB hdd (sda) which I will boot off. And a series of supposedly server type performance WD RE4 2TB hdds (sdb). With only sdb available as a samba share.

I will eventually be running MythTV and although I don't fully understand how it works yet, in mind I understand it to create lots of large files in a temp space on sda then I'll copy them to sdb once completed to serve them to clients. Also I intend to rip BluRays creating files 50GB in size then compressing them down to a few GBs also done on sda and transferred to sdb when complete.

From what I've read ext is not efficient with large files, especially in deleting them. And so I should use an alternative file system. I will not be deleting regularly off sdb just adding data, so I would probably stick with ext4 for reliability. Then I was looking into JFS for sda however I understand this is not stable enough for booting, so sda0 in ext4 for boot and sda1 in JFS for /home. (Plus I'm using a 64bit processor if that makes a difference). Or I could use XFS on the whole of sda? But again I understand JFS to be the best for performance? 

Am I over complicating things? Should I stick with ext4 or will I get a noticeable benefit from using JFS/XFS?

Also as a side question, I'm rebuilding my HTPC using a flash drive should I install using ext2 so I have no journal, as this is bad for flash?

---

