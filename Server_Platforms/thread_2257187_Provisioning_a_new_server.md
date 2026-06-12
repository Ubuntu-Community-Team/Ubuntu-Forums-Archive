---
title: "Provisioning a new server"
date: 2014-12-17
forum: Server Platforms
---

### Post by cle-ziskind on 2014-12-17
So, ol' reliable is getting less so. I'm resetting it about once a week (locks up with nulls written to syslog), and the hard drives are beginning to flake out. Oh, well.

Hoping for some tips on buying a new server. As usual, money is the limiting factor. eBay, here I come!

I'd like something as least as powerful as what I already have:

# lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    1
Socket(s):             2
Vendor ID:             GenuineIntel
CPU family:            15
Model:                 2
Stepping:              4
CPU MHz:               2196.080
BogoMIPS:              4392.75

(and, of course, I cannot parse the output, but 'someone told me' that I have Xeon processor(s)).

Any suggestions (including requests for more info) from the hardware crowd?

---

### Post by papibe on 2014-12-19
Moved to **Server Platforms**.

---

### Post by Tadaen_Sylvermane on 2014-12-19
Would be better to say what the purposes are then build a server to fit that. If many uses then you need muscle. If just a file server and nothing more then you can do it with an Atom or something equally low powered. For example my server is just files + backup and kvm experimentation. Its a AMD quad Kabini 25w tdp cpu with 8gigs of ram for the vms. An ssd and a 1 tb spinner. Think I spent around 300 bucks total. Perfect for my uses, it really depends though because it can vary so much either way.

---

### Post by TheFu on 2014-12-20
I agree with Tadaen.
If budget is the primary consideration, then knowing the workload for the server is critical.
A few years ago, I built a $150 box (26W) that does NFS and Plex, but could easily do web and email for minimal needs.  It serves media, but cannot transcode video on-the-fly. If transcoding video is important, a Core i5 or better is probably wanted.
OTOH, if this server needs to by a geospacial postgress server then 32G of RAM and a big Xeon is needed.  This will suck power.
I prefer to stay away from Xeon and many AMD CPUs, but I'm sensitive to power use which brings higher noise levels.

For running lots of virtual machines, any desktop Core i5 is plenty for home users. I'm actually running 8 VMs on a Core 2 Duo with 8G RAM. Plenty of power for those.

BTW - your CPU is dual-core. Intel is advertising hyper-threading as more cores. Whether that is true or not, is a marketing question.

So - what are the purposes and what is the budget?

---

### Post by houstonbofh on 2014-12-22
First we need to know what you have.  We know it is a dual core with hyper-threading, but that is all.
```
cat /proc/cpuinfo
```
This will give a lot more CPU info.
```
cat /proc/cpuinfo | grep model\ name
```
This will give the exact CPU.

Also memory...
```
free -m
```

And hard drive.
```
df -h
```

And then, where is it slow?  If it is meeting all of you needs but stability, and Atom based system with low power use may be the answer.  If you need a lot more CPU, but not drive space, an Intel i7 NUC with an SSD may be it in a tiny package.

---

### Post by MAFoElffen on 2014-12-22
A differing perspective--

I still have hard-box servers in the class you are talking about going to... and in the middle of retiring them. (I have 13 servers that that I am updating.) I up'ed my own standards and decided that I needed to thin down. So first I set the bar at being able to run a 64bit OS. Then to be able to do hardware visualization.

Old Xeons (single and dual-core i686'es) run hot and use a lot of power. The older Pentium III were popular becuase they used a lot less power and ran cool. Opteron's traditionally run cool and use comparatively less power. They are limited to 32bit OS'es. That is fine... and still fits the bill for low demand server processing. The old iron I'm retiring, I've been fixing up and selling to friends who want to get their foot in the door with low-end server iron, that still has some life to them.

So the perspective I propose is to look at where you want to be, and what you want to do. It's always a good idea to leave room for growth. If what you have now is sufficient to all you need to do, then there is lots out there for straight over replacement. If you have figured out that by lessons learned, there might be a smarter way to go... That may take something less old, with less wear, more available replacement parts and the ability to do more (more capabilities). The driving factor that sets standards for many with server class equipment is the promise of uptime and the physical security of data and services. Not staying you need the newest or best, but the promise is hard to keep with old iron. You can surely run a server OS on regular hardware, but the redundancy and safeguards built into server hardware, try to ensure dependable uptime.

A machine with room to grow (with later upgrades)... running at a percentage of it's max capacity... has less wear and long-term problems than something running 24x7 at it's max capacity.

---

