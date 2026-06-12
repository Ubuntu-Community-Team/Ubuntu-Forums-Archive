---
title: "Estimating hardware for a vm server"
date: 2008-08-20
forum: Virtualisation
---

### Post by victorbrca on 2008-08-20
Hi all,


  I have about 3 server at home that I'm trying to place in one machine. It looks like the best and most secure way would be to use them as a virtual machines on one powerful box. 

  I'm trying to figure out what kind of hardware I would need. I'm not looking for anything performance crazy, but also not too laggy. Is there any way that I can precisely estimate the hardware or is it all by good guessing?


  **This is what I'm looking to have on my setup:**
> => Server Acting Roles (OS Ubuntu Server)

- File-Server
- VM-Server

----------------

=> VMs needed (4)
- Web-ftp Server - OS Ubuntu Server
- XP for light use - OS XP
- Ubuntu desktop for Internet browsing - OS Ubuntu Desktop 
- SSH, squid, music streaming (Jinzora) - OS Ubuntu Server (this could also be run on host server instead if better)


**More information on Web-Server work load I have right now**
> - Hosts images for an external blog. Blog hit count is:
1190 Visits per month
1450 Pageviews per month

- Hosts my web-site. Hit count is:
100 Visits per month
151 Pageviews per month


**sysinfo on two servers**
> **Web-ftp**

Uptime: 6 days 11 hours 33 minutes

Hardware Information
Processors	1
Model		Pentium III (Coppermine)
CPU Speed	601.38 Mhz
Cache Size	256 KB

Memory Usage
Type			Usage	Free		Used		Size
Physical Memory		37%	318.7 MB	184.67 MB	503.36 MB

Load Averages	1.00 1.00 1.00 

Network Usage
Device	Received	Sent		Err/Drop
lo	188.8 KB	188.8 KB	0/0
eth0	1.84 GB		331.52 MB	0/0

################
**Apps** (taken while running squid, a vm XP and music stream all trough ssh)

Uptime: 6 days 11 hours 51 minutes

Hardware Information
Processors	1
Model	Pentium III (Coppermine)
CPU Speed	868.67 Mhz
Cache Size	256 KB

Memory Usage
Type			Usage	Free		Used		Size
Physical Memory		97%	15.82 MB	486.6 MB	502.41 MB

Load Averages	0.42 0.34 0.14 

Network Usage
Device	Received	Sent		Err/Drop
lo	714.55 MB	714.55 MB	0/0
eth0	1.3 GB		3.09 GB		0/0


Thanks for the time reading and any info!! :)


Vic

---

### Post by HermanAB on 2008-08-20
Some rules of thumb:
RAM is more important than CPU speed.
A 4GB RAM machine can typically handle up to 10 VMs.

Hope that helps!

Herman

---

