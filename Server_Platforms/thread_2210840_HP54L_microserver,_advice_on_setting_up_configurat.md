---
title: "HP54L microserver, advice on setting up configuration"
date: 2014-03-12
forum: Server Platforms
---

### Post by carlo3 on 2014-03-12
Hi all, I've picked up a HP54L microserver and am wondering what the best way to configure it would be. I would like to have Ubuntu server running on it, I don't really have much spare money to pick up a WHS license and I've really enjoyed using Ubuntu on my laptop so far. I'm pretty confused after reading various set ups and guides on how to configure it best so hopefully I can explain my intended usage and get some opinions on the best way about it. 

There is a 300gb OS drive, currently a single 2tb WD green with 3 more drives on the way in the next week or so. Hopefully I can do some of the legwork before they arrive as I have some free time at the moment. The machines accessing the server will be a combination of windows and linux computers, and media devices such as my PS3, tablets, phones etc.

I do a lot of 3d modelling/rendering, so there would be a fair amount of files on the server. Some of these can be fairly large files, especially when working on them. It would be awesome if I could set it up to have a projects area, and a library area which would contain assets that I use often. The projects area would be where files are stored that I work on, essentially only using local storage for temp storage such as writing out caches, etc. I guess in windows I would map a drive to my pc and work off that.

So without writing a giant wall of text, it would need to:

[LIST]
[*]act as a file server
[*]be able to stream media to ps3, tablet etc.
[*]be accessible with windows and ubuntu
[/LIST]

I've been reading [this guide]("http://linuxhomeserverguide.com/") which sounds promising, I like the idea of virtualising but have no experience with it (or setting up anything beyond a NAS). I also read in [another thread]("http://ubuntuforums.org/showthread.php?t=2198546&highlight=home+server+n54L") that this machine isn't really powerful enough to do it well. I also don't have too much of an idea on whether I need to set up a RAID, what sort of RAID etc. I think to sum up, I'm very green to all this and any help you can all provide is extremely appreciated!

---

### Post by sandyd on 2014-03-13
> **carlo3 said:**
> Hi all, I've picked up a HP54L microserver and am wondering what the best way to configure it would be. I would like to have Ubuntu server running on it, I don't really have much spare money to pick up a WHS license and I've really enjoyed using Ubuntu on my laptop so far. I'm pretty confused after reading various set ups and guides on how to configure it best so hopefully I can explain my intended usage and get some opinions on the best way about it. 

There is a 300gb OS drive, currently a single 2tb WD green with 3 more drives on the way in the next week or so. Hopefully I can do some of the legwork before they arrive as I have some free time at the moment. The machines accessing the server will be a combination of windows and linux computers, and media devices such as my PS3, tablets, phones etc.

I do a lot of 3d modelling/rendering, so there would be a fair amount of files on the server. Some of these can be fairly large files, especially when working on them. It would be awesome if I could set it up to have a projects area, and a library area which would contain assets that I use often. The projects area would be where files are stored that I work on, essentially only using local storage for temp storage such as writing out caches, etc. I guess in windows I would map a drive to my pc and work off that.

So without writing a giant wall of text, it would need to:

[LIST]
[*]act as a file server
[*]be able to stream media to ps3, tablet etc.
[*]be accessible with windows and ubuntu
[/LIST]

I've been reading [this guide]("http://linuxhomeserverguide.com/") which sounds promising, I like the idea of virtualising but have no experience with it (or setting up anything beyond a NAS). I also read in [another thread]("http://ubuntuforums.org/showthread.php?t=2198546&highlight=home+server+n54L") that this machine isn't really powerful enough to do it well. I also don't have too much of an idea on whether I need to set up a RAID, what sort of RAID etc. I think to sum up, I'm very green to all this and any help you can all provide is extremely appreciated!

1. RAID - if your files are precious, you probably want RAID. RAID allows for you to have hard disk redundancy so that if a drive fails (only in RAID 1 and higher levels, not including JBOD which isnt even RAID), your data will not be lost. There are a few RAID levels, each requiring a different number of drives, and having a certain amount of redundancy

2. Virtulization - I reccomend a OS called Proxmox, which provides you with a web interface to configure virtual machines. However, if you want RAID, you will have to configure debian with RAID, and then install proxmox with packages.

3. Streaming Media - Plex comes to mind

4. Fileserver - SAMBA or FREENAS if your using virtulization

---

### Post by ally2 on 2014-03-13
[http://linuxplanet1.blogspot.co.uk/](http://linuxplanet1.blogspot.co.uk/)

Keep checking this i'm also new to Ubuntu everything I learn is going on there :)

---

### Post by carlo3 on 2014-03-14
Thanks for the info guys, slowly putting together the pieces and figuring out how it's all going to work together. I'll keep this thread updated as I progress too. This whole project is also for me to learn more about how to set up and maintain a server even though it's only a small home one.

Some things I'm currently unsure of: 
[LIST]
[*]Some guides use ZFS, some use LVM. I've only got 2GB of RAM so ZFS sounds like it's out the question but LVM i'm finding difficult to wrap my head around, especially as I'll want to set up a RAID once my remaining drives arrive. Is LVM even the file system, or is LVM a thin layer on top of the file system?
[*]Virtualising. Does this happen inside my ubuntu server install?
[/LIST]

Some of the guides I'm referencing below (as well as lots and lots of forum searching): 

[http://blog.pendles.com.au/2013/04/hp-microserver-linux-box.html](http://blog.pendles.com.au/2013/04/hp-microserver-linux-box.html)
[http://amirshk.com/blog/linux-home-server/](http://amirshk.com/blog/linux-home-server/)
[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

---

### Post by bab1 on 2014-03-14
> **carlo3 said:**
> Thanks for the info guys, slowly putting together the pieces and figuring out how it's all going to work together. I'll keep this thread updated as I progress too. This whole project is also for me to learn more about how to set up and maintain a server even though it's only a small home one.

Some things I'm currently unsure of: 
[LIST]
[*]Some guides use ZFS, some use LVM. I've only got 2GB of RAM so ZFS sounds like it's out the question but LVM i'm finding difficult to wrap my head around, especially as I'll want to set up a RAID once my remaining drives arrive. Is LVM even the file system, or is LVM a thin layer on top of the file system?
[*]Virtualising. Does this happen inside my ubuntu server install?
[/LIST]

Some of the guides I'm referencing below (as well as lots and lots of forum searching): 

[http://blog.pendles.com.au/2013/04/hp-microserver-linux-box.html](http://blog.pendles.com.au/2013/04/hp-microserver-linux-box.html)
[http://amirshk.com/blog/linux-home-server/](http://amirshk.com/blog/linux-home-server/)
[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

I don't think you should consider RAID at all.  If you want to protect the data then you need to have a method to BACK UP your data.  RAID is for high availability not for data protection at all.  I back all my data up on external disks.

LVM2 is a layer of abstraction that allows you to combine multiple physical disks (the hardware) into what appears to the OS as one large partition (the logical space).  You then can format the single partition with a file system (EXT or some such).  I have a NAS that uses LVM2 to combine three 2TB disks.  LVM2 allows you to add additional disks easily if you need more space.

[Here]("https://www.google.com/search?q=lvm2&btnG=Go!") is some info on LVM2

I don't see any need for using virtualization.  In your case it won't add anything to your user experience, but it certainly will add complexity to the install and maintenance.

As you can see there is more than one way to implement what you wish to accomplish.  Think about it some more and ask more questions.

---

### Post by ally2 on 2014-03-14
[http://www.techexams.net/forums/off-topic/87323-one-linux-guys-initial-server-configuration-best-approach.html](http://www.techexams.net/forums/off-topic/87323-one-linux-guys-initial-server-configuration-best-approach.html)

Read this there is a good easy to understand explanation of LVM :)

Also LHammonds a member of this forum has decent tutorials 

[http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191)

---

### Post by carlo3 on 2014-03-14
Had a good read and look through the posts/links and I feel like I'm starting to understand it better now. Sitting here and planning it with pencil and paper has helped a lot, I do have a few more questions though! 

I've flashed my N54L with the modded bios to enable another HD over the ODD sata port so I'll  hook up the 250GB drive to this for the OS, and the 4 bays will each have a 2TB drive.

Thinking about how it'll be set up, in windows I would probably just have 4 separate drives as F, G, H, I (or whatever letters):

[LIST]
[*]Work (project folders)
[*]Media (tv, film, music etc.)
[*]Library (textures, assets etc.
[*]Mirror of Work
[/LIST]

This way, if one disk fails I still have everything else. I'd back up Media and Library occasionally to an external drive over e-sata too but they aren't as important and if they were lost the world wouldn't end. I guess the setup above would also mean streaming media wouldn't use the other drives unnecessarily.

Thinking in LVM terms would each one be a logical volume with all 4 physical volumes being set up as one volume group? I like the idea of this because I can allocate space better. If I steer clear of RAID though what happens if one of the physical volumes fails. I've had disks fail on me in the past, so with this much storage I'm quite keen to have as much redundancy as possible. [This image]("http://www.helios.de/support/manuals/vsa-e/LVM.png") is a good example of what I mean, if disk 4 goes then from what I understand that means I've lost the data in the whole volume group?

---

### Post by lukeiamyourfather on 2014-03-14
I'd take another look at ZFS. It's perfect for what you do (multimedia, rendering). If you're worried about memory for ZFS you can stuff 8GB or 16GB of unbuffered ECC memory in there. I'd configure the pool as RAID Z and then setup filesystems for each purpose (media, work, etc.). Each filesystem would share the underlying storage pool. Reasons why ZFS is perfect for what you do: adaptive replacement cache (ARC), block checksums (better data integrity), snapshots, high performance compression, super easy management. There are a lot of other reasons but you've already done some reading about ZFS it sounds like.

---

### Post by carlo3 on 2014-03-15
I've been taking another look at zfs from the information you posted luke and it sounds like this is going to be the way I go. The way you described the hierarchy of filesystems makes complete sense. I'll have to pick up some more ram for the server to be safe, but as I won't be using any of the advanced features like dedup or compression I'm hoping 8GB will be enough. 

I now have Ubuntu server installed on my 250gb hdd on an ext4 filesystem. The drive is partitioned using lvm and I followed lhammonds guide loosely to achieve this as well as everyone else's links they posted so thanks to all. 

Next thing to do is wait for my remaining drives to arrive before tackling the zfs filesystem and getting the shares all up and running.

---

### Post by ally2 on 2014-03-16
[http://www.latentexistence.me.uk/zfs-and-ubuntu-home-server-howto/](http://www.latentexistence.me.uk/zfs-and-ubuntu-home-server-howto/)

---

### Post by carlo3 on 2014-03-24
So updating this thread, I have now got my server up and running using ZFS. 

I was only able to get 2 x 2tb drives for the time being, so I have decided to mirror them while I get everything working. In the near future when I am able to buy another 2 I'll set it up as RAIDZ and that should be that. I read I'll have to destroy my pool and rebuild but there shouldn't be a lot of data to move over at that point so I think it'll be ok. Back ups are going to be taken care of with a 3tb external drive, I'll copy specific folders over a few times a week. This is probably the simplest set up for me while giving me peace of mind with my data.

Some things I stumbled over while setting it all up were:


[LIST]
[*]Has issues setting up the initial zpool, had to end up using the -f flag but everything worked ok. I think this was due to the mismatch of drive manufacturers but that's just a guess really, everything seems to work properly
[*]I went with a mirrored zpool, breaking it up into 3 filesystems /work, /media, /library. I didn't set a quota for any as I have no idea how much they will contain eventually
[/LIST]

[LIST]
[*]Setting up samba via the ZFS command **[COLOR=#ff0000]sudo zfs set sharesmb=on[/COLOR]** seemed easy, but I had problems with permissions. I set up 2 user accounts for samba and spent ages editing the samba config file but that ended up giving me doubles of all my shares (could see the ZFS filesystem share and the share from the config fille) and I still had permission problems. I got it working by chmod each of the filesystem roots with 777 but I know this is a bad way to do things. I could not get this command to work **[COLOR=#ff0000]sudo chown -R user:user *[/COLOR]**and I wasn't sure if a directory can have more than one owner anyway.
[/LIST]

The next thing I would like to do is set up the Plex media server, but first I will try to get my shares working properly without the whole filesystem chmodded to 777. If anyone can point me in the direction or has any solution to it that would be great.

EDIT: thinking about it, there's no reason for sharesmb to actually be on. I can let the samba config file take care of my shares and there won't be any doubles. Answered my own question there lol

---

### Post by carlo3 on 2014-03-26
Making good progress with this project now, I now have my Samba shares working properly as well as Virtualbox installed.


The Samba shares got really confusing, on reboot I would lose my share and have to use the command [COLOR=#ff0000]**sudo zfs set sharesmb=on /path/here/**[/COLOR] to see it again. I ended up turning all shares off through ZFS and setting up my Samba config file properly. It's all working great now, with the correct permissions too so no 0777 set anywhere.


Installing Virtualbox was a lot of hassle, mainly due to my lack of permissions understanding coming from Windows where I just don't think about these things. I got it installed but couldn't get it to run under a user account created specifically for it, yet the main user acc could run it with no troubles.


In the end it was down to my new user not having ownership of their own /home/username/ folder, not being in the correct vboxusers group and not having sudo access. Once I'd set that correct all was working, I even managed to get phpVirtualbox installed without too much trouble afterwards.


The next steps are to create a VM for Plex and Subsonic, and one for a LAMP stack + Deluge to download tv shows. I am debating whether to install ownCloud, it looks like it could be a nice way to access files externally and be useful for the other half too.

---

