---
title: "Verifying hardware before install"
date: 2014-03-10
forum: Server Platforms
---

### Post by graystrickland on 2014-03-10
I have an windows server (IBM x3200 M2 - running Windows Small Bus. Server 2003) that I wish to wipe and make a Ubuntu server instead. IBM offers drivers for SUSE Enterprise and RedHat Enterprise, but no other flavors of Linux. How can I make sure that there are the required Ubuntu drivers for everything **_before_** starting an installation? The only thing that gives me heartburn is the IBM RAID controller that shipped with it. I sure don't want to wipe this, then find out that I can't get Ubuntu to install on it.

---

### Post by thufirhawat2 on 2014-03-10
[http://www.ubuntu.com/certification/hardware/200712-202/](http://www.ubuntu.com/certification/hardware/200712-202/)

It looks like your hardware is certified for Ubuntu server 10.04.4. I would just about bet that if it is certified for 10, then 12.04 would most likely also have all the drivers needed, and I would recommend that for a business-level server as it is the current LTS. The only other way I know of to find out beforehand is to google around and see if anyone else has loaded similar hardware with the server edition you are looking at, or to test it yourself with spare/backup equipment (I realize this isn't always an option). 

You might make a USB Live boot disk of the desktop flavor of Ubuntu matching the server version you want, and boot into that USB drive and probe all the hardware, I am pretty sure if the desktop version finds drivers, the server version will as well. 

I have had phenomenal luck with Ubuntu finding drivers. My office had some old NASs that are no longer supported by the company that made them, and the OS on all of them (which was loaded on a CF card) corrupted and basically bricked the stupid things. I was able to load Ubuntu server on a CF card and boot all three NASs, and it found all the hardware, and I was able to configure the RAID and have been using all three NASs for several years now, that is how I got into Ubuntu and Linux in general. I hope this helps, good luck!

---

