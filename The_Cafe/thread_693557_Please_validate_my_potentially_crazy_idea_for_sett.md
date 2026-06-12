---
title: "Please validate my potentially crazy idea for setting up my ideal NAS"
date: 2008-02-11
forum: The Cafe
---

### Post by pete-woods on 2008-02-11
Recently I've been looking at setting up a very high capacity, reasonably fast and redundant home NAS box. I want it to run RAID 5, have gigabit ethernet, and be as absolutely quiet as possible.

I was at the point of buying a QNAP TS-409. This basically did everything I wanted. However I noticed a product release by Intel:
[http://www.intel.com/design/servers/storage/ss4200-ehw/index.htm]("http://www.intel.com/design/servers/storage/ss4200-ehw/index.htm")
The SS4200-EHW.

This is a desktop hardware based NAS box. It seems to be aimed at system builders, the idea being that they stick WHS or a Linux distro on it. I was thinking that it'd be a good idea to get one and try to put Ubuntu server on it.

It has a 40 pin DOM IDE socket on the mainboard. My thinking is that if I get some form of bootable IDE flash drive and install Ubuntu on this, setup networking, SSH, etc - then transfer it into the Intel box I'll have a fabulous home NAS.

Does this sound like a plan that'll work? I've looked at the chipsets and such like from the product documentation and they all seem to be supported by the Linux kernel.

---

### Post by ajclarkson on 2008-02-14
at first glance it seems just crazy enough to work, if it supports bootable operating systems, and will allow a ssh access, then i cant see why you couldnt run a small server on it, however, bear in mind that some NAS units are purely hard drives, and therefore wont.

If it helps I bought a linksys Nlink NAS unit, which lets you hook up usb hard drives to your network, after a relatively simple hardware hack, i was able to turn the unit into a debian server running off a usb stick, with a second usb port acting as hot swappable storage so that i could run backups to it. that worked pretty well, sounds like a similar project, just on a smaller scale!

---

### Post by pete-woods on 2008-02-14
Thanks for the reply! Glad you've had a successful experience doing something similar. The reason I want to use this box is because of the specifications of the thing:
&#8226; 1.6 GHz CPU - enough for software RAID in-case the box breaks and I need to put my disks into another machine!
&#8226; 512 MB RAM
&#8226; Proper socket for installing flash IDE drive
&#8226; 2x eSATA ports in-case I need to play around with any other hard drives
This should make running a full Linux server on it a breeze (assuming drivers and stuff are okay).

The problem I'm having at the minute is that nowhere seems to have these things in stock!

---

### Post by skinnymonkey on 2008-02-21
Heck with that! Be patient and [buy this nicety]("http://h71036.www7.hp.com/hho/cache/572544-0-0-225-121.html") when it's released. Supposed to be 500GB and only $300. PLUS, it already has linux on it :)

You could buy two of them for redundancy and save yourself many hours (days) of "figuring" things out.

I bought the Media Server (WHS). The hardware is pretty nice but WHS absolutely sucks, it's corrupted my files three time already..... everytime it is shutdown and booted back up.

This newer Media Vault has been around for a while, this is just the new version. Goodbye Media Server

---

### Post by McLogic on 2009-03-03
SS4200-E ?!!?

The Intel Machine is available today and holds 4 drives. The Intel machine has a 256 mb flash DOM (disk on module). As it is all standard PC stuff, I'm surprised that I can't find a guide for installing Ubuntu.

The 256 mb flash disk means that we could overcome the main problems with Linux software RAID: booting and rebuilding complexities.

---

### Post by handy on 2009-03-03
I use [*_FreeNAS_*]("http://www.freenas.org/") which can be built on a PII or PIII which depending on which part of the world you live in, can be obtained for next to nothing. 

You add your drives, & if need be the simplest most cost effective route, is to use PATA -> SATA adapters that plug into your IDE ribbon cable slots on your motherboard.

imho, for a home system, RAID is a waste of drives.  

Use Gigbit LAN & see if more speed is required before spending all that money on drives.  

Use some of that money to have external drive backup of your data if need be.  

RAID is not a backup. RAID is the quickest way to back up corruption. 

Think of RAID as extending storage capacity & speed where it is appropriate.

Just a final note on FreeNAS:

FreeNAS is really quick & easy to set up.  It is very specialised & can do little else than what it does do, so well.

---

### Post by darkoptix on 2009-03-03
I had some friends that made their own NAS servers. Technically you can make it from anything, even an old machine that is lying around.
My friends made the server using some pretty high tech hardware. You do not need this high of specifications for a little server. I think this is what they used:
[http://ncix.com/products/?sku=33078&vpn=ES34069-BK-120&manufacture=CHENBRO]("http://ncix.com/products/?sku=33078&vpn=ES34069-BK-120&manufacture=CHENBRO")
[http://ncix.com/products/index.php?sku=32612&vpn=BOXDG45FC&manufacture=Intel]("http://ncix.com/products/index.php?sku=32612&vpn=BOXDG45FC&manufacture=Intel")


Then they used some sort of Intel Core 2 Duo and probably around 2gigs of ram.
That case supports hot-swappable drives, which makes it easy to replace.
I don't think for home use it is really necessary to buy something that is server level. If you build your own, you could install FreeNAS or Ubuntu Server, and run it however you want.

---

### Post by handy on 2009-03-03
Depending on the job that the NAS box has, using high end hardware is a waste of money, even to the point of money wasted on electricity.

The LAN speed is the bottleneck, & very few home users are using a NAS server with lots of gigabit NIC's installed on it & every other machine on their network, nor are they using a router big enough to cope. 

This is the bandwidth & usage needed to justify the expense of a RAID array that is built to provide extra speed.

imho, so many people use RAID inappropriately; thinking it will provide extra speed when the LAN speed is the bottleneck, or thinking that RAID is actually a data backup system.

---

### Post by thisllub on 2009-03-03
I would use an older machine with a NAS setup.
FreeNAS looks the goods to me.

---

### Post by thisllub on 2009-03-03
> **handy said:**
> 

imho, so many people use RAID inappropriately; thinking it will provide extra speed when the LAN speed is the bottleneck, or thinking that RAID is actually a data backup system.

IMO the only worthwhile speed improvement from RAID is if you use RAID 10. 
You get some fault tolerance and some performance improvement but you need four disks.
RAID 0 just seems too risky to me.

---

### Post by Biochem on 2009-03-03
> **thisllub said:**
> 
RAID 1 just seems too risky to me.

Since raid 1 is mirror (2 or more drives with exactly the same things) I can't see how it is risky. Unless of course you meant raid0

---

### Post by thisllub on 2009-03-04
> **Biochem said:**
> Since raid 1 is mirror (2 or more drives with exactly the same things) I can't see how it is risky. Unless of course you meant raid0

Of course you are right.
I guess I should read what I type.:oops:

---

### Post by kevdog on 2009-03-04
Handy

I just dont get it?  How is Raid 5 a type of backup solution?  It protects in terms of hardware failure.  Yes it doesnt mirror or duplicate, however its one form of a type of backup solution.  Ive used a Raid 5 for years, and have had many a hard drive fail, but never was the array corrupt.  I'm using a 3ware hardware based solution however and not software raid which IMO is just silly!

---

### Post by gletob on 2009-03-04
My aunt's about to upgrade her computer so she's giving hers to my mom and my mom said I could have her old machine.

It's an old gateway with a 1.8 Ghz Pentium 4, 1.25 GB ram, and intel graphics it's kind of overkill for a server but I'm planning Getting a pci Sata card and and four 500GB Drives in a RAID 1 (I think the one with striping and mirroring) with Freenas from usb flash drive

---

### Post by handy on 2009-03-04
> **Biochem said:**
> Since raid 1 is mirror (2 or more drives with exactly the same things) I can't see how it is risky. Unless of course you meant raid0

RAID-1 very quickly duplicates corruption.

At least with RAID-0 you usually know quite quickly that things have gone bad.  Not that that will save you any data anyway.

---

### Post by handy on 2009-03-04
> **kevdog said:**
> Handy

I just dont get it?  How is Raid 5 a type of backup solution?  It protects in terms of hardware failure.  Yes it doesnt mirror or duplicate, however its one form of a type of backup solution.  Ive used a Raid 5 for years, and have had many a hard drive fail, but never was the array corrupt.  I'm using a 3ware hardware based solution however and not software raid which IMO is just silly!

You have just been lucky, some people are, you are proof of that! :D

---

### Post by handy on 2009-03-04
> **gletob said:**
> My aunt's about to upgrade her computer so she's giving hers to my mom and my mom said I could have her old machine.

It's an old gateway with a 1.8 Ghz Pentium 4, 1.25 GB ram, and intel graphics it's kind of overkill for a server but I'm planning Getting a pci Sata card and and four 500GB Drives in a RAID 1 (I think the one with striping and mirroring) with Freenas from usb flash drive

Are you just getting into the RAID thing because you want to learn about it, or do you see some kind of benefit for your computer usage?

Really, I can't believe the number of HDD's that are being wasted in RAID arrays when they could be actually being used for genuine backup or still sitting in the warehouse. ;)

---

### Post by mips on 2009-03-04
> **handy said:**
> 
Really, I can't believe the number of HDD's that are being wasted in RAID arrays when they could be actually being used for genuine backup or still sitting in the warehouse. ;)

I think a lot of people have misunderstanding when it comes to raid. For personal desktop/storage use I see it as waste of hard drives. rsync is your friend ;)

---

### Post by handy on 2009-03-04
> **mips said:**
> I think a lot of people have misunderstanding when it comes to raid. For personal desktop/storage use I see it as was of hard drives. rsync is your friend ;)

Truly, I'd much rather have a drive full of backup data sitting somewhere, ***_not_*** powered up or connected to anything.  

It just waits like a calm lifesaver at the beach who will save me if I get caught in a rip.

We plug its life line in when needed & it breathes life back into our system.

---

### Post by kevdog on 2009-03-04
> **handy said:**
> You have just been lucky, some people are, you are proof of that! :D

I still don't follow.  I'm talking about raid 5 specifically.  It seems you know a lot of people who have experienced data loss using a raid 5.  I'm using this mostly to protect against hardware failure.  This in combination with another computer in which I mirror the most important directories using unison(rsync).  I guess my failure in my backup plan is that my second computer is not located "off-site" so a fire or such would destroy my setup.  Im really curious however to hear of your experiences with a hardware RAID5 failure.

---

### Post by TwiceOver on 2009-03-04
My ideal server would have a hardware raid5 solution with a minimum of 4 ports.  3 in use and 1 as a hot spare.

Just my opinion though.  Wish I had the money for such a solution.

---

### Post by handy on 2009-03-04
> **kevdog said:**
> I still don't follow.  I'm talking about raid 5 specifically.  It seems you know a lot of people who have experienced data loss using a raid 5.  I'm using this mostly to protect against hardware failure.  This in combination with another computer in which I mirror the most important directories using unison(rsync).  I guess my failure in my backup plan is that my second computer is not located "off-site" so a fire or such would destroy my setup.  Im really curious however to hear of your experiences with a hardware RAID5 failure.

The only way that RAID works as a backup is if there are more than one machine in the system.  If you back up a RAID box to another box be it RAID or otherwise, then you are going to probably have to be struck by lightening to loose your data. ;)  Well, no it won't have to be quite that extreme... :(

As far as RAID-5 is concerned, it goes down. Usually because two drives fail at the same time.  Most often because the drives are of the exact same vintage.  It is not a common occurrence, but there is no way I would ever trust a RAID-5 (or any other number for that matter) array to be the only repository of my irreplaceable data.

There are things that I don't like about Blue Ray, but I can see that the dramatically enlarged data storage capacity of the BR media as opposed to DVD media, is going to be of benefit & offer greater convenience than so many home computer users & small businesses have been used to, in the area of data backup.

The Blue Ray media capacity is still too small to allow it to be the corporate backup solution of the future.

---

### Post by handy on 2009-03-04
> **TwiceOver said:**
> My ideal server would have a hardware raid5 solution with a minimum of 4 ports.  3 in use and 1 as a hot spare.

Just my opinion though.  Wish I had the money for such a solution.

<shaking my head> Why do you think you need RAID?

Haven't you got better things to do with your money?

---

### Post by Icehuck on 2009-03-04
> **kevdog said:**
> I still don't follow.  I'm talking about raid 5 specifically.  It seems you know a lot of people who have experienced data loss using a raid 5.  I'm using this mostly to protect against hardware failure.  This in combination with another computer in which I mirror the most important directories using unison(rsync).  I guess my failure in my backup plan is that my second computer is not located "off-site" so a fire or such would destroy my setup.  Im really curious however to hear of your experiences with a hardware RAID5 failure.

I don't have any experiences with raid 5 creating data failure either. The whole point of it is if a HD goes your server doesn't take a dump forcing you to spend hours rebuilding the machine. Unless you are totally unlucky and had 2 drives go at the same time.

---

### Post by gn2 on 2009-03-04
If all you want is network storage, save time *and* money and get a [Slug]("http://en.wikipedia.org/wiki/NSLU2").

I agree with Handy about back-up, you want your back-up on a drive that gets little use and is physically separate, not on two (or even five) drives in one device that can get wiped out in the same thunderstorm.....

---

### Post by handy on 2009-03-04
> **Icehuck said:**
> I don't have any experiences with raid 5 creating data failure either. The whole point of it is if a HD goes your server doesn't take a dump forcing you to spend hours rebuilding the machine. Unless you are totally unlucky and had 2 drives go at the same time.

If you keep your eye on the Server Platforms sub-forum for a little while, you will see just how many RAID-5 systems go all the way down to unrecoverable.  It happens to them in soft, pseudo & hard RAID.  Mostly it is 2 drives failing at the same time.

---

### Post by TwiceOver on 2009-03-04
> **handy said:**
> <shaking my head> Why do you think you need RAID?

Haven't you got better things to do with your money?

Not really.  I like the security of knowing that if a drive fails I can just swap a new one in.

And this is my "ideal" situation, NOT reality.  Right now I just have a boat load of smaller disks in my box with different mount points.

---

### Post by thisllub on 2009-03-04
> **handy said:**
> RAID-1 very quickly duplicates corruption.

At least with RAID-0 you usually know quite quickly that things have gone bad.  Not that that will save you any data anyway.

This is a bit long winded but somebody might get something from it.

RAID is only a measure against hardware failure. 
Corruption is another issue altogether.
Regular data backups need to be maintained. With critical data a 24 hour backup cycle can be disastrous.


The only truly effective protection against corruption has to be designed into the application. 
I had a debate with the developers of one open source database (Firebird) about a recurring corruption problem. They denied the existence of a problem which I could easily reproduce.
The database has some excellent backup facilities. A full live backup and the ability to perform incremental backups of changed pages virtually end to end.
Unfortunately the incremental backups cannot detect corruption and the full backup takes substantial system resources to detect corruption that can possibly not be repaired. 
This can result in a restore missing 2 days worth of data.

I suggested that they should have a transaction log in an external file that could store all transactions since a successful backup is flagged. Replaying these transactions on the restored database would be a quick way to bring the database back to its correct state.

They suggested a replication product that was not exactly a solution to the problem, just a reasonable method of data protection.

For less mission critical files, eg. WP documents, spreadsheets etc rsync is excellent. 
I have set up remote servers in the homes of business owners that are a mirror of their main office servers.
Rsync transfers only files that differ between the two servers every night.
If the office server fails the a 20 minute return trip to retrieve the backup server will get them going again.  
More critical sites have onsite server clones that work exactly the same way.

Having used NAS systems I have to say that I prefer a fully functioning server.
There is really no function of a NAS that isn't better performed by a server.

---

### Post by handy on 2009-03-04
> **thisllub said:**
> 
Having used NAS systems I have to say that I prefer a fully functioning server.
There is really no function of a NAS that isn't better performed by a server.

I think it comes down to personal needs when talking about NAS.

Simple home user file storage, streaming duties, coupled with the ability to be a torrent slave, all set up on the very light & simple FreeNAS serves my purposes perfectly.  

I don't have a need for most of the services that FreeNAS can provide, & the box it runs on is a $5- box from the rubbish dump. ;)

---

