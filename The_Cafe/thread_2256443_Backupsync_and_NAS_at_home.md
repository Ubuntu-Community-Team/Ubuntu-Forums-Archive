---
title: "Backup/sync and NAS at home"
date: 2014-12-12
forum: The Cafe
---

### Post by stefan_belic on 2014-12-12
Hi guys,
after ***Ubuntu One*** storage ceased to exist, I've tried finding feasible backup and sync solution (that might have web access posible and it's not *Dropbox*) and I've resorted to ***Wuala***. It did its job somewhat well but not good enough, and also I've received mail telling me they are stoping free service. 
The struggle to find solution made gave me this idea. Most of folk need the same thing I do, most of them have some type of small home routers with couple of lan ports and we can agree that hard disks don't cost a lot. Idea is to set up sort of ***NAS***, attach ***HD*** on some controler and on to the home router, ***set up sync/backup between PC and that HD***, and make simplest web interface that allows me to download and upload files from that HD through ***DDNS***.
My questions are:
[I]Did anybody try something likewise?
What are your impressions?
What do you think about general idea?
Ant experiance with DDNS, and security concernt regarding it?[/I]
My idea is if I manage to set this up fairly easy and with least posible expense to make a tutorial or manual so folks can do it on their own at shortest time manor and with small or no expence. That why I came here. 
If you ask why would I bother with this idea, answer is this: After Ubuntu one, no other product came near it (Ubuntu one's folder sync to be precise). Especially not for free. And I like idea that my data is at my home, rather than on the cloud.
I would like to thank in advance anyone participating in any way.
Cheers!

---

### Post by DuckHook on 2014-12-14
There would have been a time when I would have installed *ownCloud*, maintained it and kept it running for myself and family/friends. But with age, I've gotten positively slothful (I'm so stupid and lazy these days). I'm considering buying a *WD My Cloud* and just hooking it to my router.

Anyone with any experience of this gadget?

---

### Post by mJayk on 2014-12-14
Currently have owncloud on a DO droplet VPS, however have been looking into these mypassport devices. They are as cheap as hell at the moment, around 80 quid for a 2TB model; would also like to know if these play well on linux.

---

### Post by DuckHook on 2014-12-14
mypassport isn't the same as My Cloud. Be careful. As far as I know, you can't get a My Cloud for anything near to those prices. My Cloud hooks up to your network through Ethernet and runs as a standalone NAS. Mypassport hooks up via USB, is just a dumb external HD and cannot act as a NAS.

---

### Post by kevdog on 2014-12-15
Your solution depends on your client types -- only linux or mix of other types like Windows or MAC.  
I usually just use rsync or sftp (both require ssh server).  Seems to work well for me.

---

### Post by stefan_belic on 2014-12-15
I must say I like the answers so far. There is certain range of soultions from just a few answers. 
**OwnCloud** - As far as I read so far, it's a free solution and you need to rent a server yourself (from $5/mounth as far as I found).
Pros: Cheep soultion. Compatibility. 
Cons: Your data is still on a far away server, and you have no idea who is hosting it. (depending how much money your are about to spare)
Q: Can it be accessed from any device using web based interface (to upload or download data)?
How much effort does this soultion take? To rent a sever space, maintain it and similar?
DuckHook: Why did you stop hosting it?
mJayk: DO = DigitalOcean? Why would you stop using it?[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1327130")
**WD My cloud** - Nice solution that has most of the things I would need. But I am looking for some challenge if you know what I mean. In this case it buy it and that is it. Own Cloud has that challenge bit I like.
Pros: No effort needed to install or maintain.
Cons: [No effort needed to install or maintain] depending what do you want. 
Q: Can you access data from anywhere (dl and ul)? I don't think so :\
**rsync or sftp** - The soultion I would like kevdog to elaborate about. It sounds promising. How do you host your ssh server (where). Is there a posibility of web based access? I would use only linux clients.
Q for all: How much security can we realy expect from a solution that offers web based access? 
We can rent a server space, but we all have high speed internet that we don't use enough (10+ mbps) and HD's are cheep, why wouldn't we host our server? Can we make a chep soultion in a scenario we don't have static IP address? Some sort of DDNS? How much security can we expect from this sort of solution?

---

### Post by DuckHook on 2014-12-15
> **stefan_belic said:**
> **OwnCloud** - As far as I read so far, it's a free solution and you need to rent a server yourself (from $5/mounth as far as I found).You don't need to rent a server. If you have an old machine  laying around, you can just download ownCloud from the Ubuntu Software  Centre, install it, configure it, and voila, you will have your own  cloud server merrily chugging away at home. That's its raison d'etre...  It allows you to spin your own cloud service, both HW and SW.> DuckHook: Why did you stop hosting it?I never started hosting. I said that I *would* have, meaning that I thought better of it once I concluded that it would be too much bother to maintain. To be doubly clear, I have no actual experience with running it and am commenting based on what I have gleaned from lurking on forums and blogs.> 
**WD My cloud** - Nice solution that has most of the things I would need. But I am looking for some challenge if you know what I mean. In this case it buy it and that is it. Own Cloud has that challenge bit I like.I understand this desire. It's what motivates me to tinker, explore, take apart and not always successfully put back together as well. But I'm doing less and less of those things these days, preferring to just play with the grandchildren.

I should note that, for all I know, the *WD My Cloud* may very well use ownCloud as its foundational app. Western Digital runs most of its other NASes using Linux, so this would be just a natural. I don't know enough about it right now, so just conjecture. If someone is in the know, please share.

---

### Post by leclerc65 on 2014-12-15
I have a WD MyCloud. It's so slow that it"s practically useless.

---

### Post by DuckHook on 2014-12-15
> **leclerc65 said:**
> I have a WD MyCloud. It's so slow that it"s practically useless.Thank you for confirming this. I've heard that My Cloud functionality depends on upload speed of your ISP. Unfortunately, most ISPs only want us to be mindless consumers of their content and have no interest in treating the net as an empowering interactive medium. Therefore, on most home connections, download speeds are high, but upload speeds are throttled to the point of suffocation. Since My Cloud would obviously have to use the upload link to serve data to a remote device, this throttling would render it slow as molasses on data-heavy uses unless you had some sort of business account with your ISP that gives decent upload speeds.

Regardless of the reason, it seems that My Cloud may be better in theory than it is in practice&#8213;at least, for home use. If this is true for My Cloud, then it is probably just as true for any home-built ownCloud server that must go through the same throttled uplink. Put another way, it may not be practical to implement *any* home-based cloud platform because most ISPs have emasculated the ability pull data from a home-based server.

@leclerc65. Have you ever tested what your ISP's upload speed is?

---

### Post by stefan_belic on 2014-12-16
> **DuckHook said:**
> You don't need to rent a server. If you have an old machine  laying around, you can just download ownCloud from the Ubuntu Software  Centre, install it, configure it, and voila, you will have your own  cloud server merrily chugging away at home.

That is something I'm looking for, but do you have any idea what would be best solution to access my own cloud server (at home) from other locations then home? Dynamic IP addresses spoil the story a bit. Couple of solutions that came to my mind, were DDNS, optaining static IP address or the thing I like least renting a virtual server. Any better idea?

---

### Post by DuckHook on 2014-12-16
> **stefan_belic said:**
> Any better idea?Okay, here goes...

There is another option that I've never tried and have only read about: essentially, it involves colocating a rPi server in an Austrian colocation facility and piggybacking on their considerable business-class bandwidth. I first read about it in [this]("http://www.linuxjournal.com/content/raspberry-strudel-my-raspberry-pi-austria") Linux Journal article. I frankly don't trust the cloud for my most important or sensitive data, but others have and obviously like it. As you can see from the article, the colocation firm allowed for a rPi as well as a USB thumbdrive. Considering that you can now get thumbdrives up to 1 TB (yes, [really]("http://blog.laptopmag.com/kingston-announces-worlds-largest-usb-3-0-thumb-drive")!), you can send the whole enchilada to them after preconfiguring the components at home. After they install it, you will have a remote server that not only can run ownCloud, but any further services that you figure the rPi can handle.

If anyone makes a project of this, I'm sure that the people following this thread are all ears and would love to hear back from you.

---

### Post by stefan_belic on 2014-12-16
> **DuckHook said:**
> If anyone makes a project of this, I'm sure that the people following this thread are all ears and would love to hear back from you.

This sounds great! I'll look into it and maybe even order rPI i try it our. It very interesting solution. Thank you DuckHook!

---

### Post by Lars Noodén on 2014-12-16
> **stefan_belic said:**
> 
**rsync or sftp** - The soultion I would like kevdog to elaborate about. It sounds promising. How do you host your ssh server (where). Is there a posibility of web based access? I would use only linux clients.


+1 for rsync / sftp

You could host either behind your own router using a dynamic DNS service to track the name or else put it up on a VPS for a few dollars a month.  Read-only web access is very easy to set up but web access for that kind of thing is quite an anachronism these days when much better options exist, especially with Linux clients.  Your [file manager already supports SFTP](https://www.youtube.com/watch?v=9S4DV1PluzA), so just press ctrl-L and then enter the URI of the destination (e.g. *sftp://stefan@server.example.com/home/stefan/Documnts/*) and then drag and drop like for normal files on your local hard disk.  Similar options like SSHFS also exist and are not mutually exclusive with the file manager or even specialized clients.  

> **stefan_belic said:**
> 
Q for all: How much security can we realy expect from a solution that offers web based access? 


Not much, unless the encryption is done on the client with vetted open source or Free software  tools.  Myself I am sceptical of products and services that rely on javascript in the browser to do anything, especially the encryption.  And in addition to other things the certificate model is kind of broken.  One model that does look appealing is Tarsnap but I've only read about it and have not investigated in depth, nor does it have a graphical client yet.  

> **stefan_belic said:**
> 
We can rent a server space, but we all have high speed internet that we don't use enough (10+ mbps) and HD's are cheep, why wouldn't we host our server? Can we make a chep soultion in a scenario we don't have static IP address? Some sort of DDNS? How much security can we expect from this sort of solution?

Hosting your own server is probably a good way to go.  You would want something that does not draw much current, if possible.  And just transferring files does not require much CPU.  Also, since HDs are cheap, you could try RAID1 (mirrored drives) to protect against device failure.  For backup, two removable USB HDs would work fine, for alternating backups.  One advantage to self hosting is increased control over access or potential for access.

---

### Post by DuckHook on 2014-12-16
> **Lars Noodén said:**
> Hosting your own server is probably a good way to go.  You would want something that does not draw much current, if possible.  And just transferring files does not require much CPU.  Also, since HDs are cheap, you could try RAID1 (mirrored drives) to protect against device failure.  For backup, two removable USB HDs would work fine, for alternating backups.  One advantage to self hosting is increased control over access or potential for access.Many of us like the idea of self-hosting, but as I mentioned above, its practicality depends greatly on your upload speeds, especially if the files to be transferred are large. My own ISP gives me 20 Mbps download, but only 500 Kbps upload and that only on a good day. This is an asymmetric 40x difference in the two directions. For the benefit of general users, you can check both your download and upload speeds on [this]("http://www.speedtest.net/") link, or Google for others. It's a good idea to get this basic issue out of the way first before considering hosting locally.

---

### Post by kevdog on 2014-12-16
Again, it really depends on the size of this project.  IF you are going to be moving a lot of data frequently, perhaps a basic home connection isn't the best thing. In this case it isnt the rsync/sftp that doesnt scale well, its the network.  In terms of backup types, there is rsync (unison which is more a mirroring program that uses rsync), rdiff-backup, obnam, rsnapshot, duplicity, etc.  Most of the programs which feature a GUI usually run one of these utilities down below.  I've tried many of them, however for some reason I find just basic rsync to be the most straightfoward and least error-prone.

---

### Post by PartisanEntity on 2014-12-17
I am using 2 methods:

I rent a Linode VPS running ubuntu server on which I have installed ownCloud. I use it for file syncing and sharing between home, work and friends/family.

I have a dedicated home server also running ubuntu server which offers the following services: internal facing apache web server, virtual machine server, file storage, backup destination (and time machine server) for the computers around the house.

What option makes the most sense for you depends on your needs and how much time and effort you are willing to invest to setup the system and maintain it.

---

### Post by leclerc65 on 2014-12-17
> **DuckHook said:**
> 

@leclerc65. Have you ever tested what your ISP's upload speed is?
My line is 5/1. The cheapest offered !

---

### Post by stefan_belic on 2014-12-19
> **PartisanEntity said:**
> 
What option makes the most sense for you depends on your needs and how much time and effort you are willing to invest to setup the system and maintain it.

There are different methods, I am glad I got new info from guys that that used or use something that I find interesting and challenging, so I can start experimenting on this subject.

Thanks everybody! If I put some of this solutions to life I will post experience and additional info here.

---

### Post by kevdog on 2014-12-19
Couple of things to think about in terms of back up scheme --

1. Where are your backups going to be stored?? Locally on the LAN like on a server, or network attached device or remotely?  If remotely, do you have control of the security of the backups? If security is an issue you may want to think of a scheme that employs encryption
2. Do you want to back up in an image format -- for example taking a snapshot of the drive or drives.  Some schemes you have to restore the entire image and other you can selectively pick files out of the archive to restore.  
3. Space -- How much space do you need to backup and how much space do you have on the backup server -- If you have limited space on the backup machine -- you may want to employ some scheme that after the initial backup, only backs up diffs for subsequent backups
4. Do you need to be able to remotely mount your backups so you can look through them -- some schemes -- rdiff_backup, obnam - employ a filesystem type where you could remotely mount the backup and then peruse through the folder as if it were mounted locally and then selectively take out what you need.
5. Do you need to backup only your files -- or the entire installation (server files, etc).  Some schemes are better suited for user data, where as other are better for the entire installation.  Also sometimes its just better to reinstall the entire OS and then selectively transfer back personal data.
6. How fast do you need to restore lost data?  For example -- if you lose a file do you need almost instant access to the backup copy of this file.  Would the same be true if you lost operating system files or the entire hard-drive crashed.  If the entire hard drive crashed and you were making snapshots -- would the snapshot even include some of the information you lost?  if some type of encryption was employed with the backup -- what means would you use to decrypt and restore the backup?

---

