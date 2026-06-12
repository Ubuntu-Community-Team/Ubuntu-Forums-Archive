---
title: "What is a server's bottleneck (hardware)?"
date: 2009-07-24
forum: Server Platforms
---

### Post by garfonzo on 2009-07-24
Well, the title somewhat says it all. But, for good measure, I'll add some more details.

I have a small server for file sharing at home. It serves files to 3 to 4 computers with Win XP and Vista. I have no problem getting everyone to play nice. 

The main usage of the server is for general file storage and streaming music. Since music files are low bit rates (192 or so, depending on the file) that isn't taxing to the system. 

HOWEVER... If I want to stream a movie (DVD quality, not compressed) now I have a speed issue.

Lets assume that we have a Gigabit router, wired to a gigabit network card on the server. And, for sake of argument, lets say that all computers have gigabit network cards wired into the router too (through the walls or whatever). 

Now, I would argue, the bottleneck becomes the server's ability to serve the file. 

-----

In the above situation, what part of the server's hardware becomes the bottleneck? The hard drive I/O? The motherboard bus? The network?

I look forward to an interesting discussion...

---

### Post by Cheesemill on 2009-07-24
Gigabit networking has a theoretical maximum of 125 MB/s so you can expect to see speeds of around 100 MB/s across the network in ideal conditions.

I think that your bottleneck will probably hard drive I/O, I know that's what it is on my file-servers at work.

---

### Post by samosamo on 2009-07-24
Without any testing, how can you be sure if it's hardware?  It could be a bad config in the software.  You don't tell us what protocol you are using to test.  All protocols have their own limitations.  You mention you are using Windows so I assume you are using Samba.  Samba will never saturate a gigabit network.  It is likely that Samba is your problem.

And what kind of person would I be if I didn't ask: did you google "how to identify bottlenecks in linux"

---

### Post by Zenze on 2009-07-24
Is this a theoretical situation?

It would probably be your harddrive read times as Cheesemill said. However, that shouldn't be slow enough to make you bottleneck.

I assume you are using samba? I am running a samba server in my house to store media and stream it to other computers. But it is on slow hardware and a 5400 rpm drive and I can stream 1080p video just fine.

Maybe you have a faulty hdd or another piece of hardware?

---

### Post by dragos2 on 2009-07-24
> **Cheesemill said:**
> Gigabit networking has a theoretical maximum of 125 MB/s so you can expect to see speeds of around 100 MB/s across the network in ideal conditions.


Yes and no.

It depends on the usage.

---

### Post by snkiz on 2009-07-24
I actually did have this problem turned out my network card that was spoused to be 10/100  was only connecting at 10. Swapped the card and all is good. My server is (your going to laugh) a pIII @ 800Mhz w/160Mb ram. Its serves my desktop, a laptop, a ps3 and the occasional visitor. I'm running apache, bind, dhcp, samba, deluge, and mediatomb. I can even run a remote instance of firefox if need be, no bottlenecks.... ever.

---

### Post by toupeiro on 2009-07-24
> **dragos2 said:**
> Yes and no.

It depends on the usage.

+1

Windows networking?  SMB1.0?  40MB tops..  NFSv3+, SMB 2.0, maybe 110-115MB but you need vista/7 and/or Server 2008 on both ends of the connection in order to take advantage of SMB2 (or some sort of NAS that can handle the protocol.  Might look into Nexenta.)

In either case, if you're not using SSD for your OS, then get some nice, fast 10K-15K SAS disks and it will help out quite a bit.  If its an older server, FSB architectures have changed a great deal, ESPECIALLY Intel servers...

---

### Post by windependence on 2009-07-25
> **snkiz said:**
> I actually did have this problem turned out my network card that was spoused to be 10/100  was only connecting at 10. Swapped the card and all is good. My server is (your going to laugh) a pIII @ 800Mhz w/160Mb ram. Its serves my desktop, a laptop, a ps3 and the occasional visitor. I'm running apache, bind, dhcp, samba, deluge, and mediatomb. I can even run a remote instance of firefox if need be, no bottlenecks.... ever.

I wouldn't laugh at you at all. People (especially new to Linux) use wayyyyy overpowered hardware these days. This is not Windoze. Linux will do everything you are doing and more on very little physical hardware especially if you aren't running a GUI.

-Tim

---

### Post by tubezninja on 2009-07-25
> **garfonzo said:**
> 


In the above situation, what part of the server's hardware becomes the bottleneck? The hard drive I/O? The motherboard bus? The network?

I look forward to an interesting discussion...

As someone who deals with large data sets and video files, I can definitely say that the bottleneck, given current hardware, will almost always be the hard drives.  If you have multiple hosts access files on the same server, the hard drive will start to grind before anything else becomes an issue.  Especially if the peers have write as well as read permissions.

If you're seeing a bottleneck, check your disk io.  often times the solution is to set up the relevant file systems in RAID configuration to peed up access.  Depending on how you set it up, reliability can be increased too.

having more RAM maight also help a bit too, as it will allow the server to cache in unused RAM.

> **windependence said:**
> I wouldn't laugh at you at all. People (especially new to Linux) use wayyyyy overpowered hardware these days. This is not Windoze. Linux will do everything you are doing and more on very little physical hardware especially if you aren't running a GUI.

I disagree with this.  Sure, linux can be configured to be less demanding than a current WIndows configuration, and so older hardware can last you longer.  However, linux also makes excellent use of beefy hardware, and there are plenty of applications, *particularly* in a server environment, where it pays to have really good hardware.

I wouldn't laugh at a PIII server.  But likewise, I definitely wouldn't laugh at a multicore, multi-GIG RAM, RAIDed linux server either.  In fact, I've built/purchased/configured quite a few, and have pushed them to their limits.  It's quite satisfying. :)

---

### Post by snkiz on 2009-07-25
Well thanks for the vote of confidence, I'm very proud of my little intranet, my next project to tackle is going to be mysql & dupral, I'll break it yet :D

---

### Post by Thirtysixway on 2009-07-25
If you have a solid state drive, I would expect transfer speeds to increase.

---

### Post by garfonzo on 2009-07-25
Thanks for all the great replies. It gives me a lot to think about. 

Some more information, based on the replies, about my setup. My server, at the moment, is a 733 mhz chip of some sort with minimal RAM. After what all of you have said, I'm thinking that I could see a bottleneck in two possible spots: 
1) Samba
2) Hard drive I/O

As it is, my hard drives are SATA, but in USB 2 cases. The server tower only had IDE connections and so I figured a USB2 card would help disk I/O.

This server is without a GUI, and I access it via putty. So, I'm trying to dedicate all its resources to file serving. I'm pleased to hear (and knew to an extent) that Linux is quite capable of working smoothly on low end systems. 

I may have the opportunity to get my original server back (my original desktop may get fixed - I found the receipt with the warranty). If that is the case, I'll have a quad core with 2GB ram and SATA drives. I suppose, for ultimate speed (outside of using RAID) I could upgrade to 10K disks. 

Anyway, thanks for all the good discussion. Keep it coming!

---

### Post by ktrnka on 2009-07-31
> **garfonzo said:**
> Thanks for all the great replies. It gives me a lot to think about. 

Some more information, based on the replies, about my setup. My server, at the moment, is a 733 mhz chip of some sort with minimal RAM. After what all of you have said, I'm thinking that I could see a bottleneck in two possible spots: 
1) Samba
2) Hard drive I/O

As it is, my hard drives are SATA, but in USB 2 cases. The server tower only had IDE connections and so I figured a USB2 card would help disk I/O.

This server is without a GUI, and I access it via putty. So, I'm trying to dedicate all its resources to file serving. I'm pleased to hear (and knew to an extent) that Linux is quite capable of working smoothly on low end systems. 

I may have the opportunity to get my original server back (my original desktop may get fixed - I found the receipt with the warranty). If that is the case, I'll have a quad core with 2GB ram and SATA drives. I suppose, for ultimate speed (outside of using RAID) I could upgrade to 10K disks. 

Anyway, thanks for all the good discussion. Keep it coming!

The network will be the first bottleneck. Not sure why everyone is suggesting that it would be the Hard Drive I/O. The initial spin up might be the slowest part but sustained data read/writes kick the crap out of the network performance. USB has a lot of overhead so that is where the second bottle neck would be on your machine.

---

