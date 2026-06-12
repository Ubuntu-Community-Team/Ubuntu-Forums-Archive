---
title: "For people who have servers"
date: 2009-11-21
forum: The Cafe
---

### Post by mamamia88 on 2009-11-21
what do you use them for?  media?  storage?  also how much of a hit does your electricity bill take leaving it on 24/7?

---

### Post by FuturePilot on 2009-11-21
Storage, backups, print server. I have a second server that is purely a web server.

---

### Post by autonomy on 2009-11-21
backup and web server. I'm not leaving it on yet as I'm just learning and it's not public. It's an old computer that's no longer any good for many everyday tasks.

---

### Post by pizza-is-good on 2009-11-21
IF I had one....
I'd use it for a lot of things.
Data storage
Backups
Have my own cloud?? Maybe??? Is that even possible??? :confused:
If I get one with a very good graphics card and some 16 GB of RAM will do for nice gaming....
I don't know what else.

Maybe someday if I have a dozen thousand dollars laying around, I'll get one....

---

### Post by Frak on 2009-11-21
Print, Web, Development, etc., etc.

Raises my bill by about $3 per month.

---

### Post by Simon17 on 2009-11-21
Printing, storage, webserver, svn.

The impact on the electric bill is pretty marginal.

---

### Post by mamamia88 on 2009-11-21
ok cool thanks guys just wanted to make sure it wouldn't cost too much

---

### Post by 3rdalbum on 2009-11-22
Torrents, storage (of video and audio for streaming to my media box), sometimes some light video encoding.

---

### Post by handy on 2009-11-22
I have an IPCop box running 24/7.

It's a PIII 733 or some such.

I'll take delivery this week of a tool that will allow me to measure the electricity used (in a variety of ways) & to also input what we currently pay for electricity, after which it will spit out the cost over various measured times.

It is going to be very interesting to test the electrical appliances/white goods & such in our house.

***[Edit:]** I also have a FreeNAS setup, though it is only turned on to back up or restore, after which it is turned off & the FreeNAS drive drawers are removed, so as to be safe from any kind of power spike.    *

---

### Post by TuckLive on 2009-11-22
I have two servers.  One is a web server and the other is my IDS

---

### Post by ZankerH on 2009-11-22
Torrents, web server, ssh, SFTP, print server, backup.

---

### Post by dragos240 on 2009-11-22
> **mamamia88 said:**
> what do you use them for?  media?  storage?  also how much of a hit does your electricity bill take leaving it on 24/7?

I use mine for remote access to files, and as a nice web server. It depends how much electricity it uses. If it's a small rack server, not a lot. But if it's a big heavy duty server, maybe quite a bit. I use my netbook as a server. Quite nice.

---

### Post by GreenDance on 2009-11-22
I had a Dell PC as a server, but give that to a family member, now I have an unbranded PC setup as a web server, but it's not online at the moment as it's a bit noisy, so I have to find somewhere to hide it before I can put it online.

---

### Post by fromthehill on 2009-11-22
ASUS I220GC with celeron220(downclocked to 900MHz) with 2x640GB hdd's. powered by a PicoPSU running 24/7 

I use it for torrents, usenet, downloading large files, media server, storage, webserver.
remote access: ssh, vnc, samba

uses only 20-25 watts, uptime is 95 days :)
running ubuntu-server of course:popcorn:

---

### Post by The Real Dave on 2009-11-22
3 servers :)

Main Server - 24/7
Hostname: An-Lar
CPU: 1.7Ghz PIV
RAM: 512Mb DDR
HDD: 2^320Gb RAID0
OS: FreeNAS .69.2
Uses: Storage and Media, Sharing between Windows and Linux :)

Doesn't use a whole load of power because of the way its set up. FreeNAS boots from a disk, loads into RAM and grabs a config from a flash drive. Means that the harddrives can spin down when not being accesed, great for saving power and heat. The CPU clocks down to ~600Mhz when not in use. After a nights sleep, the air coming out of the PSU is almost cold :)

Backup Server - Turned off when not in use
Hostmae: Knox
CPU: 2Ghz PIV
RAM: 384Mb DDR
HDD: 3^320Gb RAID1
OS: FreeNAS .69.2
Uses: Stores backups from 2 Ubuntu rigs, An-Lar and a Vista lappy. 

Gets turned off when not being used so as to prevent electrical damage. Usually sits in my closest until needed. Fan on the heatsink went, so its shutdown until I can afford a new one :)

Other Server - On for the day, off at night.
Hostname: Karmic
CPU: 451Mhz PIII
RAM: 128Mb SD-RAM
HDD: 6Gb IDE (OS + Storage), 2^2Gb USB drives + 9Gb IDE in linear RAID (Storage)
OS: Ubuntu 9.10 Server
Uses: rTorrent automatically loads torrents from a directory thats shared through Samba, and quits once a certain upload limit is met. Folding@Home is running too, trying to give back a bit :) 

Heres a pic of the Karmic Server :) Replaced two small loud fans with a big one and some string :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135526&d=1257807134[/IMG]

---

### Post by CharlesA on 2009-11-22
I've got 1 running 24/7 and it only bumps the bill up by a few dollars a month.

---

### Post by AndyCooll on 2009-11-22
I have a couple of NSLU2's which are lower-powered. One is used a backup of the first. The other one I use as a file server, for torrents, storing my music etc etc.

They're on 24/7. 

:cool:

---

### Post by gn2 on 2009-11-22
I have an NSLU2, used for central file storage for my home network and for storing back-ups.
Power consumption is negligible, a television on standby uses more.

---

### Post by toupeiro on 2009-11-22
at home:

Streaming audio, database, web, backup,  and (drumroll please) NIS!

---

### Post by sefs on 2009-11-22
VPN server.

---

### Post by squilookle on 2009-11-22
I have a web server on my network at home. I currently use it for testing php scripts, and for learning more about php, mysql, apache, etc: by playing with (and sometimes breaking) them.

---

### Post by Simian Man on 2009-11-22
> **pizza-is-good said:**
> If I get one with a very good graphics card and some 16 GB of RAM will do for nice gaming....

Game servers don't need nice graphics cards.  They don't actually need graphics cards at all because the client does the rendering - not the server.

---

### Post by earthpigg on 2009-11-22
i have a desktop that wears the additional hat of multimedia/file server.

---

### Post by NoaHall on 2009-11-22
> **pizza-is-good said:**
> Have my own cloud?? Maybe??? Is that even possible??? :confused:
If I get one with a very good graphics card and some 16 GB of RAM will do for nice gaming....
I don't know what else.

Maybe someday if I have a dozen thousand dollars laying around, I'll get one....

I have 16GB on my desktop computer. I don't use it as a server for my whole house, only if I'm going to use one of my laptops. The rest of the time, it's all good.

---

### Post by MaxIBoy on 2009-11-22
Game server, web server, print server, file backup server, SOCKS proxy, and occasional thin client server (forwarding X over SSH.) Running Ubuntu 8.04.

```
max@server:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 5
model name    : Pentium II (Deschutes)
stepping    : 2
cpu MHz        : 400.922
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
bogomips    : 801.84
clflush size    : 32

max@server:~$ 
```Recently upgraded RAM from 128 to 192 Mb. There was no noticeable performance boost.

---

### Post by sandyd on 2009-11-22
> **The Real Dave said:**
> 3 servers :)

Main Server - 24/7
Hostname: An-Lar
CPU: 1.7Ghz PIV
RAM: 512Mb DDR
HDD: 2^320Gb RAID0
OS: FreeNAS .69.2
Uses: Storage and Media, Sharing between Windows and Linux :)

Doesn't use a whole load of power because of the way its set up. FreeNAS boots from a disk, loads into RAM and grabs a config from a flash drive. Means that the harddrives can spin down when not being accesed, great for saving power and heat. The CPU clocks down to ~600Mhz when not in use. After a nights sleep, the air coming out of the PSU is almost cold :)

Backup Server - Turned off when not in use
Hostmae: Knox
CPU: 2Ghz PIV
RAM: 384Mb DDR
HDD: 3^320Gb RAID1
OS: FreeNAS .69.2
Uses: Stores backups from 2 Ubuntu rigs, An-Lar and a Vista lappy. 

Gets turned off when not being used so as to prevent electrical damage. Usually sits in my closest until needed. Fan on the heatsink went, so its shutdown until I can afford a new one :)

Other Server - On for the day, off at night.
Hostname: Karmic
CPU: 451Mhz PIII
RAM: 128Mb SD-RAM
HDD: 6Gb IDE (OS + Storage), 2^2Gb USB drives + 9Gb IDE in linear RAID (Storage)
OS: Ubuntu 9.10 Server
Uses: rTorrent automatically loads torrents from a directory thats shared through Samba, and quits once a certain upload limit is met. Folding@Home is running too, trying to give back a bit :) 

Heres a pic of the Karmic Server :) Replaced two small loud fans with a big one and some string :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135526&d=1257807134[/IMG]
thats a fire hazard you know.....

---

### Post by sandyd on 2009-11-22
2 Standard 1U rack servers 

Both have the same specs..
```

Intel Xeon Dual Core (cant remember which)
4 GB ram
1 TB HD + RAID array
```

their pretty quiet. that is, until the fan turns on.

---

### Post by PurposeOfReason on 2009-11-22
I use it to mostly host files and work that I'd need anywhere else, screenshots(though I don't know if I'll keep that) and config files. As for power I really couldn't care. Can't be more than a few dollars a month. At least it's nothing compared to everything else.

*Sever is the little box in the corner.

---

### Post by Dharmachakra on 2009-11-22
My mother and sister want me to set one up. Haven't really gotten around to it yet... not quite sure what they want to do with it either.

---

### Post by fiftynine on 2009-11-22
I have two computers which could probably be classified as servers. Both of them are always on. 

First there's this main comp which is hooked up with two 22"s: it's an old p4 d805 pc w/ 700gb hdd-storage. All the parts are from my old computers and/or brothers' computers. I use this pc as a datastorage (SMB fileshare for my laptop etc) on lan, SSH-server, for everyday web browsing and playing music & videos.

Then there's my web server, which acts as a playground for php testing and sharing files online. It's packed with something like 1 ghz celeron and 512mb RAM :-|

I'm currently dreaming about tossing the latter to the discard pile and buying some multicore-cpu-powered hardware featuring a proper graphic card, but I'll wait until i7s are mucho cheaper before jumping onboard that ride..

---

### Post by red_Marvin on 2009-11-22
> **mamamia88 said:**
> what do you use them for?  media?  storage?  also how much of a hit does your electricity bill take leaving it on 24/7?
I have a Sun Ultra 10 @~.3GHz
I use mine as a public web server (plug: sig) some torrenting (legal stuff, linux isos and etqw torrents from id software's own tracker)
Since for some reason file transfer speed is horrible for me in pidgin/msn I also use it quite a lot as an intermediate storage for sending files.

Finally I also have a constantly running screen session, mainly for the sake of keeping an irssi window.

As my electrical bill is baked into my regular rent, I don't know how much it would cost me if I paid it separately, and I haven't measured how much power it needs.

---

### Post by KiraLexi on 2009-11-22
Name: Refinery
Specs: Dual Madison Itanium (rx2600), 6GB RAM
Running: RHEL 5.8 for Itanium (with RHEL 6 components added)

---

### Post by RandomJoe on 2009-11-22
I have several.  The "real" server (Dell Poweredge 600SC - nothing fancy) has 1TB RAID5 for storage of just about everything - movies, music, etc.  Also runs darkice for an audio stream to RadioReference, music server for iTunes, VPN, web server, Zoneminder for some web cameras, whatever else I can cram into it...

Another desktop machine is a dedicated MythTV backend.  Two tuner cards, but only 320GB (RAID0 of some old drives) storage so lots of turnover.  

These two are P4 machines, run a lousy 100W or so idle.  That adds up power-wise, 2.4kWh per day or 72kWh/month.  Electricity here is around 9 cents per kWh, so each of those machines costs me roughly $6.50/month.

I also have an "off-grid" server of sorts.  Actually just an Atom-based "car PC" that is connected directly to my 12V solar system battery bank.  It gathers logs for the weather station, monitors the solar system, and a few other little things.  

This one runs a much more miserly 25W, and the cost is $0, powered by the sun!   (Well, if you leave out the up-front cost of solar panels, charge controllers, batteries, wire...! ;) )

---

### Post by Nozze on 2009-11-23
IRC client
storage
torrents
DC client
FTP server
and it all runs on a old shuttle AMD 3000+ with 1 gigg of RAM. (head less)
And I haven't powered down since I built it (75 days or so).

---

### Post by spupy on 2009-11-23
* web server
* svn
* backups
* thinking of making my own cloud storage, but for friends only. :)

There is no impact on my electricity bill, since I don't run the server. I'm just paying for the machine, and god knows where it is located.

---

