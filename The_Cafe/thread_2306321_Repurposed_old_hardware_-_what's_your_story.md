---
title: "Repurposed old hardware - what's your story?"
date: 2015-12-14
forum: The Cafe
---

### Post by MoebusNet on 2015-12-14
I travel extensively in my RV; Internet connectivity is always an issue. Most RV parks have WiFi Internet connectivity, but a number of them limit you to one or two devices per RV login. To get around this, I repurposed an antique Bufallo Wireless G HP router (2.4 Ghz only) running DD-WRT as a client to feed an Asus AC56-U wireless router for a LAN (using 5 Ghz only). A single login is all I need to connect the Bufallo router; all my devices connect to the Asus router's LAN. Although the Bufallo is 802.11g with a maximum theoretical connect speed of 54 Mb/sec, most RV parks seem to throttle each client to no more than a 1 Mb/sec effective connection speed anyway. The Asus 802.11ac wireless router offers faster connection speeds when I need them in the LAN to transfer files.

What old hardware have you repurposed?

---

### Post by Dragonbite on 2015-12-14
I've done something similar, except with .

_As a Bridge_
I use an IBM (pre-Lenovo) T40 Thinkpad running Xubuntu to bridge the building's wifi to a centrally located router for my church's annual auction fundraiser.   The building has WiFi available but the signal doesn't reach the main room where everything takes place.  So the T40 picks up the building's wifi and pipes it out (wired) to a more centrally located traditional router which everybody working connects to.  The only thing that really needs the Internet connection is for running credit cards.

_Desktop to web server_
For the same auction I mentioned above I also took a spare CPU and made it into an Ubuntu Server web server.  The web site on the server is the application I use for the auction registration and check-out. Being a web site, the volunteers don't have to install anything on their computer and all of the data is centrally located for access and editing.

I also am setting up a home web server for a couple of reasons but am looking at setting up ownCloud for synchronizing everybody's files (as a form of backup) and a Wiki to place directions and house rules into a central location.  I am considering using a Raspberry Pi though I don't know if it will be powerful enough for my needs.

_Minecraft servers_
So far I have set up 2, but would love to be able to consolidate them into one machine running VMs, Minecraft servers which my son's friends are able to access over the Internet and they work together to build the world.

_Wireless Printer server_
At one point I had my Raspberry Pi operate as a wireless printer server to an old USB-only printer.  It worked great, but the network would go to sleep at times so I had to set a cron job to start a PING command so it would keep awake.

_Firewall and content filter_
I need to set something like this up again, but for a while I had a CPU with 2 NICs and placed it between the modem and the router.  It was a firewall to the outside world, and a content filter to anything that comes through the wireless router (which was everything).  I used IPCop and DansGuardian at the time but I'm not sure if that is still being maintained.  Becuase of its placement, even if the kids' friends brought their phone, tablet of device... if it went to the Internet, it went through the filter.  I really need to set something like this up again.

_Security camrea and other uses_
I've thought about taking the Raspberry Pi and the Pi Camera (or a better USB camera) and set it up in the barn ... networked so I could view anything going on out there.  I know I could use a smartphone but I don't have any.

I keep thinking of things I would love to do, but dont' always get around to it.

The great thing with Linux is being able to set things up like this and not have to worry about operating system licensing or etc.

---

### Post by Dragonbite on 2015-12-14
I really need to get familiar with DD-WRT, because some of my ideas may work on the router instead of a whole separate system.

---

### Post by mastablasta on 2015-12-15
I was recently drooling over business grade aluminium magnesium whatnot framed 2-3 yo laptops. I still need more money for them. anyway decent stuff at affordable price. I would not use Desktop Linux on them. but would sure like to repurpose them. :)

---

### Post by Dragonbite on 2015-12-15
I think my "youngest" computer currently is 5-6+ years old.  At least I have been purging and finally got rid of all of my Pentium III systems a couple of months ago. Now I am working on trying to purge my Pentium 4 systems and single cores (except the Raspberry Pi... that can stay).

---

### Post by d-cosner on 2015-12-15
I re-purposed a Dell Inspiron 531 and have been running Ubuntu 14.04 on it for quite a few months now. Believe it or not, I completely rebuilt it because I liked the look of it. I replaced the motherboard, processor, hard drive, RAM, power supply and repainted the case it's original silver and white. 

I originally paid too much for the Dell believing it was in better condition. Luckily, I found parts on-line very reasonable and traded some spare parts for a quality power supply. Ubuntu 14.04 just happened to run perfect on this hardware so I decided to leave well enough alone. I did spend a little on a passive cooled ATI graphics card with 2 GB of RAM. I call it my retro system!:D

---

### Post by jeff127 on 2015-12-17
I have a netbook (obsolete of course) and I use it as a portable hard drive. I use NFS to share my files from linux-to-linux, from my AMD desktop. Instead of wasting time with 16GB flash drives, I have a netbook with 120GB.

---

### Post by Dragonbite on 2015-12-17
> **jeff127 said:**
> I have a netbook (obsolete of course) and I use it as a portable hard drive. I use NFS to share my files from linux-to-linux, from my AMD desktop. Instead of wasting time with 16GB flash drives, I have a netbook with 120GB.

And handy having a built-in keyboard and monitor for those quick tweaks and don't want to use SSH!

I have one, it is a Gateway, that I haven't found a use for yet.  It's running Ubuntu Mate and does alright but maybe a server would be a better option (wireless too).

---

### Post by yoshii on 2015-12-21
I used to have an HP dc5800 desktop and it was really nice I installed Ubuntu Studio on it and it ran like a charm.  
These days I have an HP EliteBook 6930p laptop and it's from about 2007 but it works OK enough with Ubuntu Studio v14.04.3 that I've been able to use Windows digital audio workstation programs via Wine v1.7.55 and make music.  

It's worked out really well except that it's so old that it's started overheating.  It's only supposed to get up to 167 degrees F safely, but lately it's been getting up to 217 degrees F and this is clearly not good even though it amazingly still runs.  I am going to replace it in a few days with a brand new computer, but it is a testament that old hardware can run some nice Linux stuff.  I also use it with an old printer scanner that my brother gave to me and the scanner works plug and play without needing any special help.    I haven't even tried the printer functions yet.  

I also used to have an old Gateway from around 2000 and it ran Puppy Linux flawlessly.  Puppy Linux in some ways can be more powerful than Ubuntu depending on the distro type but support eventually ends up slightly vaporwarish.  But I still keep an old Puppy LiveCD around in case I ever need a quick fix of anything (it has gParted on it and can connect to the internet).  

Almost every computer I've ever used has been an old refurbished computer and Linux always works out.  I just make sure that my USB devices are Linux compatible or USB Class Compliant.  That reduces driver issues to nill.

---

### Post by DougieFresh4U on 2015-12-21
A friend brought over an old DELL LATITUDE D600
Pentium M
40GB hard drive
512 RAM
1.69 GHz ?
It had Windows Xp and not one update was ever done.
Laptop was brand new and stored away all these years.
Wouldn't play a YOUTUBE music video, so I put Puppy Linux on it.
It was a little sluggish, then some one here at the forum suggested
**ToriOS** and all I can say is WOW! That machine runs super quick.
My friend doesn't really know much about computers,phones, tablets, etc..
His only wish was Firefox which I put on instead of Seamonkey. Youtube
videos play without interruption. Friend just might get a couple of years
use if not more, maybe??

---

### Post by Dragonbite on 2015-12-23
> **DougieFresh4U said:**
> A friend brought over an old DELL LATITUDE D600
Pentium M
40GB hard drive
512 RAM
1.69 GHz ?
It had Windows Xp and not one update was ever done.
Laptop was brand new and stored away all these years.
Wouldn't play a YOUTUBE music video, so I put Puppy Linux on it.
It was a little sluggish, then some one here at the forum suggested
**ToriOS** and all I can say is WOW! That machine runs super quick.
My friend doesn't really know much about computers,phones, tablets, etc..
His only wish was Firefox which I put on instead of Seamonkey. Youtube
videos play without interruption. Friend just might get a couple of years
use if not more, maybe??

I have a D400 which has similar stats and found that maxing out the RAM (2GB) make such a performance benefit that Xubuntu and other distributions work fine on it.  I think I have Fedora w/Xfce installed currently.

---

### Post by Kris_M on 2015-12-28
boring - I sold it on craigslist and thereby got a good friend who subsequently bought my next upgrade. was a great way to downsize!!!

---

### Post by Irihapeti on 2015-12-28
Several years ago, I was given an old laptop with 256MB of RAM and a 30GB hard drive (complete with bad sectors), with XP on it. After replacing the hard drive with a slightly larger one (80GB) and adding a 512MB stick of RAM, I was able to run Xubuntu on it for a while. Eventually it died, but I still have the 80GB drive in an enclosure.

---

### Post by Dragonbite on 2015-12-29
I have 1 machine left that can take IDE hard drives (desktop sized) so I want to go through the drives I have and if there is nothing of value on them, clean and secure them and donate it to some flea market or thingy.  Once they are all gone then I can think about getting rid of it (It's a Pentium 4 and I am in the process of trying to remove all of the single core CPUs except for the Raspberry Pi and some usable laptops).

---

### Post by SantaFe on 2015-12-29
[ATTACH=CONFIG]266452[/ATTACH][ATTACH=CONFIG]266451[/ATTACH]

  Was digging around in my Closet Of Discards when I found my old Dell Dimension 9150.  Note the cool Ubuntu sticker on it?  Seems to be working fine, although I did get a notice that there was an upgrade to ubuntu 14.04.3 available. I think it was KDE 12.04 before so why the ubuntu 14.04.3 update offer. 

  Darned if it didn't update!  Funny thing is, this is an mongrel.  It started out with KDE, then I added Xfce and LXDE.  Got rid of KDE but still have the Kubuntu Plymouth splash screens. ;)  Not on it right now, so can't tell the stats yet.

It's a 3Ghz Dual Core Pentium D, 3 gigs of Ram, a 1 Terrabyte hard drive (via a Western Digital external HD I dropped & broke the outer case.  The drive however sailed right through with flying colors.  Go Figure).

And here's the Display card.
```

:~$ lspci -vnn | grep VGA -A
 1201:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450] [1002:95c5] (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:9018]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV620 HDMI Audio [Radeon HD 3400 Series] [1002:aa28]
    Subsystem: Dell Device [1028:aa28]
    Flags: bus master, fast devsel, latency 0, IRQ 31


```

At least the default drivers are working fine. :D

---

### Post by Dragonbite on 2015-12-30
Love it!

---

### Post by deadflowr on 2015-12-30
> **SantaFe said:**
> [ATTACH=CONFIG]266452[/ATTACH][ATTACH=CONFIG]266451[/ATTACH]

LOL, I have a Dimension E310 that looks exactly like that, with no side panel.
And...
> **Dragonbite said:**
> I have 1 machine left that can take IDE hard drives (desktop sized) so I want to go through the drives I have and if there is nothing of value on them, clean and secure them and donate it to some flea market or thingy.  Once they are all gone then I can think about getting rid of it (It's a Pentium 4 and I am in the process of trying to remove all of the single core CPUs except for the Raspberry Pi and some usable laptops).
In the same boat, the machine I mentioned is the only machine I currently have with those connections.
i decided to clear out a slew of old disks before the new year.

---

