---
title: "Question about media/storage server"
date: 2012-01-31
forum: Server Platforms
---

### Post by turtle72 on 2012-01-31
Hey, how's it going? I have been in the process of building a server. At first I was only going to do media and stream it, but I might store files and what not on it as well.
My question is that is it possible to run the server off my gaming rig( when I want to game I do not want it to slow my performance), but when I play games I want to have my other computer(well server) take over the task of the server usage. can that be done? because my main rig would have the HD, and the server computer won't have an HD, but all the other necessary parts.

Or if that would be too difficult (though could you just hook it up through a fire wire from mobo to mobo?)

Could I easily run a media server off my gaming rig while gaming without even noticing a performance drop when my server is being accessed?
(I have about 4-5 friends plus myself right now who would try and access this)
My Gaming Rig Parts:
Case: lian li pc-k62
PSU: Corsair 750w
Mobo: ASUS Sabertooth X58
CPU: i7-950 3.06GHz
GPU: HD 4870 1GB DDR5
Sound Card: Sound Blaster X-Fi Titanium 
HD1: WD 500GB
HD2: 2TB
RAM: Corsair 6GB (1333) Tripple channel memory 

Other upgrades I'm thinking about getting soon 120GB SSD and a new HD 7000 series card or a card that's specifically good at playing videos.
 
Also do you think this would slow my network down a lot and notice bad lag during online gaming?  (I have At&T DSL 6GB)

---

### Post by TheFu on 2012-02-01
It depends on the games you play, but I'd wouldn't risk it. I'd 
* put storage on a different machine
* upgrade your LAN to GigE (router and switches and NICs)
* connect the two machines with GigE networking
* use SATA or eSATA to connect the storage, not USB, not firewire
* do not use WiFi networking

Obviously you want to have the games installed on the game machine, not on the network. GigE networking is critical to file server performance, but pretty much any CPU from the last 5 yrs can provide the needed throughput as a file server over GigE.

You mention firewire.  Firewire is slow compared to SATA, eSATA or even USB3.  Firewire is closer to USB2 performance, than eSATA or USB3 performance even if it is 2x faster than USB2.

In my use of USB3, it has queuing problems.  It gets "stuck" from time to time when there are multiple requests (even a simple directory listing stalls it here) and throughput appears to stall for 20+ seconds sometimes.  This could be a USB3 controller issue or something else. I dunno.  However, I never see this with eSATA connected devices. eSATA works with the same performance as internally connected SATA drives. Highly recommended.

FYI, I routinely see 70Mbps writes to network storage over GigE to eSATA connected storage.  USB2 storage only sees 22Mbps writes over the same network.  Firewire should see about 40Mbps.  [http://www.tomshardware.com/reviews/usb-firewire-esata,2534-4.html](http://www.tomshardware.com/reviews/usb-firewire-esata,2534-4.html)

As to video cards - for video playback, it doesn't really matter. A $20 card has the same video playback capabilities as a $300 card.

If your friends on not on the LAN and you are using your WAN upload bandwidth to share videos, your online game performance will definitely suffer. That is the nature of WAN upload performance. It is always limited.  Download WAN performance is less an issue. Also, if everyone is on the same internal LAN, then the router bottleneck won't matter much, if at all.  

Hopefully, others will respond with their recommendations and reasons too.

---

### Post by turtle72 on 2012-02-01
Thank you that was very insightful to me. I knew fire wire is slower, it was the first cord I found laying around that has the same connector on both ends lol.
I am a little bit confused about GigE networking, is that just the LAN speed or w/e? such as 10/100/1000MB? also what do you mean connect two computers through GigE networking?
My current gaming rig does have and ethernet port of 10/100/1000MB and this is my [router]("http://www.bestbuy.com/site/NETGEAR+-+N600+Wireless-N+Dual+Band+Router+with+4-port+Ethernet+Switch+and+USB+Port/1208844.p?id=1218234872989&skuId=1208844"). Though I would probably need to buy a network card for my server since it does have my older parts bought back in (2007).
These two machines for sure are always wired, I only use wireless for wireless made devices such as laptops and ipods.

Well I am the only person who will be streaming it over LAN. For my friends I'll be streaming it over a network.
are there any good guides you (or anyone) know of that can help maximize networking speeds (not just for streaming).

I also don't game too often anymore, so I'm not too worried about it, just when I do I don't want a performance drop.

Other advise and input would be greatly appreciated if there is anything to add =)

---

### Post by a2j on 2012-02-01
> **TheFu said:**
> 
* put storage on a different machine
* upgrade your LAN to GigE (router and switches and NICs)
* connect the two machines with GigE networking
* use SATA or eSATA to connect the storage, not USB, not firewire
* do not use WiFi networking



and I approve this message...

---

### Post by TheFu on 2012-02-02
> **turtle72 said:**
> 
I am a little bit confused about GigE networking, is that just the LAN speed or w/e? such as 10/100/1000MB? also what do you mean connect two computers through GigE networking?

GigE is 1000-base-tx  or 1000Mbps, not MB/sec.  Network bandwidth is always bits/sec, not bytes/sec.

You need a new router. Your current one isn't GigE. You asked for performance, you need a new router to get it. Or you could buy a new GigE switch, but that would add network hops when you don't want that.

> **turtle72 said:**
> My current gaming rig does have and ethernet port of 10/100/1000MB and this is my [router]("http://www.bestbuy.com/site/NETGEAR+-+N600+Wireless-N+Dual+Band+Router+with+4-port+Ethernet+Switch+and+USB+Port/1208844.p?id=1218234872989&skuId=1208844"). Though I would probably need to buy a network card for my server since it does have my older parts bought back in (2007).
These two machines for sure are always wired, I only use wireless for wireless made devices such as laptops and ipods.

Your "server" may have a GigE network adapter already. They've been on motherboards since 2004-ish. If you do need a new NIC, be certain it is supported by Linux in the kernel modules included.

You want the router, server and "gaming rig" to all have GigE network cards, all be connected with wired ethernet and using CAT5e cables or CAT6 cables.  If one of these things is not done, you won't get GigE bandwidth on your LAN.

LAN and WAN and "network" are all the same.  LAN is the network in your house. WAN is the connection from your router to the internet. All of these things are "networks."  

With that said, **where are your friends on the network? ** LAN or WAN?  If they are on the LAN, you're fine with whatever connection they bring for SD content, but for HD content wired ethernet of 100base-tx or better is needed.  WiFi-G will stutter.  WiFi-N may stutter.

If your friends are on the intenet, sharing video is foolish. you don't have the bandwidth with a DSL connection.  For sharing audio, pretty much any broadband connection is fine for a few people.

> **turtle72 said:**
> 
Well I am the only person who will be streaming it over LAN. For my friends I'll be streaming it over a network.are there any good guides you (or anyone) know of that can help maximize networking speeds (not just for streaming).

First you need to walk. Later you can run.  Getting GigE for all your devices is more important by over 10x than anything else you can do.  Later, you can search for settings to control disk cache sizes and ethernet frame caches, if that is needed. I doubt you'll need it.

> **turtle72 said:**
> 
I also don't game too often anymore, so I'm not too worried about it, just when I do I don't want a performance drop.
If you don't want a performance drop, don't run anything else on the same machine, period.  There is no way to run 50 programs and not expect any impact. Sorry - [https://en.wikipedia.org/wiki/There_ain%27t_no_such_thing_as_a_free_lunch](https://en.wikipedia.org/wiki/There_ain%27t_no_such_thing_as_a_free_lunch)

BTW, I'm assuming all these are running Linux, not some other OS.

---

### Post by turtle72 on 2012-02-02
oh yeah my bad man, I sometimes only type MB out of typing habit lol.
Ok I was researching around about what you meant by that, just was not sure if you meant something specific about it. 
My friends are on WAN.
Though I simply do know I could run a music/video streamer off my desktop and store all media files on a separate HDD without even building a server, but what fun would that be?
I just didn't know how much streaming media would actually bog down my network.
As you could probably tell I'm still new to the networking side. I understand the basics of a network. Just when it comes to abbreviations I don't know what they stand for and sometimes I don't know what it's for.
Well I was only asking if there were any guides or what not because that would be learning material for me, hooking up cords to a socket isn't any harder to understand putting computer parts into a pc. I guess I should reword the question to saying "Are there any good networking guides that you (or anyone) else know of that could help me learn?"

As for the OS (sorry forgot to mention) I run dual boot windows 7 and ubuntu desktop on my gaming rig. I am going to run the server with Ubuntu server. Also for the media streaming I was planning to start off with subsonic for a streaming service, though I would like to (not sure how to say/word this) set up my own streamer?

btw going back to my original post up top, I only asked if those options where possible because running two computers at the same time makes my electric bill higher(I have 0% knowledge of how much a computer actually consumes).

I do appreciate the help, Never actually thought of network performance and how that would be affected. I'm definitely going to probably get a new router for GigE because also there is an ISP out here that said they would be getting 1gbps fiber connection soon, and if affordable for my budget might switch to it.

---

### Post by turtle72 on 2012-02-02
Just wondering would it work well if the people who I allow to use my server connected it remotely, would that work any better?

---

### Post by TheFu on 2012-02-02
> **turtle72 said:**
> "Are there any good networking guides that you (or anyone) else know of that could help me learn?"

For a near beginner (you don't know how little you know), it might be good to learn from an organized method.  In the first 50 episodes, [https://www.grc.com/securitynow.htm](https://www.grc.com/securitynow.htm) covers fundamentals of networking. You will learn LAN, WAN, routers, switches, and security considerations.  Ep25+ explain *How the internet works*, LAN Networking, etc.  It wouldn't hurt to start with Ep01 tho.

This podcast is weak on enterprise networking, but for an LAN, you can learn all the basics.  If you really want to understand WAN and larger scale networking, take a few Cisco certification classes.

For most detailed information, google is your friend. There are **Linux Networking HowTos**, but google will find them easily.

Just recall, we all had to crawl, then walk before we tried to run too. If you jump too far ahead, you risk missing important background information.

---

### Post by turtle72 on 2012-02-02
> For a near beginner (you don't know how little you know)No trust me I know I don't know very much reason why I'm trying to learn because I have friends and what not who come to me all the time asking about what kind of hardware they should get for their computers, but when it came to the network part, I always had to tell them sorry.

> For most detailed information, google is your friend. There are Linux Networking HowTos, but google will find them easily.
.
Oh yeah definitely google is my best friend, right when you mentioned GigE I went straight to google and tried to research it, I typically research for a good amount of hours or days before asking people.
I am a computer engineer major so once I get a bit further in it, I'll be taking a networking class, though I might know a lot of it by the time I do take it haha.

---

