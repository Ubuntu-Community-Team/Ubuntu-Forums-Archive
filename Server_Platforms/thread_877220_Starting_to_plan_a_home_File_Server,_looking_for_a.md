---
title: "Starting to plan a home File Server, looking for advice on hardware."
date: 2008-08-01
forum: Server Platforms
---

### Post by gyzer on 2008-08-01
I am in the process of planning on setting up a home file server running Xubuntu. The file server will also be used to download torrents and binaries off of Usenet. down the line I might setup a proxy server, but I don't know enough about Squid yet to even think about that in detail right now.
 
I have only been using Linux (Ubuntu 8.04 is the distro I started out using first) since about April of this year. 
 
The server is going to contain all documents, music, videos, images, and all that jazz for me, my wife, and eventually my daughter. 
 
A total of 6 computers (5 starting out until my daughter gets old enough to have her own computer) will be accessing this server.
 
One computer is a Windows XP/Vista machine (my gaming machine), an Ubuntu 8.04 machine (the machine I do everything else on outside of gaming), my wife's Vista machine, a media center pc running Xubuntu 8.04, and a very old laptop that is running Xubuntu 8.04. 
 
I am looking to spend under $1000 on this server, the lower the better.
 
Here is my currently picked out hardware:
Intel BOXDG965WHMKR LGA 775 Motherboard
Intel Pentium E2200 2.2GHZ Dual-Core Processor
2GB of DDR2 800
4x Seagate Barracuda 7200.11 500GB 7200 RPM SATA II in RAID 5
80GB SATA Where OS will be installed to
Rosewill RC-219 Silicon Image PCI Express External eSATA II x2 NCQ non-RAID Controller Card
 
To help keep the price down I'm thinking about using the RAID options on the mobo, but that idea isn't set in stone by any means.
 
I have the eSATA card so I can hookup an external hard drive where I can keep backup images for all the client computers in my home network. I'm not very well versed in backup applications or processes in Ubuntu, but I have used Partimage off of the System Rescue CD, and like how it works on all different file system types. 
 
I am very interested in hearing about any other backup suggestions that people have. I would also like to figure out someway to back up the 1.5TB RAID5 array, but I have no idea where to start on that.
 
So, I'd like some comments and suggestion on my hardware choices, what file system the RAID 5 should be (vfat, ext2, ext3), and some suggestions on backup solutions for the client machines and for the RAID array.
 
Thanks in advance!

---

### Post by dca on 2008-08-01
I'm not gonna' be much help but most of my home servers have all been Pentium III PC(s) w/ anywhere from 256 to 512 MB RAM.
 
The only thing special is I purposely would install PCI/IDE RAID card.  I'm cheap so I never fooled around w/ SATA drives at the house but RAID cards for them are about the same.
 
The last one was a PIII w/ 512MB that had 4x 80Gb IDE HDDs in RAID5 running Ubuntu 6.06LTS Server Edition.  Only SAMBA, FTP, & SSH installed.
 
If you start going in the TB range you run into issue(s) w/ doing back-ups because how expensive a 1.5TB NAS device is.  Having to buy one of those just to b/u a server that cost you $50USD in parts was kinda' out of the question.

---

### Post by dca on 2008-08-01
Oh, if it's just storing files, nothing else, no web hosting, no playing on it while other people are trying to store stuff on it, I would go the cheapest route possible.  You can get your hands dirty w/ the latest LTS Server Edition release (8.04).  Don't get nervous, it boots up w/ no GUI.  Text only.

---

### Post by gyzer on 2008-08-01
Is there anything backup wise that can do compression so I don't have to have 1.5TB to back up the entire 1.5TB of data?
 
Also It will take a very very long time for me to fillup 1.5TB of hard drive space, so even then I think I could use a smaller hard drive to backup on.
 
I guess if I were to go to a pcie based RAID controller with an IOP on it I could drop the processor down from being a dual core. Sadly though the processor is only costing like $70 while I know at minimum a RAID 5 capable SATA II pcie crontroller will cost at least $150 up to over $350.

---

### Post by gyzer on 2008-08-01
In Ubuntu 8.04 Server, can you start x, startup whatever services and do whatever setup you want to do then just shutdown x and those services and configurations will just stay and work perfectly?

---

### Post by dca on 2008-08-01
Ubuntu 8.04LTS Server Edition is text only.  You can install the desktop over it if you wish but it's designed to be run on a headless server.

---

### Post by dca on 2008-08-01
...also you can look into 'rsync' using gzip compression...
 
[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)
 
I believe it installs by default in Server Edition, also look into 'cron' or 'cron jobs' to make it automatically sync when you want it to...

---

### Post by gyzer on 2008-08-01
This is definatly going to be a headless server, I'm just not 100% comfortable setting up stuff via the command line yet. I litterally would install the gui, then after setting everything turn off the x server.

---

### Post by jimmy the saint on 2008-08-02
If you go to the Dell outlet site, you can get a killer deal on a tower.  I just got a nice one for 300 [dual core, 2gigs ram, 300gig HD, and a bunch of other stuff].  This would likely be overkill for a server, but it was an easy way to get spare parts that I used for my main machine.  I removed the cdr, 19-in-one card reader, and some other stuff.  All you really need is a p3 with some ram, a NIC and a whole lot of disk space.  If you are in the US you can check out craigslist or even govt surplus sites.  Another easy alternative would be a cheap NAS device from newegg.  If you budget is $1000 you can get a really really really nice one!  If  you want to save some money you can settle for a really really nice one.  Good Luck.

---

### Post by gyzer on 2008-08-02
Originally I was thinking about going the NAS route, but then I started to read up on them, and most of them have really poor performance compared to a files server. I just thought that in the end I'd be able to do more and get better performance out of a file server than going with an expensive overpriced NAS. 

I know I could go the route of building my own NAS with using one of the various Linux/Unix based NAS mini OS's but down the line I might want to do more with this machine then just a file server. 

Thanks for the sugestions!

---

### Post by cariboo on 2008-08-03
If you don't have a large budget, for what you need just go with a lowend motherboard and maybe only a 1GB ram, You can find some all in one mb's for less than $100.00 including the processor. Spent your money on storage. I just sold an ECS A740GM-M the other day and saw that it had 6 sata ports, something like that would be perfect for a server.

Jim

---

### Post by gyzer on 2008-08-04
Yeah.
 
Anyone have any sugestions on a good pcie SATA RAID 5 capable Controller card that has an IOP?

---

### Post by 3rods on 2008-08-04
If you're going to buy a E2200 2.2GHZ Dual-Core Processor, I would spend the extra cash to get the quad-core or at least move up a processor family. My E2200 Dell at work is a turd compared to the E6600 I have at home. It is a **very** noticeable difference. Both are dual core and both run near 2Ghz, but my E6600 is way faster with similar specs.

At the very least, spend the extra $40 to upgrade to the E7200 wolfdale and 45nm. It's only $120 at the egg. It's LGA 775, so you can use the same board. I'm partial to Asus boards, but I don't have anything against the Intel board - especially for a server box. 

If it was me, I'd get the Q6600 OEM. It's under $200, it's got 4MB x 2 of L2 cache, it's LGA 775 and it's quad core @2.4ghz. I don't think it's a stretch to spend 20% of the budget on the CPU. It may just be a file-server now, but you might want it to stream video and music next week. The E2200 isn't going to cut it for that.

---

### Post by ajk32 on 2008-08-05
I just set up a new headless file server based on Ubuntu 8.04 (server edition). I am relatively new to linux but not to computers in general (having built more windoze machines than I care to remember) but was impressed by how easy it was. Lots of googling was done beforehand and these forums have been very helpful. Here is the hardware I chose if it helps! (all from Newegg)

MSI motherboard 945GCM7-F 775 945GC Retail - $47.99
CPU INTEL Celeron 1.8G 775 512K Retail     - $39.99
1 GB RAM DII667                            - $19.99
CASE ATHENATECH A3603BB.400 BLK            - $41.99
Seagate 500GB 16M SATA2 ST3500630AS (x4)   - $319.99
  
I already had a spare 80GB PATA hard drive to use for the OS, and the motherboard has 4 SATA ports and an ATA port so this was perfect. The case is bog standard, but what I liked is it's a mini tower with 9 (nine!) drive slots, so I could have 5 drives with a space in between each one to promote air flow.

I added a few SATA cables and a 'Y' power splitter to power two hard drives (the motherboard only has two and the older ATA HD uses the standard 4 pin.

With shipping and handling (40 bucks! because of the case), the whole thing cost me a shade over 500 bucks.

It took me a few hours to set everything up, but I was being very careful not to do anything wrong. I also had to work out how to set up Ubuntu server from a USB stick (no CDROM drive) but that was pretty easy in the end. Once the OS was installed, which needed a keyboard and monitor, it was made headless, shoved in the cupboard upstairs and I continued the setup via SSH and putty.

I now have a fully functioning 1.4TB Raid5 samba server which is serving two laptops and an Xbox with movies, photos and general files. Linking it up to the wireless router upstairs, the file transfer rate to the living room is a little slow for my liking, but that's not the servers fault. In the past couple of days I have installed some cat6 cable and now it transfers at 100Mbit/10MB per sec (the limit of my router). Next plan is to upgrade the aging router so I can see how much of the gigabit pipe it can cope with. I've transferred some files directly by mounting an external HD via USB to the server and that is much quicker but I have never measured it. It built the array at around 50-60MB/sec so maybe that is the theoretical maximum of the MB/proc/HD combo? It seems to be more than speedy enough for what I want and I have the freedom of adding more functionality than I would have had just buying an off the shelf NAS.

Hope this helps! Good luck!

Andy

---

### Post by gyzer on 2008-08-05
3rods- You are defiantly smoking something, I'd never throw a quad core or a higher end dual core into a file server unless the server was for enterprise purposes. 
 
The only reason I was initially putting in that E2200 was cause of how cheap they are.
 
I've actually changed my configuration again to help bring down its price.
 
Then new board I'm using is a ECS GF6100-M754 with a Athlon 3200+ for $83.99 and thats before a $20 rebate. Thats on newegg.
 
I've also changed my hard drives to Seagate Barracuda ES.2 ST3500320NS 500GB 7200RPG SATA II drives. I've read that they are more reliable than the regular consumer grade Seagate drives. They cost like $15 more or so a drive.
 
I've also thrown in a Accusys ACS-61000-4 PCI Express SATA II RAID Controller. Sadly this bad boy is the most expensive single component for the entire system, at $299. 
 
ajk32- Are you using the on-board "fake RAID" thats on that MSI mobo, or are you using a controller?
 
I've only used mobo based RAIDs for RAID 0 setups. I've never done a RAID 5 before personally. I'm a bit scared about using a mobo based RAID for fault tolerance because of all the horrible stories I've heard about them going bad. 
 
I guess though it would be cheaper to replace a $50 mobo then a $299 controller card.
 
Thanks for the sugestions. ajk32, I'm definatly gonna take a look at that mobo and processor, I really don't like ECS boards.

---

### Post by gyzer on 2008-08-05
Ok ajk32, I just looked at the MSI board on NewEgg, and it has no on board RAID. Are you using software raid in Ubuntu?
 
That scares me even more lol
 
ajk32, what file system are you using on your RAID array? vfat?

---

### Post by ajk32 on 2008-08-05
Software raid - to my thinking it gave me the most flexible and cheapest solution.

Using my logic (which I admit, is just my opinion) I can suffer 1 SATA HD failure and still have my data intact, due to raid 5. I can suffer the PATA drive failing because all I would need to do is put another cheap hard drive in and reload the OS (a pain, but it's the data that's important, not the OS). I can even have a motherboard failure and I *should* be able to take my raid array and move it over to a new computer if I have to. What scared me was if my raid controller card went bad, I would have to purchase *exactly* the same model and put it in to access the array. I have no idea how reliable these cards are, but to my mind, software raid and regular backups of mission critical data (mainly photos in my case!) to an external hard drive was the way to go for me. 

As I said, I am relatively new to Linux and all the information I could find on the web pointed to either ext3 or reiserfs for a file system. I went with ext3 in the end (mainly because I got bored of all the ext3 vs reiser websites) and it has been fine. The only thing that surprised me is that ext3 reserves 5% (5% of 1.4TB = 70GB!) for the root user in case the rest of the disk is full. For days, I was trying to work out why windoze was telling me I had 70GB less than I should. Since my OS is on a separate drive, and again reading the web, I saw no problem with reducing this to 0 (easy to do, I forget the command now but google ext3, 5%, reserved).

HTH, Andy

---

### Post by gyzer on 2008-08-05
Software raid is starting to make alot more sense. Only thing now is I'm wondering if I should go to a low end dual core to help the system multitask some more when it comes to multiple users and the cpu dealing with the raid.
 
Now with using ext3, which is what I currently use on my Ubuntu machine, you aren't using any window's based pc to interact with the server are you? I'm under the impression that Window systems can't read ext3 partitions, but with a small plug-in they can read ext2 partitions. Thats also why I asked if your using vfat.
 
I'm going to be connecting at least 2 Windows machines up to this server in addition to the several Ubuntu machines.
 
Thank you so much for your help, I think you've deffinatly pointed me in a better direction then I've been going in!

---

### Post by ajk32 on 2008-08-05
Forgot to mention the motherboard only comes with 1 SATA cable and it wasn't clear what size it was so I purchased:

12-123-108  10" SATA CABLES OKGEAR|GC10AUBM12 x2 @$2.99 **
12-123-111  18" SATA CABLES OKGEAR|GC18AUBM12 x2 @$3.99

The extra SATA power cables needed come from:
12-123-119  HD Power CABLES OKGEAR|GC6ATAM2 x1 @$1.89

With this case, you could put all the drives at the bottom all bunched up in the 3.5" bays, but I wanted to spread them out so I organised them so that I had (moving up the case): drive, space, drive, space, drive, space, drive, space, drive. There were two unforseen problems with this: 

Firstly, I forgot to purchase the 3.5" to 5.25" drive rails to install the two uppermost drives into the big bays (luckily I had some lying around from years ago). The cables are a perfect length with the shorter two serving the lower two drives and the longer the uppermost.

**Second, you will notice that the SATA cables I purchased were straight at one end and 90 degrees at the other. The logic was to have the straight ends in the motherboard and the 90's in the drive. This was perfect apart from the lowermost drive, which couldn't accommodate the 90 bend (no room between the drive and the case 'floor') so I had to reverse that cable. I suggest purchasing 1x10" straight/straight, 1x10" straight/90 and 2x18" straight/90. Depending what case/MB combo you go with, YMMV.

You will also need more drive screws as there are not enough supplied with the case/MB. Might seem trivial but it's annoying enough to turn the air slightly blue when you realise.

Andy

---

### Post by ajk32 on 2008-08-05
> **gyzer said:**
> 
 
Now with using ext3, which is what I currently use on my Ubuntu machine, you aren't using any window's based pc to interact with the server are you? I'm under the impression that Window systems can't read ext3 partitions, but with a small plug-in they can read ext2 partitions. Thats also why I asked if your using vfat.
 
I'm going to be connecting at least 2 Windows machines up to this server in addition to the several Ubuntu machines.

I'm using SAMBA on the server so that my windows machines can see it in 'My Network Places' as a mapped network drive. I'm probably only scraping the surface of what SAMBA can actually do, but it works brilliantly.

Andy

---

### Post by gyzer on 2008-08-05
So samba doesn't care what file system is on the drive? WOW I did not know that.
 
Check out this site for cables [http://www.monoprice.com/products/subdepartment.asp?c_id=102&cp_id=10226](http://www.monoprice.com/products/subdepartment.asp?c_id=102&cp_id=10226)
 
I freaking love this place. You can pick up HDMI cables for under $10. 
 
That link is for there assortment of sata cables, some with even locking connectors for under $2.00.

---

### Post by ajk32 on 2008-08-05
Yeah - I actually used monoprice for the cat6e cables I installed and some connectors, very cheap. Problem with splitting the order is you have to pay for shipping twice...

---

### Post by gyzer on 2008-08-05
Alright, this is my FINAL config:
 
MSI 945GCM7-F LGA 775
Intel Celeron E1200 1.6GHz Dual-Core
1GB of DDR2 667Mhz
4x Seagate Barracuda ES.2 ST3500320NS 500GB 7200 RPM SATA 2
Evercool EC-PT12-9525EA 95mm CPU Fan
Athenatech A3602BB Case w/ 400W Power Supply
WD 20GB Ultra ATA/100
 
I decided to go with the E1200 because I think that a dual core would be good here so as to help offset the cost of the RAID 5 on the cpu. Also with a simple bsel mod I can get its base non-overclocked speed up to 2.2Ghz which should be more then enough to help support the software RAID 5.
 
The total cost, including a new WD 20GB for $17, comes to $583.91. My last setup was at $965.83. This setup is also not including a backup drive for offline backup. That I plan to add in with a simple eSATA PCIe card, a external HDD dock, and of course a HDD. 
 
I'm not to sure on the size of the hard drive, because I'd like to experiment on different compression methods so as to make it that I don't need a 1.5TB backup solution.
 
Any insight in to a couple of compressed backup solutions would be really nice.
 
Thanks for all the help

---

### Post by ajk32 on 2008-08-05
No problem! Keep us all up to date on progress... good luck!

Andy

---

### Post by gyzer on 2008-08-05
Sadly this wont be happening for several months. I've just had alot of time on my hands lately and I wanted to hammer out all the details on this project and on several others.

---

### Post by Teh_Messiah on 2008-09-24
I was actually informed about Xubuntu through [www.bit-tech.net]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1"). I am studying certificate 4 in IT at a local college and after being taught about raid 5 and windoze server 2003 it got me curious. Then i got a virus on my computer and nearly lost all my pictures, movies, game files and what not. 

So i googled "how to build a file server" and this was the first site that turned up.
It gives you a great walk though on how to set up a cheap file server but unfortunately it doesnt tell you about raid 5 setup.

I bought a SiI3114 sata raid controller card from Ebay which supports 4 drives and raid 0, 1, 5, 10 and JBOD. However i also discovered that it's linux driver 
(which i dont know how to install, it needs JAVA, which i also dont know how to install or wich one to install either)
doesn't support raid 5 despite the fact that windoze driver does.

As you can probably guess i am new to Xubuntu, but i am keen to get this project working.
I know basic programming in WinXP VB Scripting and Visual Basic.net. However i am very new to Linux and how to use it. we had major issues installing Xubuntu, but discovered (after consulting my lecturer) That the install was conflicting and getting confused with with my IDE OS 40 gig HDD and my 4x 250gig Satas on the raid controller. (Disconected the power to the hard drives and it worked first time after re-installing Xubuntu).

This is my old first computer which is still going strong. It has had many upgrades to make it much better than a 2.4ghz P4 with double the ram than this rig has.
[MS-6390]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=307&maincat_no=1&cat2_no=&cat3_no=") mobo,
AMD Athlon XP 2200+ 1.8 ghz cpu Socket A,
ATi 9550 with 256mb,
SiI3114 SATA raid controller with 4x Samsung 250gb SATAs,
IDE Maxtor 40gb primary HDD,
512mb Ram.

I guess i should
- install a software raid 5 program 
- then set the disks up as a JBOD through the raid controller software
- then use software raid to set up a raid 5 array

My questions are,
1. Is this the right way to do it? (as above "I guess i should")

2. What Java do i install/search-for in the Synaptic Packet Manager 
- (I need Java to run the controller card software)

3.1 What software RAID 5 do i get and where do i get it and how do i install it?
3.2 or should I search Synaptic Packet Manager for 1 and which one should i use?

Tutorial wise if you are new to Linux (like myself), that tutorial at [www.bit-tech.net](www.bit-tech.net) is awesome. although it needs a little more info in some areas.

---

### Post by gyzer on 2008-09-24
Check out this thread [http://ubuntuforums.org/showthread.php?t=849659](http://ubuntuforums.org/showthread.php?t=849659)
 
Its about software raid 5 setup.
 
I don't think you need to set them up as a jbod at all. 
 
With doing the software raid, you don't need a controller card, if your system board has sata ports on it, use those, otherwise just get a stata controller, not a raid controller.
 
Also watch out on if this card is a pci or a pcie card. The bus speed on a pci sata card can bottleneck the performance of your sata drives.
 
Good luck

---

### Post by windependence on 2008-09-24
The card you bought is software "RAID-on-a-chip", it's not real RAID. Any time you need a "driver" for a RAID card, it's probably not real RAID.

You can either get a good card like 3ware, or use software RAID. I prefer a hardware card but software RAID works fine. Generally, if you have time and you just want to learn, software RAID is great, but if you just want to get a server running as soon as possible, hardware RAID is better because there will be less configuration.

You also cannot boot from a software RAID array, whereas you can with hardware RAID.

-Tim

---

### Post by Teh_Messiah on 2008-09-24
OK.

Thank you.

I don't have $300 (actually, it's $500+ AU) to buy a hardware raid. :(

At the moment i can't see any of my 4 sata drives and I don't know how to access them to format them. When the option comes up in bios when i start the machine it looks something like this

Press ctrl + s or F4 to enter set-up
sata raid controller
drive 1    <drive ID>   232gb
drive 2    <drive ID>   232gb
drive 3    <drive ID>   232gb
drive 4    <drive ID>   232gb

Then i need the Java program in the machine to set up the raid in there.
in the bios setup i can set up a raid 5 in there but then it doesn't format properly in widoze.

Unfortunately this mobo is nearly 10 years old and doesn't have its own sata connectors. It also doesn't have any PCIe slots, they weren't heard of 10 years ago when this mobo was made. It doesn't even have USB 2.

So even though it's through bios it's still a software raid?

I found another site last night that said to use mdadm which i found in the synaptec thingy.
I installed that but got tired and went to bed. since it was like half past midnight when i posted last night...!

So what software do i use and how do  do it? or is that on that other link you posted gyzer?

Thank you both. I gotta go get my Lego castle chess set now \\:D/

Be back later.

---

### Post by Teh_Messiah on 2008-09-25
Not to mention, no one has told me what Java to use and how do i get it and install the raid software.
I cant even see my drives and don't know how to access them.

When i google "how to do it ...." I get alot of rubbish which is no help what so ever.

Is there a beginners step by step guide to Xubuntu or something somewhere is can learn how to use this properly. 

It seems alot of people like to use acronyms and just assume that everyone knows what the hell they are talking about. I want to learn but I cant find anything that will teach me how to use it properly.

Please help?

---

### Post by windependence on 2008-09-25
Well you certainly don't need Java installed in order to set up RAID in your card's BIOS because it can't possibly be loaded during boot. I'm also kinda doubting you need it after boot also because you need an OS installed to run it, and you can't do that unless your RAID is set up. Here is how to install Java on ubuntu:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Now, if you will give me the exact brand and model number of your card, I will see if I can find some documentation for you. Actually, with Linux, older hardware is usually better supported than newer hardware so that could be an advantage.

In most RAID card setups, you have to select your RAID type and then add the drives that you want to put in the RAID array and save the configuration and exit. Then the RAID array will build so you can use it.

Let me know about the card and I will try to help you. ;)

-Tim

---

### Post by Teh_Messiah on 2008-09-25
Ok,

It is a Silicon Image [SiI3114 PCI to 4 port sata150]("http://www.siliconimage.com/products/product.aspx?id=28") <-- Linked to the site. 

In windows although it has the bios set-up it wouldn't work in windows even after setting up the raid5 in bios. I couldn't format the logical drive of 464Gb (raid 5 drive). (I had to use only 3 of the 4 sata drives because one was an old one and apparently has errors, it kept dropping out and i got a warning from the raid controller saying it was bad. I then had to delete it as an Orphan.
I needed the Java software in windows to set up the raid5 and then format it through windows mmc disk management. (running windows XP home)

From what i have read at the web site I also need to do the same in Linux.
Install a Java software program to set up the raid. 
I downloaded the .pdf for the raid tools manager, but i don't have the install guide for the Java software.
 The manager pdf file mentions how to set it up but not how to install it and i don't know enough about the commands and what i need to type to do any of this. 

I'm still learning and I am not getting anywhere at the moment.

Thank you very much for the help too, it's greatly appreciated.

Ben

---

### Post by Teh_Messiah on 2008-09-28
Hi guys,

Just checking in to see how you went with your search for the right driver that i need. 
There seems to be alot of drivers for different linux platforms and i dont know which one i should get.

This is the [driver link for the SiI3114]("http://www.siliconimage.com/support/supportsearchresults.aspx?pid=28&cid=3&ctid=2&osid=1&"), Which one should i get please?

I gather i just get the latest [SATARAID tools (link)]("http://www.siliconimage.com/support/supportsearchresults.aspx?pid=28&cid=11&ctid=2&osid=1&") from here since there only seems to be 2 of them?

Thanks again, Ben

---

### Post by Teh_Messiah on 2008-09-28
I tried to install the raid gui with no luck. then i remembered that i needed to allow the rights to install it and this is the result i got in the terminal:

```
ben@MS-6390-Xubuntu:~/Desktop/SiI3114/RAID_GUI/SiICfg$ chmod a+x Setup.sh
ben@MS-6390-Xubuntu:~/Desktop/SiI3114/RAID_GUI/SiICfg$ ls -l
total 104
drwxr-xr-x 7 ben ben  4096 2005-08-27 02:25 [COLOR="Blue"]classes[/COLOR]
drwxr-xr-x 5 ben ben  4096 2005-08-27 02:25 [COLOR="Blue"]doc[/COLOR]
drwxr-xr-x 3 ben ben  4096 2005-08-27 02:25 [COLOR="Blue"]image[/COLOR]
-rwxr-xr-x 1 ben ben   222 2005-08-27 02:25 [COLOR="Lime"]J2ee.library[/COLOR]
-rwxr-xr-x 1 ben ben   258 2005-08-27 02:25 [COLOR="Lime"]jhelp.library[/COLOR]
-rwxr-xr-x 1 ben ben   286 2005-08-27 02:25 [COLOR="Lime"]jmail.library[/COLOR]
-rwxr-xr-x 1 ben ben 12432 2005-08-27 02:25 [COLOR="Lime"]libSiCommand_i386.so[/COLOR]
-rwxr-xr-x 1 ben ben 12432 2005-08-27 02:25 [COLOR="Lime"]libSiCommand.so[/COLOR]
-rwxr-xr-x 1 ben ben 17545 2005-08-27 02:25 [COLOR="Lime"]libSiCommand_x86_64.so[/COLOR]
-rwxr-xr-x 1 ben ben  1501 2005-08-27 02:25 [COLOR="Lime"]macro.properties[/COLOR]
-rwxr-xr-x 1 ben ben   216 2005-08-27 02:25 [COLOR="Lime"]port.properties[/COLOR]
-rwxr-xr-x 1 ben ben  2436 2005-08-30 02:48 [COLOR="Lime"]Setup.sh[/COLOR]
-rwxr-xr-x 1 ben ben   436 2005-08-27 02:25 [COLOR="Lime"]SiICfg.html[/COLOR]
-rwxr-xr-x 1 ben ben   607 2005-08-27 02:25 [COLOR="Lime"]siicfg.properties[/COLOR]
-rwxr-xr-x 1 ben ben  4028 2005-08-30 02:46 [COLOR="Lime"]Start_RAID_CFG.sh[/COLOR]
-rwxr-xr-x 1 ben ben   240 2005-08-27 02:25 [COLOR="Lime"]vssver.scc[/COLOR]
ben@MS-6390-Xubuntu:~/Desktop/SiI3114/RAID_GUI/SiICfg$ ./Setup.sh
You must have a Silicon Image Driver newer than 1.0.0.52
for this GUI to work. Enter CR to continue cr
 JNI library not found in /usr/lib. copying libSiCommand.so to /usr/lib
cp: cannot create regular file `/usr/lib/libSiCommand.so': Permission denied
copied libSiCommand_i386.so to /usr/lib/libSiCommand.so
DEV_NUMBER= 0
Making node to character device major 0 (/dev/SiIdev c 0 0)
mknod: `/dev/SiIdev': Permission denied
Doing a 'ls -al /dev/SiIdev' and confirm that the driver registered a character device
ls: cannot access /dev/SiIdev: No such file or directory
Type carriage return to continue
```

Why did it not have rights to install this and how do i get around it so it will install properly please?

The instructions just say to 
"Run Setup.sh"

But when i double click it nothing happens and if i right click it and "Execute" also nothing happens.

Ben

---

### Post by Teh_Messiah on 2008-09-28
This is the instructions from the compressed file too:

> Install & Run Instructions for Linux RAID GUI

To install:

	Run Setup.sh script

To run:

	Run Start_RAID_CFG.sh
 

Notes:

	Inspect Start_RAID_CFG.sh. The Java Run Time environment directory varies with system configuration. You may need to modify this script and set the proper path.

	DISPLAY variable may not be set correctly  ( e.g. export DISPLAY=:0 )

	The driver must be running and /dev/SiIdev must exist. Do an lsmod to see if the driver module sii has been loaded. 

	Load JRE 1.5.0_04 from [http://java.sun.com](http://java.sun.com). Some kernel versions need JRE 1.4.2 (e.g. FC2).

Which made sense but didn't work!

Ben

---

### Post by Teh_Messiah on 2008-10-07
Bump!

How did you go windependence?

[QUOTE=windependence]Let me know about the card and I will try to help you. ;)[/QUOTE]

---

### Post by Spitphire on 2008-10-14
This guy wrote a great how-to for software raid setup on a headless machine using Webmin and mdadm.  It's a fairly current how-to (written on 9 Sep 08 ).  Complete with a screenshot walkthrough.

[http://www.smallnetbuilder.com/content/view/30573/77/]("http://www.smallnetbuilder.com/content/view/30573/77/")

---

### Post by lazyart on 2008-10-14
> Making node to character device major 0 (/dev/SiIdev c 0 0)
mknod: `/dev/SiIdev': Permission denied
Doing a 'ls -al /dev/SiIdev' and confirm that the driver registered a character device
ls: cannot access /dev/SiIdev: No such file or directory"Permission denied" means you need to use sudo to run this command```
sudo ./install.sh
```and possibly sudo again to run the config script.

---

### Post by windependence on 2008-10-16
> **Teh_Messiah said:**
> Bump!

How did you go windependence?

Looks like you can use the card, but you won't be able to boot fomr the RAID array with that card. You have to load the kernel module to use the card. Only the RAID manager uses java, not the actual driver itself. below is from the user manual:

> Linux Systems
On a Linux system the SATARAID5 Manager and daemon can be installed into any subdirectory. Before launching the SATARAID5 Manager, the driver must be installed and the daemon must be running in background. If you are using a bootable version of the SATARAID5 driver, it is already included in your Linux kernel. If you are not using a bootable version of the SATARAID5 driver, you must manually load the driver by typing the following command:
• insmod si3XXXr5.ko (where “3XXX” refers to your specific SATA controller chip)
Then, the daemon must be started. If the daemon has been incorporated into the startup scripts (typically included within the /etc/rc directory structure, it will start automatically when you boot your system. Otherwise, you must manually start the daemon in a background mode by typing the following command:
• ./SATARaid5ConfigServer &
Finally, you can launch the SATARAID Manager by typing the following command:
• java –jar SATARaid5Manager

-Tim

---

### Post by cbreaker on 2008-10-23
> **gyzer said:**
> 3rods- You are defiantly smoking something, I'd never throw a quad core or a higher end dual core into a file server unless the server was for enterprise purposes. 


Eh.  They're so cheap!  You can get a quad core CPU (either Intel or AMD) for so cheap it's almost silly NOT to get one.

File servers at home always end up doing more than just serving files.   They are used as media servers, backup servers, domain controllers, and everything in between.

If someone is going to build a file server for home, and plan on attaching a lot of storage to it, I'd recommend 4GB RAM minimum for a nice big disk cache (it's so cheap! You can get a 4GB pack (2 2GB sticks) for like $60 at NewEgg) and a decent dual-core CPU, or quad if you want to spend the extra $30.   The extra RAM is especially important if you go with a software RAID.

If you want great disk performance go with a hardware RAID controller but it will probably be the most expensive part in the machine.

I have two servers running at home - a Windows Server 2008 x64 file server (4GB RAM, Dual-core Opteron, 11 hard drives totaling 5.5TB on an Accusys 12-port SATA RAID controller) and an Ubuntu VMware host (Ubuntu 8.10, 8GB RAM, four 500GB SATA disks on an Accusys 4-port SATA RAID controller running VMware Server 2.0.)  

To me, the hardware RAID cards are my favorite parts.   They were the most expensive single parts ($550 for the 12-port, $250 for the 4-port) but it was worth it to me.   The Accusys cards are really nice, and they are really fast.  Very full featured cards and they support MacOS, Linux, and Windows (Vista/2008 x64 too.)

Honestly, if you invest in the hardware RAID, you won't be sorry.   The Accusys cards support online RAID expansion, snapshots, and lots of operating systems.   The only bad part is they usually hardware RAID controllers require PCIe x8 slots, and many boards only have one of them.   So, get a motherboard with built-in video (unless you're going to use it as a media player machine on an HDTV) or get yourself a PCI video card (you can get a decent nVidia PCI video card for $40.)

That's my 2 cents on home file servers =)

---

### Post by carmy on 2008-10-23
I was trying this but i am not succeed so if you have more suggestion then give another reply,

---

### Post by ezacon on 2008-10-24
I built my first ubuntu home server long times ago, and i have replaced it 3 times now, because there are always new services that need more resources.
In the begining, it was a file server only. Now ir runs vmware server and a web server in a virtual machine, a mail server (zimbra) a another VM, Jinzora for music broadcast and local play at server, gallery 2 for digital photo and it is the gateway/firewall for my home network.
I use 4gb and 64 bit ubuntu server 8.04 (you need 64 bit to use 4gb or more).
For me, the power (energy) and noise are very important. This is why i use only 1gb sata drive. I have another external 1gb drive and i run a rsync job at night for backup. It is a home server, so it is not a critical server. In case of a disk crash, i can rebuild the server in a new disk with the daily backup.
So my recomendation for people building home server is:
It is dificult to load lots of services in the same machine. Use virtual machines instead to avoid conflicts and to separe things. Chose low power and low noise hardware.

Sorry for my bad english.

---

### Post by Teh_Messiah on 2008-11-09
I am still trying to sort this issue out and am still having troubles actually getting Xubuntu to work properly.
I have 8.04 installed and was going to upgrade it to 8.10 but the upgrade button isn't in the Update Manager.
it says i am up to date but it still says that i have 8.04 on startup.
I have downloaded the i386 desktop version of 8.10 and burnt it to disk. I just havent tried rebooting to try an upgrade yet!

I managed to get Java installed and running but i have got bogged down with study and can't get any further at the moment!

When i have time i will get back here and try to iron out the kinks.

---

### Post by kingnubian on 2008-11-11
I'm putting together a really cheap but very capable Ubuntu 8.10 based home server this week actually. Here is my parts list.

Intel D945GCLF2 Atom 330 Motherboard
1gig DDR2-5300
2x Samsung F1 750Gb SATA2 hard Drives
Micto ITX/Flex ATX Case (200W PS). 

A home server does not need to be a beast at all. The reviews I've seen using the board in my parts list, not fast at all, shows that for home server function it's much more than capable. 

I wanted a low power, quiet, reliable server to handle file, print & web server chores.

---

### Post by JonCage on 2008-11-19
A word of warning KingNubian: I have a very similar parts list:

Intel D945GCLF2 Atom 330 Motherboard
2gig DDR2-5300
4xSeagate Barracuda's of varying sizes

...and it seems there's some incompatibility under ubuntu and this set up. I'm using Ubuntu 8.10 and after swapping out a lot of the hardware, I've come to the conclusion that it's the SATA card it doesn't like. The whole system will lock up and need a hard reboot at some random time after Linux has started booting up. If I remove the card it's all good (I'm booting off a PATA drive).

I've aptitude update/upgrade'd and that hasn't helped. If anyone has any suggestions of how to get this going I'd be very grateful.

---

### Post by kingnubian on 2008-11-27
> **JonCage said:**
> A word of warning KingNubian: I have a very similar parts list:

Intel D945GCLF2 Atom 330 Motherboard
2gig DDR2-5300
4xSeagate Barracuda's of varying sizes

...and it seems there's some incompatibility under ubuntu and this set up. I'm using Ubuntu 8.10 and after swapping out a lot of the hardware, I've come to the conclusion that it's the SATA card it doesn't like. The whole system will lock up and need a hard reboot at some random time after Linux has started booting up. If I remove the card it's all good (I'm booting off a PATA drive).

I've aptitude update/upgrade'd and that hasn't helped. If anyone has any suggestions of how to get this going I'd be very grateful.

Thanks for the info!
I'm not using an addon SATA card just an Intel Pro/1000 nic and it seems to work great. I do get a kernel panic when the kernel tries to load off of the 8.10 64bit server cd but it doesn't matter since with only 1gig of ram in the system, 32bit will do fine. 

My issue now is the dismal & erratic Samba write speeds which are limiting one of the main uses for this setup which is as a file server.

---

