---
title: "help with building a home server"
date: 2008-09-27
forum: Server Platforms
---

### Post by jic12 on 2008-09-27
I'mg bulding a home server from scratch. I'm posting the components I'm thinking of buying and putting together to build this new system to serve as a home Server. Would you guys please look through these specs and let me know if there are any problems or incompatibilities with this system idea or suggestions, Thanks in advance!


+++ SAPPHIRE PE-AM2RS690MH AM2 AMD 690G HDMI Micro ATX AMD
Motherboard - Retail
[http://www.newegg.com/Product/Produc...82E16813154014](http://www.newegg.com/Product/Produc...82E16813154014)

+++ AMD Athlon 64 X2 6000+ Windsor 3.0GHz 2 x 1MB L2 Cache Socket
AM2 125W Dual-Core Processor - Retail
[http://www.newegg.com/Product/Produc...82E16819103773](http://www.newegg.com/Product/Produc...82E16819103773)

+++ OCZ Reaper HPC Edition 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2
800 (PC2 6400) Dual Channel Kit Desktop Memory - Retail
[http://www.newegg.com/Product/Produc...82E16820227267](http://www.newegg.com/Product/Produc...82E16820227267)

+++ Seagate Barracuda 7200.11 ST31000340AS 1TB 7200 RPM 32MB
Cache SATA 3.0Gb/s Hard Drive - OEM
[http://www.newegg.com/Product/Produc...82E16822148274](http://www.newegg.com/Product/Produc...82E16822148274)

---

### Post by jamesrfla on 2008-09-27
The links don't work but you do have the details which helps. As far as I see it should work. Is the motherboard 64-bit?

---

### Post by lykwydchykyn on 2008-09-27
What is your home server going to do? Just offhand, I'd say that unless you'll be streaming multimedia, pushing out thin clients, or running an instance of Oracle 4 GB of RAM seems excessive.

---

### Post by jic12 on 2008-09-27
Some friends and I are starting a website, and this will be the server to get it off of the ground.  If you would give me your opinion, I would really appreciate it!  I have some more money to spend, but I am trying to do it for as little as possible.  I just don't want to parts that don't work together.  And will drivers for ubuntu be a problem with any of these parts?

+++ SAPPHIRE PE-AM2RS690MH AM2 AMD 690G HDMI Micro ATX AMD
Motherboard - Retail

CPU Socket Type-AM2
CPU Type-Athlon 64 X2 / Athlon 64 / Sempron
Memory Standard 	DDR2 800
Expansion Slots
PCI Express x16 	1
PCI Slots 	2
PATA 	1 x ATA100 2 Dev. Max
SATA 3Gb/s 	4
SATA RAID 	0/1
Physical Spec
Form Factor 	Micro ATX
Power Pin 	24 Pin
Features
Features 	BIOS BACK Function: The BIOS Backup and Recovery Function
CPU Vcore 7-Shift / Shift_to the scalabilities and flexibilities
Debug Port: The Professional Hardware Diagnosis System
Packaging

+++ AMD Athlon 64 X2 6000+ Windsor 3.0GHz 2 x 1MB L2 Cache Socket
AM2 125W Dual-Core Processor

CPU Socket Type 	Socket AM2
Core 	Windsor
Multi-Core 	Dual-Core
Name 	Athlon 64 X2 6000+
Operating Frequency 	3.0GHz
Hyper Transports 	2000MHz
L1 Cache 	128KB+128KB
L2 Cache 	2 x 1MB
Manufacturing Tech 	90 nm
64 bit Support 	Yes
Hyper-Transport Support 	Yes
Virtualization Technology Support 	Yes
Multimedia Instruction 	MMX, SSE, SSE2, SSE3, 3DNOW! Professional
Voltage 	1.35-1.4V
Thermal Power 	125W
Cooling Device 	Heatsink and Fan included
Manufacturer Warranty
Parts 	3 years limited
Labor 	3 years limited

+++ OCZ Reaper HPC Edition 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2
800 (PC2 6400) Dual Channel Kit Desktop Memory - Retail
Type 	240-Pin DDR2 SDRAM
Capacity 	4GB (2 x 2GB)
Speed 	DDR2 800 (PC2 6400)
Cas Latency 	4
Timing 	4-4-4-15
Voltage 	2.1V
Heat Spreader 	Yes
Features 	Patent-pending Reaper HPC Heatsink
2.2V EVP
EPP-Ready

+++ Seagate Barracuda 7200.11 ST31000340AS 1TB 7200 RPM 32MB
Cache SATA 3.0Gb/s Hard Drive - OEM

---

### Post by lykwydchykyn on 2008-09-27
I'm not an expert on hardware compatibility (especially with newer equipment), but if the intention is to build a server you're probably in the clear.  The big areas of incompatibility tend to be 3D video capability, wireless networking, and internal modems; none of which concern you on a server.  I don't know what brand of NIC is on this board, sometimes broadcoms give you trouble, but being as it's an AMD board it probably doesn't use broadcom.  

If this server is for a website, and the website is going to have important data on it, you might want to focus your budget more in the area of storage and backup.  In other words, you probably want more than one hard drive and you want them in some kind of (preferably hardware) RAID configuration.  You need to look at how much data you're likely to have stored there and decide how to back it up -- DVDRW, tape, etc.

---

### Post by jic12 on 2008-09-28
> **lykwydchykyn said:**
> I'm not an expert on hardware compatibility (especially with newer equipment), but if the intention is to build a server you're probably in the clear.  The big areas of incompatibility tend to be 3D video capability, wireless networking, and internal modems; none of which concern you on a server.  I don't know what brand of NIC is on this board, sometimes broadcoms give you trouble, but being as it's an AMD board it probably doesn't use broadcom.  

If this server is for a website, and the website is going to have important data on it, you might want to focus your budget more in the area of storage and backup.  In other words, you probably want more than one hard drive and you want them in some kind of (preferably hardware) RAID configuration.  You need to look at how much data you're likely to have stored there and decide how to back it up -- DVDRW, tape, etc.

Thanks for your input.  Does anyone else have any comments before i order this stuff?

---

### Post by devonps on 2008-09-29
When you install your OS + applications you'll need a monitor and keyboard - but you haven't identified the gfx card, is it integrated with the m/board or an add-on?

I would add a 2nd hard drive **_(must have the exact specs as the 1st drive)_** - to allow you to use (soft) RAID from your m/board, and look at the different backup solutions.

Again, You haven't identifed what kind of case you intend to house these components in - will it have sufficient space/cooling, as you'll no doubt want to run the webserver 24/7.

This then leads nicely on to cooling aspects of the server, are you adding extra chassis fans, how many do you have?

Finally what about the power supply, is it branded? will it provide enough power? have you allowed for psu degredation as you'll be running the webserver 24/7 (I assume).

I've mentioned the above incase you haven't thought about them :)

I've recently completed a DIY build of a webserver and had to plan/research all of the above items to ensure compatability and reliability.

Anyway hope some of this is helpful to you.

Steve.

---

### Post by kevdog on 2008-09-29
Are you looking for a RAID solution?  If so RAID5 to prevent data loss?  I don't know if this is in your plans.

---

### Post by volkswagner on 2008-09-29
Seems like intense specs for a home server.  Are you hosting games?

Did you order the mobo yet?  It is out of stock at the moment.  You may consider a more power efficient cpu, like a 45 watt model.

The egg is great.  I alway read all reviews.  Usually someone will report on Ubuntu status.

Check this out
 > -from **good board for linux**
Pros: nice board,easy to install parts, good placement of components, plenty of usb. Processor and ram install was simple Ubuntu found everything out of the box. video works,sound works after swapping out some bad RAM it's a rock sold platform!

Cons: ati drivers are not all that great,compiz fusion dose not run so hot. no built in fire wire

Other Thoughts: amd athlol dual core 5200+ corsair 400w power supply 2 gig corsair ddr2 800 RAM 250 gig hard disk ubuntu 8.04 lst 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131172]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131172")


Another one I have my eye on.  This one has HDMI
> - from **Great MOBO**

Pros: A great price for a board that works with all the OS I installed. Great for over clocking easy to do safety features. Now running my AMD 4600+ @ 2.9ghz for five months no problems. I am going to go to the Phenom chip soon to see how the board works with that.

Cons: PCI slots too close together. If you install a Video card with a big fan you can't use the PCI slot next to it. That leaves you with one slot.

Other Thoughts: I have used Linux 64 bit, XP 64 bit, Vista 64 bit all on this board with dual boot options and no problems. As stable as my Asus Opteron server board but with all the clocking features. Thinking about buying another one of these for my son's machine. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813186141]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813186141")

---

### Post by kpatz on 2008-09-29
What will this website entail?  Dynamic content?  Streaming music/video?  How many visitors?

That platform should be more than plenty unless you anticipate heavy usage.

Chances are you won't need 4 GB RAM but it doesn't hurt to have it.  You'll want a 64-bit distro to take advantage of the 4 GB though.

The other thing to consider is data backup.  Maybe plan on getting 2 or 3 of those 1 TB drives.  Put 2 in the box, mirrored (RAID 1), then stick a 3rd in an external enclosure and use it for offline backups.

---

### Post by brian77095 on 2008-09-29
What time of internet connection are you going to use?  Does your ISP have static IP addresses?

---

### Post by jic12 on 2008-09-29
> **kpatz said:**
> What will this website entail?  Dynamic content?  Streaming music/video?  How many visitors?

That platform should be more than plenty unless you anticipate heavy usage.

Chances are you won't need 4 GB RAM but it doesn't hurt to have it.  You'll want a 64-bit distro to take advantage of the 4 GB though.

The other thing to consider is data backup.  Maybe plan on getting 2 or 3 of those 1 TB drives.  Put 2 in the box, mirrored (RAID 1), then stick a 3rd in an external enclosure and use it for offline backups.

It will stream video and host a forum.  Maybe more as It gets off of the ground.

---

### Post by Penquite on 2008-09-29
Again, not quite sure what you want to do with your server, but I run a server at home running a couple of web sites, plenty of samba shares, etc... on 

[http://www.fit-pc.com/new/](http://www.fit-pc.com/new/)

I am running Ubuntu server on it, and it is fanless, so the only noise is the occasional hdd click, and uses very little power. They have upped the spec since I purchased mine.

It was a bit fiddly getting Ubuntu server on it, but only because it has no optical drive so had to install from a memory stick.

Worth a look for a home server.

---

### Post by jld186 on 2008-09-30
Josh...I gathered the thoughts...I think we need to reshop.


64 bit OS - a problem, we aren't going to use Vista, or probably any other 64 bit OS which means we only need 3GB RAM, and we don't need a 64 bit Motherboard.

Add another HD in RAID - which means we need to learn to set up RAID.

More power efficient processor - so we need to shop for compatibility.

Ask ISP about static IP addresses - or look into dynamic hosting.



Can anyone tell me... 
What is a branded power supply?

~~~~
Josh, read this...

[http://www.wikihow.com/Buy-a-Power-Supply]("http://www.wikihow.com/Buy-a-Power-Supply")

---

