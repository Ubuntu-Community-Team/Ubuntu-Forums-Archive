---
title: "HP Proliant DL160 G6 running Ubuntu Server 11.10"
date: 2012-04-12
forum: Server Platforms
---

### Post by ptyo on 2012-04-12
I have Ubuntu Server 11.10 setup on a HP Proliant DL160 G6 and have been trying to figure out how I can monitor the Raid and hardware of the server. I came across the below:
 
[http://www.ubuntu.com/content/hp-proliant-server-certified-canonical](http://www.ubuntu.com/content/hp-proliant-server-certified-canonical)
 
So I am a little confused. Do i need to download Ubuntu Server 9.04 and install that or should Server 11.10 be able to monitor the hardware? Basically before I setup a full blown KVM with a file server and other stuff I want to make sure I can monitor the raid and other server components so I know if a drive is going bad or other issues are happening. Any help or links would be greatly appreciated I know very little about linux it is new to me.
 
Note when I run ```
 lspci | grep -i raid
```
 
I get ```
04:00 RAID bus controller: Hewlett-Packard Company Smart Array G6 controllers (rev 01)
```

---

### Post by ptyo on 2012-04-12
from the material I have found on the internet I believe the server I have uses Fake Raid. I am going to log into the bios and shut off the raid then research setting up a software raid through Ubuntu Server which I would image will have numerous tools to monitor.

---

### Post by Jonathan L on 2012-04-12
Hi Ptyo

 > I am going to log into the bios and shut off the raid...This sounds like a good plan.

I don't know your particular hardware, but my notes from my last HP server said I couldn't find out how to turn off the RAID in BIOS, and I ended up making single-disk RAID0 "sets" of each disk, then joining them in software RAID.  It worked perfectly well.  Ubuntu 10.04.3 server.

> HP DL320 G2 server 2 Gbyte RAM + 2 x 80 Gbyte disk 

The boot order is pretty fast and it's easy to miss the BIOS prompts for the various controls:
RAM test

Then RAID controller (F8 to config, Escape or wait few secs otherwise) 
 [...]

Has onboard primitive RAID controller: seems impossible to turn  off.  In BIOS controller (Press F 8 Create two 'arrays' of one disk  each, RAID 0, initialise. 


As far as monitoring goes, I've only seen things like this in /var/log/dmesg 
```
[    3.409833] raid1: raid set md0 active with 2 out of 2 mirrors
[    3.409848] md0: detected capacity change from 0 to 240740401152

```

I'll take a look to see what else might be in the logs.

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by ptyo on 2012-04-12
I did use dmesg and grep to look for anything with raid and as it turns out what I have is
The HP Smart Array P410 is an 8 Port Serial Attached SCSI (SAS) RAID controller. The P410 is designed for RAID applications and can be upgraded with the 512MB battery-backed write cache (BBWC) or 512MB / 1GB flash-backed write cache (FBWC) and the Smart Array Advanced Pack.
 
However what I don't know is that Fake Raid? I am still assuming I am better just using a software raid. Currently I am backing my data up from the server then i am going to blow it away and start from scratch...

---

### Post by Jonathan L on 2012-04-12
Hi again Ptyo

I took a quick look at the manual for this P410 and to me it looks like hardware help for RAID: that is to say, a piece of hardware to help do the parity checking and so forth, but without being a full hardware RAID controller.  I repeat it's just a guess, based on the description being gate arrays and so forth.

HP RAID and configuration management and so on is supposed to be excellent IF you have a lot of HP kit and are committed to it and you don't have mixed hardware.  As illustration, these controllers appear to need license keys.  HP says it has special drivers for Novell and Red Hat.

Call me a faithless swine but I'd much rather put my trust in something portable to different suppliers, and that would leave me choosing software RAID (and perhaps buying a bigger CPU if I really believe the performance was affected).  Then when my hardware breaks, I can replace with equipment of whatever manufacturer.

Hope that's of some help.

Kind regards,
Jonathan.

PS.  HP docs I was reading
[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=329290&prodSeriesId=3883890](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=329290&prodSeriesId=3883890)

---

### Post by ptyo on 2012-04-13
Jonathan,
 
I do appreciate all your help. I removed the raid controller from the server then just setup software raid. Things seem to be working great.  
 
Thanks Again.
 
Pete

---

