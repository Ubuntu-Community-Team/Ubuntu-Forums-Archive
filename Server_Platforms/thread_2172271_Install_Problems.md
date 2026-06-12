---
title: "Install Problems"
date: 2013-09-04
forum: Server Platforms
---

### Post by djreplay1234 on 2013-09-04
Hello,

I recently came across two servers I am in the process of formatting and installing Ubuntu on. Although, I have come across this seemingly simple problem I am having trouble with. During the install process the system hangs are various points. From the multiple attempts of installing it either hangs up at 33% when attempting to create partition table. Or at 71% when installing the base system "Ramfs-tools". The specs on the server are:
3Ghz P4 processor
2GB RAM

I have run both a memtest and check the CD for errors. I have even tried multiple .iso's of both Ubuntu 12LTS and 13 still to no progress.

Any help on this matter is appreciated.
Thanks in advance,

---

### Post by TheFu on 2013-09-04
Try the Alternate Install DVD and use a non-PAE 32-bit kernel. Stay with 12.04.3 and do not load a GUI. A pure WM environment should be fine - might be ok with LXDE, depending on the GPU.

Calling anything with a P4 CPU a "server" is just ... .... ...  wrong. ;)

---

### Post by bab1 on 2013-09-04
> **TheFu said:**
> Calling anything with a P4 CPU a "server" is just ... .... ...  wrong. ;)

Why do you say that?  What is *your *definition of a "server"  There are thousands, maybe even millions of servers out there with less than P4 spec cpu's.  I have 2 homebuilt NAS units with P3 cpu's that work perfectly fine as file servers .

---

### Post by TheFu on 2013-09-04
Only because you asked ... I've specified and had the company purchase lots and lots of servers. As an Integration and technical architect, it was my job for about a decade.  Different sized servers based on the need.
* Superdome Server - [https://en.wikipedia.org/wiki/HP_Superdome](https://en.wikipedia.org/wiki/HP_Superdome) - bought 5 of these - complete waste of money for the purpose.

IBM p550, Sun Fire 2xx/4xx/6xx, HP N4000 (aka rp7400), rp7410, K580, V2600s, Dell 2950, IBM xSeries x36xx, HP DL3xx, DL5xx

For home: 
* Alix 2d13 - [http://www.pcengines.ch/alix2d13.htm](http://www.pcengines.ch/alix2d13.htm) - bought a few of these to run pfSense for clients (x386) (3W of power)
* AMD E350 APU - [http://arstechnica.com/civis/viewtopic.php?f=11&t=1179621](http://arstechnica.com/civis/viewtopic.php?f=11&t=1179621) - Built one of these, but it is just an XMBC box, not a server. (25W of power at boot)  Would also be good for running an Asterisk PBX for a small company.
* A few Core i5 and Core 2 Duo desktop-class machines here. No Xeon. Virtualization is the key requirement, but redundant power, networking, disk access just isn't cost effective.

Found this [http://www.tomshardware.com/reviews/intel-cpu-power-consumption,1750.html](http://www.tomshardware.com/reviews/intel-cpu-power-consumption,1750.html)  about power use. Newer CPUs are much more efficient, until we add monster GPUs.  The point is to have the system sized for the purpose, but watch total costs over the lifetime of use.  At a few clients, we've replaced 20+ "servers" with 2 real servers and sold off their 20K VA UPS for a 4K VA UPS. Huge savings, plus the replacement systems were faster and actually under warranty. Critical for a business.

The annual power use on a P4 can probably offset the cost of a new low-power system - Atom, AMD-E series can be had for cheap - $120 or less. The Alix boards are more pricy, special use and hardened for terrible environments. The atom and AMD-E series are probably 2x-4x faster than a P4 too.  I live in a place with EXTREMELY cheap hydroelectric and nuclear power and it is worth it here to build-new systems. Run the numbers for your situation, it is different, but probably higher costs in cooling and electricity.  Replacing a 250W system with a 25W system can save $10/month.  Just sayin'.

The P4 was a great CPU for the time.  Free-cycle those puppies to someone without any computer at all.

---

### Post by bab1 on 2013-09-04
> **TheFu said:**
>  ... I've specified and had the company purchase lots and lots of servers. As an Integration and technical architect, it was my job for about a decade.  Different sized servers based on the need.
...

:-)

The question was semi rhetorical to begin with.  I guess your idea of a "server" is really *server grade hardware *.  So be it.  

My idea of a server is the process running in the background waiting for a client request.  I worked in an organization that was 95% SUN Microsystems that supported 25,000+ users.  Hardware was always referred to as "server grade"  The servers (processes) most always would reside on that hardware.  But not always.  We had plenty of Sparc workstations that were used in smaller departments as local file servers.
> 
The P4 was a great CPU for the time.  Free-cycle those puppies to someone without any computer at all.
This may be the best hardware available for @djreplay1234.  The OP may be the recipient of the recycling you have suggested.  Who are we to judge.

---

### Post by TheFu on 2013-09-04
In another thread, oldfred recommended checking the BIOS settings for AHCI ... I can't remember if a P4 has that option or not, but thought it was worth a mention.

Rather than installing, can you try a liveCD on the machine?  If it works, then the disk controller, cables, and HDDs are the likely issue.

---

### Post by djreplay1234 on 2013-09-04
I am using the Ubuntu server distro which does not have a GUI included. Take a little load off of the GPU and I do not need a GUI for a server platform. I will however attempt to use the live CD with a GUI in attempts to maybe pinpoint the problem. I will post the results when I get home tonight. 

As mentioned earlier, I am a recipient of recycled parts, I can't say that free is too expensive. I understand that a newer system would be more energy efficient, but these servers are going to be on very low load. They are replacing my last P4 server that is still running for small things like NAS backup and the occasional gaming server.

---

### Post by trundlenut on 2013-09-05
Bit of an oddball suggestion, but I had an old server which I had all kinds of random problems installing ubuntu server on which turned out to be due to the cd drive being full of dust and the lens was mucky.

Memtest ran fine and when I checked the discs on another machine they were all fine.

---

### Post by mörgæs on 2013-09-06
> **TheFu said:**
> Try the Alternate Install DVD and use a non-PAE 32-bit kernel. Stay with 12.04.3 and do not load a GUI. A pure WM environment should be fine - might be ok with LXDE, depending on the GPU.

Calling anything with a P4 CPU a "server" is just ... .... ...  wrong. ;)


No, stay with a PAE version. all Pentium 4's support PAE. 

The only recent processors without PAE are some of the Pentium M's, which were only used in portables.

A Pentium 4 can be a great web- or fileserver. No need to ditch it.

---

### Post by mörgæs on 2013-09-06
> **djreplay1234 said:**
> I understand that a newer system would be more energy efficient

Yes and no. New hardware is more efficient per unit of calculation power, but not in total. Old hardware is often the best choice for a light work load if saving electricity is the goal.

[http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html](http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html)

---

### Post by d4rk0wl on 2013-09-06
Well looks like I found the problem. This is OP djreplay1234. This thread was posted under my old account I thought I lost.

I am not to sure what it was, maybe the HDD didn't like the previous install of Windows. So I used DBAN to completely write the drive to 0's and then tried installing again. It looks like this trick worked on both machines.

Thanks for the help,
d4rk0wl

---

