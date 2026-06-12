---
title: "Help with hardware selection for new server."
date: 2011-02-11
forum: Server Platforms
---

### Post by DigDreams on 2011-02-11
I am planning on building a new server to run Ubuntu 10.04 LTS with Plesk but I am not sure what motherboard/cpu to go with. The last time I purchased new hardware for a Linux server it turned out to be "too new" and I wound up having to use it as a desktop and use my fastest desktop as a server. I really want to avoid that this time.
 
Here are the basic requirments:
 
1) Quad Core 64 Bit CPU.
2) RAID 1 (Mirroring), 2x 500gb+ drives, the faster the better.
3) 4gb+ Memory.
4) STABLE!!!
 
Obviously I could care less about the video since I will not be running a GUI. This is strictly a web server. I am looking for a Mobo/CPU reccomendation that is currenly available and that is "known good" for Ubuntu 10.04 LTS.
 
Originally I had a AMD Phenom II X4 955 system speced out, but it looks like Ubuntu does not like SATA III. I normally buy my parts from NewEgg and put the system together myself, and that is what I would prefer to do ths time. The pre-configured systems in my price range have MUCH lower specs than whatI can build myself.
 
I would prefer a hardware RAID so that I can boot up form an Acronis CD and do an image backup without any issues. Stability is the most important thing since my life depends on my server staying up and running (I run a small web hosting/development business).
 
My budget is ~$800 for the whole system. Any suggestions would be much appreciated. I am just trying to get the "best bang for the buck" and am open to AMD or Intel solutions.
 
Thanks in advance!

---

### Post by YesWeCan on 2011-02-11
I set up a 10.04.1 64-bit server for multimedia files, OpenVPN and a Java/Netbeans/Glassfish installation.

I wouldn't call myself an expert but I chose an Intel DH55HC mobo with i5-750 uP. Also a software RAID10 with WD Caviar Black disks and a RAID1 for certain backups. It has been running since mid December without any signs of instability. I haven't been pushing it hard.

I tried to find good info on the web regarding reliability of mobos. I mostly found disparate comments from home users. My experience in the industry led me to favour Intel's engineering quality. I also have a desktop with a Gigabyte mobo, a few years old now, that keeps giving me RAM problems. Indeed, RAM problems seem to be commonplace with lots of boards. I am not a gamer so I am more interested in proper operating margins.

I am looking forward to binning my Gigabyte board when I can buy one of the new Intel Sandy Bridge boards. Looks like I'll have to wait until April sadly.

---

