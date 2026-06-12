---
title: "mdadm softraid thoughts"
date: 2009-10-14
forum: Server Platforms
---

### Post by epsolon77 on 2009-10-14
I am looking for peoples opinions that have actually used mdadm for a softraid setup.  I understand that hardware RAID is the preferred method, but I am having trouble finding cards that are adequate for me (number of drives, hot spare capability and cost are all major factors).  The server I would be setting this up in would have at least 7 SATA drives (two pairs of 3 with 1 hot) and would do nothing other than manage the raid and ISCSI protocol. 

1. Is it reliable?  
2. Are you required to take the array offline before adding a new hot spare and removing the old failed drive?  
3. Is there a way to automatically provision and integrate a newly added hot spare to the array?  
4. Are there any web based management and alerting tools for mdadm that can be recommended? (SNMP alert works just fine)
5. Do you feel mdadm is acceptable to be used in a small production environment.  We seem to be too big for a standard SAN system backed up by tapes, but are too small to justify the expense of an Equilogic type system.

---

### Post by laluz on 2009-10-22
1-3 I guess nobody answers you because you could just RTFM and try yourself. It would be a right thing to try to restore and exchange hot spare yourself anyways.
5. People keep saying RAID is no substitute for backup not for no reason. It helps you to keep your production running in most cases, but not all of them. And once your system is destroyed for whatever improbable event, you'd be happy to have backup.

---

### Post by fjgaude on 2009-10-22
Well, over the years **mdadm** has been totally reliable if you always follow the rules of the road. Read the **man mdadm** pages to realize just how complex software raid can be.

You can have hot spares and the software is just about perfect, so... some reading material:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://www.antunkarlovac.com/blog/20...ux-raid-array/](http://www.antunkarlovac.com/blog/20...ux-raid-array/)
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Have fun!

---

### Post by epsolon77 on 2009-10-23
fjgaude thank you for your intelligent and open minded response.  I am looking a little outside the box here when it comes to using a RAID system, which is actually why I want to use a softraid as opposed to hardware raid and would love your opinion.  I would have two ISCSI targets with MDADM raids at two sites keeping each other in the loop.  I know how complex RAIDS can be, that is exactly why I am seeking other people opinions.  I currently am cut off a little because I have no test hard drives, so playing with MDADM is not really a current possibility.  Any thoughts?

Before I go any further, I have RTFM, and RAID arrays are commonly used in conjunction with one another to create a self backup system when tapes can no longer economically hold the amount of data you need.  I would prefer intelligent responses, not belittling close minded assumptions based off technological information and preference from the previous decade.  I get the people prefer tape backups, but our current full tape backup runs for 20 some hours, and that is just not acceptable.

---

### Post by fjgaude on 2009-10-23
Okay, the two sites would be synced-up with something like an **rsync** script. Each site would be identical, one backing-up the other? No, one server would have the two raid arrays?

I can't see why mdadm in raid5 pairs each with its own hot spare wouldn't do the job. I have no experience with ISCSI but can't why that protocol has anything to do with the raid setups.

---

### Post by epsolon77 on 2009-10-23
Rsync is a great option for the link.  The two physical system would be not only in different physcial machines, they would be in different locations.  My initial thought is to have a dedicated file space for the other systems backup.  If I read the MAN right this would not be a live script running 24/7, but rather a nightly type task.  Which is great. 

Not to try and incur the wrath of the forum, but I was intending on using a RAID 10 setup instead of a RAID 5, because it should take fewer resources to rebuild the RAID 10 array after a failure event, which becomes important if the rebuild would be initialized during business hours.  
**For those out there that are big supporters of RAID 5, yes it works great, I'm not saying it's bad, just don't think it's preferable in this case.  If you disagree, please state your case!**

---

### Post by epsolon77 on 2009-10-23
> **fjgaude said:**
> I have no experience with ISCSI but can't why that protocol has anything to do with the raid setups.

The ISCSI protocol really doesn't have much to do with the RAID array, other than they will be on the same system, and you never know where and how a complication could arise.

---

### Post by djamu on 2009-10-23
Hi there,
since fjgaude provided you already with some useful links ( and has a trustful opinion ) I'll just ventilate my own experiences, alternates etc...

> **epsolon77 said:**
> 
1. Is it reliable?  
2. Are you required to take the array offline before adding a new hot spare and removing the old failed drive?  
3. Is there a way to automatically provision and integrate a newly added hot spare to the array?  
4. Are there any web based management and alerting tools for mdadm that can be recommended? (SNMP alert works just fine)
5. Do you feel mdadm is acceptable to be used in a small production environment.  We seem to be too big for a standard SAN system backed up by tapes, but are too small to justify the expense of an Equilogic type system.

1. yes absolutely > given that you have server grade hardware supported by the OS.
2. No in general not, but keep in mind you have to differentiate between cold- / hot swap, cold swap requires you to tell mdadm that you're about to remove a HD from the array ( without getting it offline ) and then yank it out. Also if your HD's are powered with or via a Molex adapter ( the 4 pin/wire ones ) hotplugging (attaching) disks is not advisable without powering off the server ( the 5th pin > 3.3V supply ) can supply a sense function. 
The layout of the 15pin connector arranges a staggered power supply connection ( it makes sure  that ground 0V connects before any live voltage -connects first / disconnects last ) > In other words if you insist on using molex adapters to 15 PIN > Use the 15 Pin to connect and disconnect.
Lastly you OS needs to use AHCI ( linux does by default ), but make sure it's enabled in your mobo BIOS

more specs > [http://en.wikipedia.org/wiki/Serial_ATA]("http://en.wikipedia.org/wiki/Serial_ATA")

3. It's supported by madam > spares can be arranged in pools
4. mdadm supports e-mail notification
5. It sure does ( was this a real question?  )

> **epsolon]
fjgaude thank you for your intelligent and open minded response. I am looking a little outside the box here when it comes to using a RAID system, which is actually why I want to use a softraid as opposed to hardware raid and would love your opinion. I would have two ISCSI targets with MDADM raids at two sites keeping each other in the loop. I know how complex RAIDS can be, that is exactly why I am seeking other people opinions. I currently am cut off a little because I have no test hard drives, so playing with MDADM is not really a current possibility. Any thoughts?
[/QUOTE]

1st. Whenever someone tells you softraid is less performant then hardware raid, I can assure you that they have no idea what they are talking about ( unless the server load is near a constant 100% from other applications, in that case use a Zero-raid controller in conjunction with normal sata expansion cards > Zero raid controllers don't have any connections but offload other COTS cards 

2nd. Virtualization allows you to "play" with as many disks as you like > install vmware / virtualbox / xen whatever > create a couple of disks and go berserk ....


[QUOTE=epsolon]
Before I go any further, I have RTFM, and RAID arrays are commonly used in conjunction with one another to create a self backup system when tapes can no longer economically hold the amount of data you need. I would prefer intelligent responses, not belittling close minded assumptions based off technological information and preference from the previous decade. I get the people prefer tape backups, but our current full tape backup runs for 20 some hours, and that is just not acceptable.
[/QUOTE]

I second that, tapes are way to slow, if you need to backup +8TB...
Use a spare ( old ) server with RAID for that ...  > I'll recap some options later on.

**Rsync ?**
**iSCSI ?** 
**Replication?**

> I hope you do realize that iSCSI is not a fileserving protocol > ( works the opposite from SMB/NFS actually, aside from being a block-device )  
SMB/NFS > single server / multiple clients  
multple iSCSI storage devices ( targets ) > single client ( initiator ).

In other words It's use is to concatenate a bunch of storage devices for 1 client ( the initiator ) which can then act as a fileserver in itself ( SMB/NFS )
**do not** connect with multiple initiators to the same target ( the storage device ) file corruption will occur as iSCSI doesn't feature any kind of filelocking ( on a blocklevel / blocklocking ? :confused: lol ) 

This means that as soon as you start with iSCSI devices, you don't need rsync etc ..( file replication ), but you need a block replication mechanism ( easy as pie > read on )...



**Quick example** of storage backup replication with 2 iSCSI servers these can be in remote locations since iSCSI uses the TCP protocol > data can travel over the internet. 

needs 3 servers. 
2 iSCSI servers ( targets ) that hold the data / HD's, each configured as  RAID5/6 ( & spares yada yada ) 
1 fileserver ( the initiator ) that provides the contents of both iSCSI devices to clients ( SMB/NFS ) on your local network...

Since an iSCSI device is just another block device like an ordinary HD, you can use RAID1 for that....  
Mount both iSCSI devices on the fileserver ( the initiator )  and create a RAID1 ( mirror ) from them > format it with the FS of your liking and your set .... no rsync needed .... 
If you need an additional backup > add another ( iSCSI ) device as RAID1 > remove that device when done ( mdadm --fail --remove as usual )

This is the way I backup live systems (remote RAID1 volumes ), and is also ( by far as I know ) the only / easiest way to handle live databases.

> related example 

server with database that needs backup ...
1. > create an empty file on a remote fileserver for which this file has the same size as the partition you want to backup ( use DD ) 
2. > mount the remote share with either SMB/NFS/STFP 
3. > mount that empty file on computer you are about to backup as a loopdevice so it becomes a device 
4. > add loopdevice ( aka empty file ) as a RAID1 mirror of the partition/array you want to backup 
5. > let it resync 
6. > remove RAID1 loopdevice
7. > unmount loopdevice
8. > unmount share
(I use a small script for this)

if you are using iSCSI for this > replace steps 1 / 2 / 3  with mounting the remote iSCSI device.
this way you get a perfect copy ... even if the partition has a database on it...

FYI > RAID1 devices can have more then 2 devices .... and have no problem running degraded ( without the remote mirror )  said:**
> http://en.wikipedia.org/wiki/DRBD[/URL]


**important!**
if you want good performance and efficiency here's a couple much overlooked settings ( applies to ext3/ext4  )
Since both come with journaling, efficiently striping that across a RAID array can dramatically improve performance. ( also seriously consider using a 2.6.30 kernel with latest e2fsprogs when using ext4 ... > I can provide you those debs for debian 

so instead of 
```
sudo mkfs.ext4 /dev/md0 ( or the remote iscsi device )  
``` 

do ( read explanation! don't copy & paste )
```
 sudo mkfs.ext4 -E stride=96,stripe-width=16 -m0 /dev/md0 
```

stripe= raidblocksize / ext4 blocksize > raidblocksize=64k ( default ) ext4 blocksize=4k ( default ) > stripe = 16
 
stride = stripe * active disks > acive disks = amount of disks without parity & spares > a raid5 array with 7 disks has 6 active disks / raid6 with 8 disks and 2 spares  has also 6 active disks 

so the stride value for a raid6 array with 8 disks and stripe= 16 > stride = 96

-m0 > makes sure there isn't any wasted superuser disk space ( default = 5%) , there's no need to reserve this much space on a storage device

at home ( I  do high end 3D ) my work fileserver runs on a pentium-D >  6TB RAID6 with 8 disks and 1 spare
read performance with default settings ( raidblock 64k / ext4 block=4k ) = 552MBs sustained read on a 200GB file, write = 460MBs ( raid6 needs 2 write cycles for the dual parity )
no need to say this easily saturates my channel bonded Gb network.... :-\"

I have another one with a 10 disk raid5 array  running for 4 years now that I use for my backups... 
and have numerous installations that ( mostly) run flawless

Just 1 last advice, mdadm doesn't really like sudden shutdowns ... as it might start to resync > your raid is vulnerable at that time... 

Also keep in mind that mdadm will do a resync / check every 1st sunday of the month at 1AM ( reschedule  1 server on another day >  do not let both iSCSI resync simultaneously ) 


[QUOTE]
Not to try and incur the wrath of the forum, but I was intending on using a RAID 10 setup instead of a RAID 5, because it should take fewer resources to rebuild the RAID 10 array after a failure event, which becomes important if the rebuild would be initialized during business hours. 
**For those out there that are big supporters of RAID 5, yes it works great, I'm not saying it's bad, just don't think it's preferable in this case. If you disagree, please state your case!**


sorry to say but this is nonsense ... one does not make either one or the other out of personal preference ( as you suggests ), but because of needs... a RAID1 is (should be ) used when high concurrent access is needed ( lots of small files that needs to be accessed simultaneously ), a RAID0/5/6 when fewer files needs faster access,  RAID 5/6 if redundancy is needed  .... ( RAID 0 / 5 / 6 are all striped arrays RAID 1 is mirroring > RAID10 / 01 ( yes there's a big difference ) is just a tradeoff between striping and mirroring...
rebuilding a RAID5/6  takes just a tiny bit more resources... just consider the fact that your HD's are the bottleneck and not your CPU...
on top of that, if you mirror both iSCSI devices ( either RAID5/6 ) > you effectively have a RAID 15 / 16 .....  if you stripe those you have a raid05 / 06  or you could RAID5/6 a couple of striped devices creating RAID50 / 60 or ..... raid5 a couple of raid5 iSCSI devices ....  or .... 
these setupss are pretty common in very large storage facilities ... I'm not kidding 

just toy a bit with virtualized setups -as I said before- to get used to this kind of technology ... I strongly advise that you take a look at LVM, and use it to virtualize ( detach storage from the physical layer ) your storage devices ( LVM on top of RAID on top of iSCSI on top of RAID )  ...

Also take a look at AoE and NBD as lower overhead replacements for iSCSI

and by all means make sure there's no way you can get at any point a split brain situation ( a situation where both mirrors lose connectivity with each other but not with the rest of the network )... data corruption will be yours then ...


my 5 cents  

Jan

:KS

P.S. > if you ever run into troubles > there's a bunch of posts related to RAID5/6 from me on this forum.

---

### Post by windependence on 2009-10-23
I prefer hardware RAID for reasons I have stated before, so I don't want to get into a flame war because no one here (especially) is going to change their minds. After working for several Fortune 100 and 500 companies I can tell you that you will not find software RAID in those companies. Take from that what you will. 

As for your question, try an Adaptec 2820SA and that should solve your problem. Supports 8 drives in many RAID configurations, easy to set up, drives are hot swappable, and the controller is real hardware RAID and is supported under VMware if you need to virtualize.

-Tim

---

### Post by djamu on 2009-10-24
> **windependence said:**
> I prefer hardware RAID for reasons I have stated before, so I don't want to get into a flame war because no one here (especially) is going to change their minds. After working for several Fortune 100 and 500 companies I can tell you that you will not find software RAID in those companies. Take from that what you will. 

As for your question, try an Adaptec 2820SA and that should solve your problem. Supports 8 drives in many RAID configurations, easy to set up, drives are hot swappable, and the controller is real hardware RAID and is supported under VMware if you need to virtualize.

-Tim

Don't intend a flame war either, but this isn't what OP asked and needs, FYI I have to been using HW raid's too. ( what's that "especially " ? )

situation:
-small setup, most likely small company with a few offices
-amount of data to large for tapes, and to small to justify the pricetag of EMC / related products. > cost was a major factor

cards:
Supermicro is a good alternative for adaptec and their SAS/SATA line of products are server grade > both for soft/hardware raid with a lower then average pricetag ...
He could then go for a an ordinary multichannel SAS HBA card ( and sata splitters)  and add ( if the situation justifies it ) a zero-raid controller > or a real SAS/SATA HW Raid card.


I'm not affiliated just a happy customer >

2 cards that might be a good fit HBA only / softraid support > 
[http://supermicro.com/products/accessories/addon/AOC-USAS2-L8i.cfm?TYP=E](http://supermicro.com/products/accessories/addon/AOC-USAS2-L8i.cfm?TYP=E)
an older one 
[http://supermicro.com/products/accessories/addon/AOC-USAS-L8i.cfm](http://supermicro.com/products/accessories/addon/AOC-USAS-L8i.cfm)

if needed ( 1st one ) you can easily compile a driver for your favorite OS flavor

complete line of products
[http://supermicro.com/products/nfo/storage_cards.cfm](http://supermicro.com/products/nfo/storage_cards.cfm)

---

### Post by epsolon77 on 2009-10-24
Thank you everyone.  While I did not ask specifically about hardware raid, the input will be seriously considered.  I am not sure what I will have as far as budget is concerned, which is why I am looking for a way to do this as a soft raid.  

Windependance I am not trying for a flam war either, so please if anyone else responds, keep it factual and as unbiased as possible. "Software raid sucks because I slept with your mamma last night" doesn't help anyone.

In my experience companies choose hardware raid because soft raids got a bad rap when processing power was limited, and frankly, most software raids I have seen were on windows systems that were already resource strapped, and naturally they fail.  That is why I am dedicating the machine to this raid, and not virtualizing it or really anything else.  I would not have a software raid on any of my servers that have other functions.  For instance our mail server, runs exchange, not a raid, the hardware raid card does that, but I hope that running a software raid on it's own box should eliminate a ton of expense, and allow for drive consolidation across all my servers.  As always, *please* disagree with me, this is how people learn.

djamu--that is great info on iscsi and hot swap hardware requirements.

I have one questions.  You said that there is a 1 to 1 relationship with iscsi server to client.  This is why I want iscsi, to keep the data control OFF this box.  However if I remember correctly, a single OS can host multiple iscsi targets, and the 1 to 1 relationship you spoke of refers to the disk space.  What I don't remember is if the target OS is required to see the drive portion as a logical partition.  So, you should be able to have 3 iscsi targets run off one OS and one drive, that has been partitioned into several groups.  Each group would be locked to one iscsi target, and one iscsi client.  So that 500gb block is dedicated to iscsi target and client 1 and can not be used by target and client 2 unless it is first released from target 1.  I hope this makes sense.

---

### Post by windependence on 2009-10-26
> **djamu said:**
> Don't intend a flame war either, but this isn't what OP asked and needs, FYI I have to been using HW raid's too. ( what's that "especially " ? )

situation:
-small setup, most likely small company with a few offices
-amount of data to large for tapes, and to small to justify the pricetag of EMC / related products. > cost was a major factor

cards:
Supermicro is a good alternative for adaptec and their SAS/SATA line of products are server grade > both for soft/hardware raid with a lower then average pricetag ...
He could then go for a an ordinary multichannel SAS HBA card ( and sata splitters)  and add ( if the situation justifies it ) a zero-raid controller > or a real SAS/SATA HW Raid card.


I'm not affiliated just a happy customer >

2 cards that might be a good fit HBA only / softraid support > 
[http://supermicro.com/products/accessories/addon/AOC-USAS2-L8i.cfm?TYP=E](http://supermicro.com/products/accessories/addon/AOC-USAS2-L8i.cfm?TYP=E)
an older one 
[http://supermicro.com/products/accessories/addon/AOC-USAS-L8i.cfm](http://supermicro.com/products/accessories/addon/AOC-USAS-L8i.cfm)

if needed ( 1st one ) you can easily compile a driver for your favorite OS flavor

complete line of products
[http://supermicro.com/products/nfo/storage_cards.cfm](http://supermicro.com/products/nfo/storage_cards.cfm)

The OP made this statement to which I was responding:

> I understand that hardware RAID is the preferred method, but I am having trouble finding cards that are adequate for me (number of drives, hot spare capability and cost are all major factors).

People often say hardware RAID is too expensive for them because they assume that without really checking. As you have pointed out (and I am actually grateful to you for the info) hardware cards are not always cost prohibitive and if I can use hardware RAID I will do it every time I can over softraid. 

The "especially" is because although this is supposed to be a "server" forum, it seems it's more a discussion about torrent boxes and such which I don't define as "servers" per se looking at the description of this forum. Ubuntu makes a server distribution which is really and truly geared to server class hardware in data centers, and I had thought that was what was to be discussed here. Apparently not, and it's frustrating. If not here, then where? Almost without exception when RAID is discussed here, it is software RAID which won't normally be found in a production data center at all. I don't know about you, but I wouldn't want to be the one to tell my boss that my softraid crashed and the server will be down until I can restore from backup. That's real world. If you're using it for your torrent box then go for it, and he has already gotten the best advoce he can from fjgaude who is what I consider to be a softraid expert.

At any rate, I appreciate your information on SuperMicro who's products I use all the time.

-Tim

---

### Post by djamu on 2009-10-26
> **epsolon77 said:**
> 
I have one questions.  You said that there is a 1 to 1 relationship with iscsi server to client.  This is why I want iscsi, to keep the data control OFF this box.  However if I remember correctly, a single OS can host multiple iscsi targets, and the 1 to 1 relationship you spoke of refers to the disk space.  What I don't remember is if the target OS is required to see the drive portion as a logical partition.  So, you should be able to have 3 iscsi targets run off one OS and one drive, that has been partitioned into several groups.  Each group would be locked to one iscsi target, and one iscsi client.  So that 500gb block is dedicated to iscsi target and client 1 and can not be used by target and client 2 unless it is first released from target 1.  I hope this makes sense.

mmm not really 
I made / attached a small graph to illustrate a typical small iSCSI setup ( without failover capabilities ) > use DRBD for that  > [http://en.wikipedia.org/wiki/DRBD](http://en.wikipedia.org/wiki/DRBD)
and try to use the correct terms because some components in this setup are both client and server 
( I've added the most common functions / possible synonyms ) 


now my dear Tim ( windependence ), it may well be that quite a lot of those Fortune 100 and 500 companies in the USA are allergic to softraids, but In europe my governement  (which pays a substantial portion of my consultancy fees ) and their datacenters use software raids very frequently even for their most critical servers > the idea behind this is > less components means a better MTBF ...and higher portability,  do you see the logic here ?

I don't frequent this forum often, because I still have to see the 1st deployment of ubuntu in one of their centers > in contrast to debian ( which has uptodate IDS packages ) and sun deployments...

Now you seem to be offended by all those home users here who want to get some kind of ( stable ! ) redundancy that doesn't cost them a single penny... 
 
I'm not someone who likes to belittle someone, but may I remind you that I was the one who explained the difference between EVMS / LVM to you, and since you failed to see that your highly acclaimed  Frank said something rather.... mmm well .... stupid ( I didn't mind, but rsyncing iSCSI devices is ....impossible > iSCSI's are block devices )  Now that makes you ?  Certainly not all-knowing 

The only reason I frequent this forum is to help people in my rare spare time, and I agree that some questions here will never be answered....

But not having thousands of posts doesn't make me less proficient, I consider myself a real specialist, who is able ( and takes time ) to explain stuff in the most simplistic manner so every beginner can understand, and have never lost a single byte on the dozens of HW/soft raid arrays   I manage ( torrentboxes :rolleyes: lol )

If you're that unhappy why don't you join the debian forum > they only talk about servers ... Dom0 and DomU galore ....


bye

---

### Post by epsolon77 on 2009-10-26
I am not using this a torrent server.  This is an "enterprise" enviorment.  I feel though that most people's deffinition of a business class computer network is a little narrow.  We have 6 servers, running windows server 2003 and need an external storage solution.  Something akin to a SAN box.  However I have been very put out by most storage solutions.  The SAN/NAS solutions I have worked with in the past were always a bit flakey, and there was nothing you could do to fix them, or they were not expandable or customizable, so I couldn't do what I needed to with them.  Instead I would have to tailor my network to it's needs.  I'm not up for that.  The only equipment I have been impressed with is the Equilogic (now owned by Dell) PS series of arrays.  They have hot swap drives, I belive up to 10, and work as ISCSI targets.  I am almost certain we are not going to be able to swing that kind of money though, so I need another option, hence softraid.  I have looked into pricing on hardware raid cards, an up until the comment on the Adaptec card I had not found a potential card for an approachable price.  

You speak of restoring from back up if the softraid OS fails, but how often does your core OS fail.  This is one of the main reasons I mentioned that this box would do NOTHING other than manage this storage.  And by Nothing, I mean it may not even have internet access.  Also, if the OS is created and stable, in the event of a hardware failure involving the OS main drive, it shouldn't take long to restore that backup right?  (yes I've restored OS's from backups)

Again I have only been doing IT for about 5 years, and I don't know everything, which is why I am asking.  We can't spend thousands on this project, and we need the storage badly.

I'm sorry if this post sounds belligerent, but the information being provided is great and deserves prompt replies, but then again I'm at work and severely distracted.

---

### Post by epsolon77 on 2009-10-26
djamu thanks for the info I'm going to have to rethink the iscsi portion of this.  It's been a long time since I have functionally used iscsi.

I think what windependnce is getting at, is that there are a lot of people that call their home file share a "server", case in point is the Windows Home Server OS, which really isn't a server in the business sense.  I think he is very accustomed to the American IT department model which is not traditionally rooted in flexibility, but rather redundancy.  I've actually had debates similar to this one.  It always seems that our European brethren have a distinctly different taste for network setups than we commonly see in America.  The perfect example is here.  Yes most fortune 500 companies here in America have classic data centers, with racks upon racks of branded equipment all functioning on 24x7 support plans from the vendor and a team of IT pro's to feed info to the vendors and enact a repair while the redundant system takes control.  It seems across the "pond" that companies are favoring inexpensive systems that are highly portable and IT pro's that really do it all, relying on vendor support as a last line of defense.  Does this sound accurate?  For some reason each of the projects I'm working on it seems someone from America says "this isn't how corporate networks work" and someone from europe says "yeah I did something similar last week"!  I guess I'm just on the wrong continent.

---

### Post by djamu on 2009-10-26
> **epsolon77 said:**
> 
snipsnip .....

  It seems across the "pond" that companies are favoring inexpensive systems that are highly portable and IT pro's that really do it all, relying on vendor support as a last line of defense.  Does this sound accurate?  For some reason each of the projects I'm working on it seems someone from America says "this isn't how corporate networks work" and someone from europe says "yeah I did something similar last week"!  I guess I'm just on the wrong continent.

You're a funny one,  I'm quite surprised,  pretty  accurate actually.  -google does this too btw > instead of a couple big irons > a whole bunch of COTS machines- 

There is of course another less obvious consideration, politics and the dependency from american oriented vendor support,  the continuos monitoring of ... well you know .. couple that to crippled encryption on US products and our freedom to use the strongest encryption imaginable ( except for france ) . Specifically  government issued centers are prone to that policy ( all documents must be stored & archived in an opensource format for example ) 

now as a bonus :popcorn: 

maybe you could try something like this then, .... ( I've been torture testing this setup for over 6 month's now.. and all is well )

it's kind of unorthodox, but it reduces the amount  of (OS) disks and hence point of failures, works blazing fast ...and allows -as a bonus- almost instant deployment, -most OS's don't even need to be backuped-

Test rig : 
6  ( i7 920)  compute nodes as smb client  > 1 computer as  iSCSI initiator with PXE  /TFTP / DHCP / SMB services > 2 computers iSCSI targets each with a raid5 3*500GB 

the SMB clients and the iSCSI targets don't have any OS disks / partitions > targets only have storage ...

the iSCSI initiator has 2x OCZ SSD's as RAID1 ( use the SLC SSD's not the MLC ( MLC are the ordinary ones, be sure to look up the difference )... they don't come cheap but are nearly indestructible  > I used these > [http://www.ocztechnology.com/products/solid_state_drives/ocz_vertex_ex_series_sata_ii_2_5-ssd]("http://www.ocztechnology.com/products/solid_state_drives/ocz_vertex_ex_series_sata_ii_2_5-ssd")

These SSD's are much faster then any other HD (including WD Velociraptors ) and have a near zero seek time ( 0.08ms > 90 x faster then the WD velociraptor >7.2ms ).
I just saw that they now have PCI-E based SSD's ( SLC ) > 
Read: Up to 800MB/s   
Write: Up to 750MB/s    

woooot 

I've crammed the 2 whole Os's for both the compute nodes and targets into 2 initramfs files CPIO compressed 150MB ( I use them to boot the whole OS instead of bootstrapping it,  resides completely in RAM on the client computers ( unpacked a little under 400MB)  and those get served by DHCP / PXE /TFTP ( I'm still trying to build a torrent tracker inside the initramfs and use that to use as a massive deployment means > deploying +10.000 computer out of a single server and a single image )... if you know how torrents works ... you'll get the idea...

in other words > the initiator provides the OS image for the targets > targets boot up with the OS residing in RAM > initiator connects to targets / mounts devices / starts serving a secondary image on the other NIC for the compute nodes /desktops / whatever ... ( images on the iSCSI targets ). 

This way only the initiator has an OS disk ... and the whole system is extremely portable..

try it, you'll be surprised ...

cheers

---

### Post by epsolon77 on 2009-10-26
I guess this kinda proves that I'm a nerd, but I think the thought of that storage system is going to give me some GREAT dreams tonight.  I think I'm actually drooling right now.

I love your concept of running the storage cluster on a PXE boot.  I would not need 10,000 storage boxes, but hey, we'll get there.  I'm going to have to chew this one over for a little bit and get back to you with a ton of questions...

To me it's almost like American companies are shooting themselves in the foot for not considering other options other than the ready made package deal.  I'm so sick of dealing with one point of failure, that I cant get to because it voids my warrentee is KILLING ME.  I feel that I need to be able to track everything that is going on in the network.  I need to be able to see and touch the phone call, the fax, the extension configs the server, the OS's packages, the backup set.  If I can't touch it all, I can't fix it all, and then what am I being paid for???  

I digress.  I will have some questions for you on your storage network before too long.  I need to go get my kid off the bus.

---

### Post by windependence on 2009-10-27
> **djamu said:**
> 

now my dear Tim ( windependence ), it may well be that quite a lot of those Fortune 100 and 500 companies in the USA are allergic to softraids, but In europe my governement  (which pays a substantial portion of my consultancy fees ) and their datacenters use software raids very frequently even for their most critical servers > the idea behind this is > less components means a better MTBF ...and higher portability,  do you see the logic here ?
No, I really don't. I seriously don't. I suppose you aren't virtualizing either? Lets forget about whether hardware RAID is more reliable than software RAID, one thing is clear. I can replace a simple card in 5 minutes, and I can configure my array in about the same amount of time. Let me see you do that with software RAID.


> **djamu said:**
> Now you seem to be offended by all those home users here who want to get some kind of ( stable ! ) redundancy that doesn't cost them a single penny... 
Not at all, I just think there should be a forum for "enterprise" servers or maybe a forum for "home" servers.
 
> **djamu said:**
> I'm not someone who likes to belittle someone, but may I remind you that I was the one who explained the difference between EVMS / LVM to you, and since you failed to see that your highly acclaimed  Frank said something rather.... mmm well .... stupid ( I didn't mind, but rsyncing iSCSI devices is ....impossible > iSCSI's are block devices )  Now that makes you ?  Certainly not all-knowing 
I think you have me confused with someone else. I don't ever remember even discussing EVMS anywhere here. If you post the thread, I'll shut up. FJ knows way more about softraid on Linux than I do. I DO run softraid on BSD, and it's quite stable, but there's a world of difference between the two.

> **djamu said:**
> The only reason I frequent this forum is to help people in my rare spare time, and I agree that some questions here will never be answered....
Ditto.

> **djamu said:**
> But not having thousands of posts doesn't make me less proficient, I consider myself a real specialist, who is able ( and takes time ) to explain stuff in the most simplistic manner so every beginner can understand, and have never lost a single byte on the dozens of HW/soft raid arrays   I manage ( torrentboxes :rolleyes: lol )
I can give you numerous examples of people who were helped by my answers. I don't expect anything in return, certainly not a "belittling" from you. How is this helping the OP. Good for you, your softraid never broke, so what does that prove?

> **djamu said:**
> If you're that unhappy why don't you join the debian forum > they only talk about servers ... Dom0 and DomU galore ....

bye

I've gone one better - I have belonged to the BSD forums for years - a much saner place where these types of bashings don't occur.

-Tim

---

### Post by windependence on 2009-10-27
> **epsolon77 said:**
> I guess this kinda proves that I'm a nerd, but I think the thought of that storage system is going to give me some GREAT dreams tonight.  I think I'm actually drooling right now.

I love your concept of running the storage cluster on a PXE boot.  I would not need 10,000 storage boxes, but hey, we'll get there.  I'm going to have to chew this one over for a little bit and get back to you with a ton of questions...

To me it's almost like American companies are shooting themselves in the foot for not considering other options other than the ready made package deal.  I'm so sick of dealing with one point of failure, that I cant get to because it voids my warrentee is KILLING ME.  I feel that I need to be able to track everything that is going on in the network.  I need to be able to see and touch the phone call, the fax, the extension configs the server, the OS's packages, the backup set.  If I can't touch it all, I can't fix it all, and then what am I being paid for???  

I digress.  I will have some questions for you on your storage network before too long.  I need to go get my kid off the bus.

This subject is probably better discussed in some other forum but Europeans have a different viewpoint in some cases than we do here in the states. having worked for several GLOBAL companies I can tell you ALL of the Europeans, Asians, and Aussies I worked with in the enterprise all did it the way we do here. I don't know what this guy is talking about.

Now, for some constructive ideas, take a look at FreeNAS, based on FreeBSD. I have a storage box built using FreeNAS where I store VMs, files, etc. and it can also easily act as an iSCSI target, NFS server, SAMBA server and much much more. Even has abuilt in torrent client. ;) It has been very stable for years.

-Tim

---

### Post by djamu on 2009-10-27
again, this is just because you claim no one in the industry uses softraid, as said before I consult for the government and the HPC (3D) industry and universities... 
but since you're asking for it..

> **windependence said:**
> No, I really don't. I seriously don't. I suppose you aren't virtualizing either? 

yes we do, and it's of no importance since iSCSI initiators rely on a network ( when using copper instead of fiber and there's no point in virtualizing iSCSI targets.

> 
...
 I can replace a simple card in 5 minutes, and I can configure my array in about the same amount of time. Let me see you do that with software RAID.

how about 1 minute with the setup I described above ( considering we both have spares parts )

> 
Not at all, I just think there should be a forum for "enterprise" servers or maybe a forum for "home" servers.
 
I totally agree on this one, I think moderation should be more stringent.. but I very much doubt this is ever going to happen > Ubuntu is much more geared toward desktop users and I don't see much a real professionals around here  ( according to a couple of questions I had that stayed unanswered )

> 
I think you have me confused with someone else. I don't ever remember even discussing EVMS anywhere here. If you post the thread, I'll shut up.

I don't ask that, and I do respect your efforts for the community, my point is that soft raid offers a very elegant solution for problems that are very hard / complex / expensive to solve in hardware, for example > replicating remote block devies ( as iSCSI targets ) with a ( temporary ) RAID1 array that you break ( where you remove 1 mirror ) after syncing...  this is easy with softraid ...

I have a good memory and had to go back a while to find that thread ... where you praised me for a remark, we chatted a little ... you might want to re-read it > [http://ubuntuforums.org/showthread.php?t=860288&page=2]("http://ubuntuforums.org/showthread.php?t=860288&page=2")

>  
I can give you numerous examples of people who were helped by my answers. I don't expect anything in return, certainly not a "belittling" from you. How is this helping the OP. Good for you, your softraid never broke, so what does that prove?

nothing, as said before I appreciate your efforts, and you should appreciate mine... just watch your language when you assume that only people with torrentboxes use soft raids, because some environments just work different over the "pond" .

> 
I've gone one better - I have belonged to the BSD forums for years - a much saner place where these types of bashings don't occur.

I never intended to bash you and I'm really sorry you feel that way, but you should not claim things, that are untrue.. your experience doesn't include everyone's... 

Showing consideration for other peoples opinion ( even if they are biased )  is a virtue.


Peace 

Jan

---

### Post by fjgaude on 2009-10-27
"Showing consideration for others people opinion ( even if they are biased ) is a virtue." - Jan

Well, Ubuntu is a little late getting into the server game but it is doing what it can. As for this forum: With advent of 2TB SATA drives and the home media theatre many folks wish to use a server to source all the HD movies they have on Blu-Ray disks. Thus so many amateurs herein. <smile>

Yes, Ubuntu should have a forum just for Enterprise help. Likely they will as folks like us talk more about having one.

A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. -- Archbishop Desmond Tutu, 1999

frank

---

### Post by epsolon77 on 2009-10-27
The major difference between enterprise and personal use is merely where it is used and thus the amount of tolerance the systems owners have in failure, and the budgets used to create them.

Remember that a few decades ago the computer was a business entity only, except for some semi rich hobbyists.  Then networks were only for large enterprises.  As processing power grows, and network technology progresses more and more people will be adopting the same technologies that make computers work at the office in their own homes.  So where do you draw the line in support?  What about desktops?  The differences between a desktop used in an office and one used at home is a few applications.  90% of that machine is identical.  Same desktop, same browser, same internet ect.  I argue that it is the same with servers.  They are no longer strictly the realm of business.  As hard drives become cheaper and are more approachable to mass markets more people will want to take advantage of storage systems that normally were only the realm of corporations.  My mother, for instance, is really into her pictures and scrapbooking.  She has nearly 200 gb of pictures and needs a good place to store them and access them from any of her many computers.  Does this mean that her storage solution will be very different from a small company holding hundreds of thousands of pdf's to the tune of 200 gb?  The only difference here is my mother does not have funding for a 500 dollar hardware raid card.  But then again neither does my company right now.  All that cash is locked away in proprietary tape drives, phone systems and maintenance contracts.  

My point is that the lines are gray and wide, with the same technology being utilized on both sides of the line.  The question should not be "what are other businesses doing" but rather "what really works".  No company can innovate and break out into new markets by doing the same thing everyone else is, and I argue that IT departments should be run the same way.  IT Professionals of this world I say "[SIZE="3"]Don't fear to break out of the conventions of yesterday.  Forge ahead on your own path![/SIZE]  [SIZE="1"]Just don't put forge ahead on the production servers. The boss will be REALLY pissed.[/SIZE]":D

---

### Post by windependence on 2009-10-27
> **djamu said:**
> 
I have a good memory and had to go back a while to find that thread ... where you praised me for a remark, we chatted a little ... you might want to re-read it > [http://ubuntuforums.org/showthread.php?t=860288&page=2](http://ubuntuforums.org/showthread.php?t=860288&page=2)

<snip>

Peace 

Jan

Actually my memory is good as well and I do remember talking with you. It was a good thread, but certainly I don't think your remark about about my level of proficiency was warranted. I looked after you posted and I am sure you were remembering this post:

[http://ubuntuforums.org/showthread.php?t=981224&highlight=evms+lvm](http://ubuntuforums.org/showthread.php?t=981224&highlight=evms+lvm)

which is was not involved. Surely you don't think because I haven't been exposed to a certain technology e.g. EVMS, I am stupid or incompetent? In the thread you referred to I simply asked you about it as I WAS ignorant of EVMS at the time, but there you seemed to agree that I was a "professional" just as you are. We just have different experiences being on different sides of the globe. 

At any rate, why so confrontational this time. I remembered I really enjoyed our conversation in that thread. We're all on the same side here with the same goals. I would hope we continue to work together to help users become aware of the "professional" way of doing Ubuntu server. That's why I'm here. As you mentioned, I don't see any Ubuntu in data centers, but I certainly don't think there is any other reason besides it's new and many enterprise admins don't even know the server product exists or if they do, they think it's just the desktop kernel with the GUI removed. I have several installs of Ubuntu server running Zimbra in VMs for my small business customers and I have to say I'm impressed. I was hoping to eventually see more uptake into the enterprise instead of RH, CentOS, and SuSE. (which are all fine distros, but diversity is good)

Peace out!

-Tim

---

### Post by epsolon77 on 2009-10-27
Hey windependance I have some more questions for you RE-zimbra.  I'd like to say that I really appreciate the information everyone has given.  I will probably work up some specs on a three storage server system using soft raid, vs comparable storage on a hardware raid and see which is better.  I really like the work up djamu had with PXE boot storage clients and a initiator running the PXE.  I will make some modifications I'm sure, but it's a killer concept to give additional reliability on the cheap.  I will also be seeing how the price on that adaptec card changes the equations for hardware raid.

On Zimbra, have you had good feedback?  How does it compare to exchange?  Were still a couple years out from needing to get off exchange 2003, but for when we do I've been eying zimbra and would love some preliminary thoughts.

---

### Post by windependence on 2009-10-28
Exchange replacement is what I do with Zimbra. There are even import tools. We use only the Open Source free product, but licensing is much cheaper than Micro$oft if you need support or extra features. It certainly is by order of magnitude more stable and robust than Exchange. You may be surprised to know that Comcast's web mail is a modified version of Zimbra. You can see that it scales very well.

If you need help, let me know.

-Tim

---

### Post by epsolon77 on 2009-10-28
I sure will let you know.  Like I said that nut is a ways off, but I don't think I can swallow an exchange upgrade.  It pains me to think about the cash we are dropping on proprietary software.  

It doesn't surprise me that Comcast uses modified Zimbra, in part because I was a Comcast technician for three years...

---

### Post by joeinbend on 2009-11-02
Hi, just dropping a few lines in on this: Regarding the posters' original question, in personal use and even small business production, there is nothing wrong with software RAID. As you have probably already read, today's processors are so fast that the minimal overhead presented for parity calculations in the RAID are barely a blip on the proverbial radar. The reason Enterprises do not use software RAID are because they are such high-performance NAS/SAN's that it does require dedicated processing for RAID.

Regarding your comment about NAS vs. SAN, they are very very different technologies. SAN is not just the "big brother" of NAS. I recommend some Wiki reading to come to terms with the technology differences. You will see that basically NAS's are for general storage, and SAN's are "virtually locally" attached, typically via fiber, to datacenter servers.

Anyway, others on here can attest, I have written a complete how-to document on building a RAID-5 NAS based on Ubuntu server, requiring no previous knowledge of Linux, and will give you a good handle on learning Ubuntu at the command-line! Take a look if you like: [http://www.bishoptechnology.com/content/pdf/raid.pdf](http://www.bishoptechnology.com/content/pdf/raid.pdf)

enjoy :)
Joe

---

### Post by djamu on 2009-11-03
Some comments.

> **joeinbend said:**
> 
snipsnip....
As you have probably already read, today's processors are so fast that the minimal overhead presented for parity calculations in the RAID are barely a blip on the proverbial radar. The reason Enterprises do not use software RAID are because they are such high-performance NAS/SAN's that it does require dedicated processing for RAID.


I second that, but the main reason ( according to me ) for using HW raid's in the industry is slightly different. 
Most large deployments use pre-build OEM racks with HW-raid cards for which the client has to install a OS of his choice. Windows soft raid is notoriously bad / slow, so to get any kind of reasonable performance out of it ....  you need to use HW raids... 

I think OP is well aware of the differences between NAS/SAN as even the most simplistic iSCSI setup needs to be SAN ( for non local storage )

> 
Anyway, others on here can attest, I have written a complete how-to document on building a RAID-5 NAS based on Ubuntu server, requiring no previous knowledge of Linux, and will give you a good handle on learning Ubuntu at the command-line! Take a look if you like: [http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

enjoy :)
Joe


** A couple of remarks on your paper:**
Please do consider these changes.

Most users don't need the latest mdadm version, and so I don't recommend it. The latest stable release ( 3.1 ) supports re-shaping raids from about any type to any other type ( including from raid5 > raid6 )

Also simply compiling stuff is not recommended either as apt / aptitude is then unaware of these changes. The recommended procedure for any compile is to create a deb package that gets installed and involves 1 additional package. > checkinstall

```

sudo apt-get install build-essential checkinstall 
wget http://www.kernel.org/pub/linux/utils/raid/mdadm/mdadm-3.1.tar.gz
tar zxf mdadm-3.1.tar.gz
cd mdadm-3.1
sudo make
sudo checkinstall -D make install
sudo update-initramfs -u

```

This will create a deb package that gets installed, and updates any initramfs image

**Whole devices vs partitioned devices:**
Creating 1 partition on each device prior to create an MD device out of those partitions has a couple of advantages over creating an MD device from whole devices.

I'll elaborate:
Some long term users ( including me ), have a policy of cycling out disks at regular intervals ( including not buying all disks from the same fabrication batch ).
Because of this policy disks may be of different models and even brands, and so it's very possible that some disks have a total sector count that is slightly more or less from the other disks.... and you will be in a lot of troubles if it's only a tiny bit less....

So a good policy is to create a partition that is slightly smaller then the total raw volume of the disk ( 100MB is safe  > this area is near the spindle and is always somewhat less reliable and slower anyway )

So, disks don't need to be the same size > 
raw volume size will be (n-1)*size ( for a raid5) and (n-2)*size for a raid6 where size=volume of the smallest device
for linear raid it doesn't matter at all ( but better use LVM for that )



**don't manually create a mdadm.conf after creating the array**

```

dpkg-reconfigure mdadm
mdadm --assemble --scan

```

this will automatically create the correct one for you > add a MAILADDR [email]you@your.url[/email] if it didn't ask for it.


**Formatting arrays**:

ext3/ext4 on striped arrays ( raid 0 / 5 / 6 ) 

simply creating a ext2/ext3/ext4 FS on a newly created array is a no GO... as it will work inefficient ( this is because the blocksizes / journalling positioning doesn't match raid 0/5 / 6 stripes which will cause additional and unnecessary head seeks.

**Making the FS raid aware** is the correct way when using ext 2/3/4 ( on any array > including HW raids ) 

example for ext4.
don't copy and paste these !

```
 sudo mkfs.ext4 -E stride=96,stripe-width=16 -m0 /dev/md0 
```

stripe-width = raidblocksize / ext4 blocksize > raidblocksize=64k ( default ) ext4 blocksize=4k ( default ) > stripe-width = 16
 
stride = stripe-width * active disks > active disks = amount of disks without parity & spares > a raid5 array with 7 disks has 6 active disks / raid6 with 8 disks and 2 spares( 10disks total)  has also 6 active disks 

so the stride value for a raid6 array with 8 disks (without the spares ) and stripe-width=16 > has stride = 96

-m0 > makes sure there isn't any wasted superuser disk space ( default = 5%) , there's no need to reserve this much space on a storage device


**Recycle:**
Most windows users are rather clumsy and will look for the recycle-bin when they accidentally deleted something on a SMB share...  
SMB does support this with a vfs object, and will move a deleted file inside it instead of permanently deleting it, this deleted file can be sorted by user ( who deleted it ) / date / keep track of versions / keep tree ...

Can be a real lifesaver even for nix users...

A sample config for a standard share definition

```

[storage]
        comment = RAID6-storage
        path = /media/storage
#        force user = jan  # not needed 
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes
[COLOR="Blue"]        vfs objects = recycle 
        recycle:maxsixe = 0
        recycle:versions = Yes
        recycle:touch = Yes                       
        recycle:keeptree = Yes 
        recycle:repository = recycle-bin/%U [/COLOR]

```

**explanation:**

        vfs objects = recycle                                 > defines vfs type
        recycle:maxsixe = 0                                 > 0=unlimited size
        recycle:versions = Yes                             > keep versions
        recycle:touch = Yes                                  > keep permissions
        recycle:keeptree = Yes                            >keep the original ( relative ) filetree 
        recycle:repository = recycle-bin/%U    >relative path to share path > in this case path=/media/storage/recycle-bin/


you can change the relative path to an absolute path > even another disk ( large storage system with seperate scratch share ) 


> 
From other Linux desktops, you can also install Putty, which should be available through your flavor
of Linux&#8217;s repository


huh? lol since when does one need putty on a linux machine ?
 in any shell / terminal you can just type 
```
ssh your.url
or 
ssh yourIP

```

if you need X use 
```
ssh -X your.url

```


**lastly: partitioning arrays**

you can partition arrays > (as /dev/md0 is not the 1st partition of /dev/md)

a normal array ( /dev/md0 ) is unpartitioned and is normally treated by the OS as a large superfloppy ( which is also unpartitioned )

The advantage of partitioning an array has over creating several arrays from partitions is that the partitiontable becomes redundant too ( when you create several arrays from partitions, the partititiontables of the individual disks are not redundant, neither is the MBR btw.
That means you have to consider that not all data on the disks is redundant..

The latest versions of mdadm require you to include the --auto=mpd statement ( good to always include whether or not one uses it.. )
 
you can then partition this array to your liking with your favorite tool > mine is cfdisk

```

sudo cfdisk /dev/md0 

```
mounting a partitioned array ( after formating ) can then be done with > mount /dev/md0p1 /media/array-1

or you can use LVM to do the same ( and much more )


**Administration GUI ? **
you don't seem to be aware that ubuntu ships Samba with Swat ( seperate install on debian ) 
apt-get install swat 
you might need to restart xinetd/inetd  (whatever was installed or got installed with it) to get it operational 
so one does not need webmin ...

it's accessible on [http://yourserverIP:901](http://yourserverIP:901) /  [http://yourserver.url:901](http://yourserver.url:901)
and doesn't need separate apache etc.. installs 

I'm not to keen on all those fancy administration interfaces but I often use Munin as monitoring tool ( bandwidth disk/array status temperature )  uses rrdtool > and uses plugins .. ( I've written a whole bunch of them myself )

[http://munin.projects.linpro.no]("http://munin.projects.linpro.no/")/
[screenshots]("http://images.google.be/images?hl=en&source=hp&q=munin&um=1&ie=UTF-8&ei=hGvwSpLFEqLNjAfvotnKCA&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CCIQsAQwAw")



A quick summary of mdadm commands 

[http://svn.debian.org/wsvn/pkg-mdadm/mdadm/trunk/debian/README.recipes?op=file&rev=0&sc=0]("http://svn.debian.org/wsvn/pkg-mdadm/mdadm/trunk/debian/README.recipes?op=file&rev=0&sc=0")


and lastly, do differentiate ( as I said earlier ) between cold/hot-swap ( cold swap is NOT the same as swapping drives while the server is off )... see my 1st post in this thread 


;)
my 5 cents

---

### Post by joeinbend on 2009-11-03
WOW! djamu, that is by far the best feedback I have gotten! Any system always has room for improvement based on additional knowledge, and I am blown away by all of this; truly an eye-opener. I will be going through all of your info and building new test VM's and physical test servers over the coming weeks, to release an updated document. 

Thanks again, truly fantastic. I'll post here when I have an updated version, and will probably have questions before then.

Thanks!!

---

### Post by fjgaude on 2009-11-03
Okay, Jan, take your place at the head of the table when it comes to software raid. Thanks for sharing your valuable experience!

I'm still using v2.6.7.1 of mdadm... never had an issue with it. Will look into v3.0 and beyond soon.

frank

---

### Post by djamu on 2009-11-03
> **fjgaude said:**
> Okay, Jan, take your place at the head of the table when it comes to software raid. Thanks for sharing your valuable experience!

I'm still using v2.6.7.1 of mdadm... never had an issue with it. Will look into v3.0 and beyond soon.

frank

Thank you for your comment... I feel flattered :oops:
... It's just that I follow up development closely and I noticed these new capabilities, which come in handy if one has has to perform such operations as reshaping MD devices ( RAID5  > RAID6 normal devices to RAID5 etcetc... there's still a minor issue with reshaping RAID0 to RAID6 ;)  ), also note that online shrinking is now fully supported ( but make sure your FS also supports it ! )... for schrinking one needs to schrink the FS before schrinking the MD ( the opposite of growing )

I tested the latest version a couple of days ago on a spare RAID6, and went on a destruction derby ..... but all is good ...

But still, I don't even consider using it on a production server ( why would I ) as I don't have any issues with the stock installed ones either....


):P

---

### Post by epsolon77 on 2009-11-03
Ok here's a big what if.

What would happen to the raid array if the bootable partition were recovered to say a week earlier, assuming of course no hardware had changed since then.  I would assume it would recover correctly, but assumption is the mother of all ... mistakes.

---

### Post by djamu on 2009-11-03
> **epsolon77 said:**
> Ok here's a big what if.

What would happen to the raid array if the bootable partition were recovered to say a week earlier, assuming of course no hardware had changed since then.  I would assume it would recover correctly, but assumption is the mother of all ... mistakes.

I'm afraid I don't fully understand your question, can you elaborate a bit ?

---

### Post by epsolon77 on 2009-11-03
> **djamu said:**
> I'm afraid I don't fully understand your question, can you elaborate a bit ?

On your server that hosts the softraid you have a boot partition and your storage partition.  What happens if your boot partition gets corrupted, or your Operating System becomes non functional for any reason.  If you were to back up that boot partition to a previous time does this break the raid array?  The one assuption I will throw in is that there were no hardware changes since the backup was done.

---

### Post by djamu on 2009-11-03
> **epsolon77 said:**
> On your server that hosts the softraid you have a boot partition and your storage partition.  What happens if your boot partition gets corrupted, or your Operating System becomes non functional for any reason.  If you were to back up that boot partition to a previous time does this break the raid array?  The one assuption I will throw in is that there were no hardware changes since the backup was done.

I now assume you're talking about my proposed setup ... 

I always boot from a raid1 into a raid5/6 ( you really can boot from this kind of raid -raid1 I mean- in contrast to what some claim ) > this is because the initramfs loaded kernel initially is not aware of the ( ro ) mounted partition and only sees a normal partition and FS ( critical MD info related to the array is written at the end of the partition and takes less then 1MB ... this also means that the only safe way to convert a normal partition with an FS on it to a raid0/1/5/6  is to shrink  the FS on it with about 1MB > convert it to RAID and then expand the FS on the remaining :rolleyes: diskspace . ( not related to your question I believe ... ) 

I often employ cheapo 256MB usb sticks as RAID1 with mount point /boot  to bootstrap the system and continue booting into the main array using UUIDS ( the one from the MD array not the individual disks ) > grub supports using UUID's instead of for example 
```
root (hd0,0)
```
references ( in /boot/grub/menu.lst )
so my menu.lst would then look like ( it's a debian server sorry )
```
title           Debian GNU/Linux, kernel 2.6.30-lrfp-b
uuid            9692910c-5ca9-4cb2-a2f8-c87d224d0e4d
kernel          /boot/vmlinuz-2.6.30-lrfp-b root=/dev/md1 ro quiet
initrd          /boot/initrd.img-2.6.30-lrfp-b
```

This assures you that the disk from which the system continues to boot may be irrelevant ( in case of a continued boot in RAID1 > as said earlier RAID1 is the only mirror type, all other raid types are stripe flavours, that also means the system only needs to access one of the physical disks out of which the RAID1 consists...  I'll explain the reason for using RAID1 as OS partitions later on 

ok:  enough with  this:

The proposed boot server I spoke of earlier doesn't have any storage
It uses the aforementioned SLC SSD's as RAID1 and boots straight into these ....
if anyone if these fail ... well it's irrelevant as I don't reference from grub to a physical disk.

My backup server PXE boots from the boot server straight into a partitioned 4TB RAID5  ... I'm not using a local swap partition because it has 4GB RAM and loopdevice mounts a small ( 100MB ) file from the bootserver as swap. > The contents of this server consists of a couple of very large LZO compressed files that contain the complete backup of my main and a couple of files that act as loopdevice mirrors for the other systems...
It doesn't have an OS ( uses large tftp served initramfs image as OS )

my main storage server in my lab is more "traditional" in layout, just because if something would not be right ... and consists of

4GB RAM 
2*256MB USB sticks as RAID1 mounted as /boot
9*1TB as RAID6 ( 1 spare ) 6TB raw storage
I didn't partition the array itself for various reasons ( mainly because I'm the only one who will ever touch that machine, and I wanted a traditional setup that should continue to work when everything else fails, this server OS also mirrors onto the backupserver with a loopdevice file )

each disk has 3 partitions > 4GB / 1GB / 995GB

/dev/md1 mounted as / RAID1
2nd partition as swap 
/dev/md2 mounted as /media/storage  RAID6

In this case it's extremely unlikely that my OS gets corrupted .... and since I'm using UUID's for grub, the system can pick any disk of the /dev/md1 device to continue booting

my iSCSI targets are similar to the backup server and don't have an OS either... 

My compute nodes don't have disks at all 

My workstations all use PXE boots / or mounted loopdevice files as HD's ....

So you see I have quite a lot of computers, but there's none of them that isn't redundant ..
The 2 computers that actually contain an OS consists of RAID1 devices that are also mirrored onto remote loopdevice mounted files ( a file the size of the OS partition onto a share that is mounted onto a loopdevice that is mounted as a RAID1 mirror )...

This all creates a kind of Ouroboros system ( actually 2 Ouroboros systems that self reference to each other )> 
Ouroboros wikipedia h[ttp://en.wikipedia.org/wiki/Ouroboros]("http://en.wikipedia.org/wiki/Ouroboros")
Self-reference / Self-reflexivity > [http://en.wikipedia.org/wiki/Self-reflexivity]("http://en.wikipedia.org/wiki/Self-reflexivity")


This means I can yank out any disk at any time ( and even remove all HD's from the bootserver ) without the systems ever going down ....

does this answer your question ? ... no need to tell you that a good UPS is crucial .....

I have to admit I never tried a "normal"  boot into a partitioned array ( I will do that tomorrow >  good point )


geez look at all that text again 

;)

---

### Post by djamu on 2009-11-04
mmm after re-reading my previous reply I thought it was a little to messy and confusing ( had a long day and it was late )

What I'm essentially doing with these setups is similar to using distributed  mirrored (OS) vmware images without the need of using a distributed FS.  ( more or less the way Wubi works, which gave me the idea ) 

This in 2 ways:

Either compressed CPIO initramfs images ( with a complete OS ) that get served by PXE / dhcp / tftp, these images completely reside inside RAM ( my workstations / backupserver / compute nodes use these )

or 

Shared files mounted on loopdevices ( as a block device ) as a localized RAID1 mirror. ( my main storage / bootserver  use these )

Raid1 only needs 1 device for reading, and uses all of them for writing. 
To prevent any excessive network latency / possible race conditions on the system / network ( at least 1 mirror resides remotely ) these files get mounted RO ( Read Only ).

I extensively use AUFS to track any changes to the OS onto a RAM disk( AUFS is an alternate version of UnionFS ) 
[http://en.wikipedia.org/wiki/Aufs]("http://en.wikipedia.org/wiki/Aufs").

AUFS / UnionFS / Cowloop are all similar mechanisms where one does combine a RO device with a RW device > the 2 get presented to the OS as a single device > it reads from the RO part and write to the separate RW device ( for which I use RAM disks )
On shutdown I can then opt to flush the contents of those RAM disks to storage > either rebuilding the RO image / LVM snapshot / discard ( you'll have to script these )

For clarity. I don't use NFS / SMB to distribute the images ( the PXE booted ones ) Only TFTP.  The TFTP service gets replaced by a torrent tracker as soon as I solved some minor problems with random access ( and have time )...  

Keep in mind that this system is actually more geared toward the storage part of a 3D HPC cluster then for web-services ( network topology is completely different on both )

I just finished a big job, so my site is now completely outdated. I hope to free a couple of weeks to work on both. I'll keep you guys updated if anyone is interested in this.



Jan

---

### Post by epsolon77 on 2009-11-04
Per your "look at all that text again"  I've never faulted a text book for having too much information in it.

That kind of awnsers my question.  I'm trying to understand how the information about the raid is stored.  If all the raid configuration data is stored on the core OS, a fault in the core OS would kill the raid.  But if the config data were to be stored on the raid itself that transporting the drives to a new OS and rebuilding the RAID array would be simple.

Sorry I'm getting away from a question on best practices and more into an indepth interrogation on RAID technology.  I can't help it, I'm a nerd.  It's what I do.

---

### Post by fjgaude on 2009-11-04
Data is stored in the superblocks of each drive in mdadm raid, so the OS can be changed. I've done it many times without issue, moving an array to a different machine running different CPUs and OSs.

---

### Post by djamu on 2009-11-04
> **epsolon77 said:**
> 
....
That kind of awnsers my question.  I'm trying to understand how the information about the raid is stored.

raids are self contained and portable... they don't really need a config, all config data ( from the raid ) is on the RAID itself > mdadm has an option to export the bitmap onto a seperate device btw.
> 
  If all the raid configuration data is stored on the core OS, a fault in the core OS would kill the raid.

no the images get mounted read-only and uses AUFS to track changes to the core OS.
> 
  But if the config data were to be stored on the raid itself that transporting the drives to a new OS and rebuilding the RAID array would be simple.

correct, I use a golden client ( a vmware image on a workstation ) to actually build the core OS's > they get exported as either Initramfs images / DD files and will only change on a complete rebuild.
Just think of it as a live CD system which is btw also an option, > build your core OS the way you like, reserve space for any DB onto a ( remote ) rw file ( loopdevice mounted whatever ), install AUFS/UNIONFS and add mountpoints for your log directories > and build a Live CD out of it ... ( an ISO file onto anything the can hold the image ) > load it into RAM to accelerate IO, RAM is cheap these days...

> 
Sorry I'm getting away from a question on best practices and more into an indepth interrogation on RAID technology.  I can't help it, I'm a nerd.  It's what I do.

That's a good thing

---

### Post by djamu on 2009-11-04
I answered a little to quickly. I think I'm getting what you really mean.  
> 
If all the raid configuration data is stored on the core OS, a fault in the core OS would kill the raid


Linux uses vfs ( virtual file system ) which effectively layers and abstracts devices ( virtualize if you like ).. each layer works independent from the other and all are self contained.. 

It sits between user space and your physical hardware ( in kernel space )
( FUSE allows kernel space to interact with user space > making your own FS systems ... add custom encryption / exotic FS's ... )
good example is the Fuse NTFS driver )


This is hard to understand at first, but allows almost infinite combinatons of real and virtualized.

I suggest you read these, you'll understand much better what I was proposing earlier..

Multipathing is related ( and enabled ) by this.. The device mapper... ( in short multipathing allows a system to have multiple ways to connect to for example a physical HD )


[http://en.wikipedia.org/wiki/Virtual_file_system]("http://en.wikipedia.org/wiki/Virtual_file_system")

some schemes 

[http://www.haifux.org/lectures/119/linux-2.4-vfs/linux-2.4-vfs.html]("http://www.haifux.org/lectures/119/linux-2.4-vfs/linux-2.4-vfs.html")

Fuse explanation graphs and links.

[http://en.wikipedia.org/wiki/Filesystem_in_Userspace]("http://en.wikipedia.org/wiki/Filesystem_in_Userspace")



Multipath.

[http://en.wikipedia.org/wiki/Multipath_I/O]("http://en.wikipedia.org/wiki/Multipath_I/O")

Device Mapper ( multipath )

[http://en.wikipedia.org/wiki/Device-Mapper]("http://en.wikipedia.org/wiki/Device-Mapper")

---

### Post by epsolon77 on 2009-11-04
Thank you that expalins it.  Now if only I had the spare parts around here to make a full test.  Oh well.  I've scrounged a piece of hardware with 1 SATA drive.  I'll use LVM to block it up into 3 parts and try a mdadm raid on those three drives I guess.  I had a second drive but my new external IDE power adapter made the controller smoke and explode.  At least the drive is still readable on a different controller.

---

### Post by djamu on 2009-11-04
> **epsolon77 said:**
> Thank you that expalins it.  Now if only I had the spare parts around here to make a full test.  Oh well.  I've scrounged a piece of hardware with 1 SATA drive.  I'll use LVM to block it up into 3 parts and try a mdadm raid on those three drives I guess.  I had a second drive but my new external IDE power adapter made the controller smoke and explode.  At least the drive is still readable on a different controller.

woops...

mmm you don't need LVM for this ... I myself only use it occasionally .. focus on the basics

I learned all of this by using vmware / virtualbox / KVM ( vmware can only use 2 cores / virtualbox all off them / KVM needs hardware support ( needs either VT / AMD-V ) 
> virtualbox is a free Sun product which I recommend that allows multiple project snapshots
[http://www.virtualbox.org/]("http://www.virtualbox.org/")
vmware might be a litlle easier > server version is free but only supports 1 snapshot / and has easier to configure (virtual) networking..

KVM is what I very often use to virtualize rendernodes.. ( barely any performance penalty )

If you go for KVM > simply install these from the repos and ignore the difficult ( outdated ) howtos  > [http://virt-manager.org/]("http://virt-manager.org/")

Then with whatever you have installed > create some virtual HD's / raids  / networks / machines / and go berserk ...

:lolflag:

---

### Post by epsolon77 on 2009-11-06
I know LVM is not required, but I figured it's high time I start learning it.  As for KVM I can't use it because my proc is an ancient P4 that does not have VT support required by KVM.  
I could probably run VirtualBox on there, and probably will in the future.  

Here's a thought....Can you install a virtual machine on a Cloud?

---

### Post by epsolon77 on 2009-11-06
> **epsolon77 said:**
> I know LVM is not required, but I figured it's high time I start learning it.  As for KVM I can't use it because my proc is an ancient P4 that does not have VT support required by KVM.  
I could probably run VirtualBox on there, and probably will in the future.  

Here's a thought....Can you install a virtual machine on a Cloud?

Nevermind, I think I figured out that you can install a virtual machine on the Eucalyptus Cloud, but the nodes need to be KVM capable.  Sigh.

---

### Post by djamu on 2009-11-06
> 
Here's a thought....Can you install a virtual machine on a Cloud? 

I don't think you can install anything else but ....
> **epsolon77 said:**
> Nevermind, I think I figured out that you can install a virtual machine on the Eucalyptus Cloud, but the nodes need to be KVM capable.  Sigh.
That shouldn't be a problem for creating those ( I think )
mmm, well I might give you access to one of my i7 rendernodes ( I'll hook up some scrapped disks mmm got some 1TB disks that are not in use, those should do I guess, you can then create the initial images with them > and I'll dump them wherever you like ..... but not this weekend ;) I'll PM you first with the details. As a matter of fact you might be well of with one of my VM's, just PM me with what you think you'll need / evt. cloud access codes .. and I'll see what I can do to get you started ( 1 time offer only ) ...


have a nice weekend

---

### Post by epsolon77 on 2009-11-06
> **djamu said:**
> I don't think you can install anything else but ....

That shouldn't be a problem for creating those ( I think )
mmm, well I might give you access to one of my i7 rendernodes ( I'll hook up some scrapped disks mmm got some 1TB disks that are not in use, those should do I guess, you can then create the initial images with them > and I'll dump them wherever you like ..... but not this weekend ;) I'll PM you first with the details. As a matter of fact you might be well of with one of my VM's, just PM me with what you think you'll need / evt. cloud access codes .. and I'll see what I can do to get you started ( 1 time offer only ) ...


have a nice weekend

I really appreciate your offer.  I must decline, primarily because it would be for no other purpose than my own education, and my job, wife and kids see too it that I have little time strictly for my education.  I'm trying to free some of my companies investments in technology and make them more flexible and highly availability.  They've been investing in proprietary solutions each on their own server box, and now we have tons of servers all doing their own thing and failing on their own.  The web is now so tight that if we lose 1 server, the rest are almost useless until the failed server can be restored.  So I'm obviously trying to set up an hardware virtualization layer to bind all my physical boxes and run the VM's off the combined boxes.  I think I'm onto something with clustering, like Beowulf or something else that starts with a K and has some ties to the EU and France (gotta love how specific I am.  What can I say, it's Friday, my brain has stopped working).   I really appreciate all the help you've given me, and your offer is very generous.  I just know I don't have the time to use it outside of work, and my work doesn't have the funds to buy a set of VT capable boxes, so it would not be the most efficient use of my time.  I can guarantee I will not be buying anymore non VT or AMD-V class processors.

---

