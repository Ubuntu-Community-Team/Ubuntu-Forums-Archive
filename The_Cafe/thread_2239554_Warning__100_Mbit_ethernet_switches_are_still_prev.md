---
title: "Warning:  100 Mbit ethernet switches are still prevalent in small towns!"
date: 2014-08-14
forum: The Cafe
---

### Post by 1clue on 2014-08-14
Hi,

Not a support request, feel free to move this if it's not the appropriate place.

If you're in the market for a wired ethernet switch then you need to read this.

I recently ran out of ethernet ports on my wireless router and went looking for what I thought would be pretty common:  A 1gbps 8-port switch.

I live in a small town, needed the switch asap and so I went looking at bring and mortar places.  The choices are limited here:  Walmart, Kmart, Radio Shack and (lucky for me) a one-off business-oriented place.

Walmart and Kmart had nothing in stock.  Radio shack had 2 options, both 5-port and both 100 mbps.  I checked the local office supply store, also a one-off, and they didn't know much about computers so they didn't bother carrying computer supplies.  (?!!!?)  Finally I found a business computer supply place, and they had two gigabit switches in stock: A 5 port and an 8 port.  I literally got the only available 8-port gigabit switch in town.

100 mbps is 1/3 the speed of an 802.11n connection!  How do they still even stock these things?  I literally threw out a few of them a couple years ago because they were useless!


So this is just a heads-up:  If you're thinking about wired networking for speed and/or privacy, be careful because there are still some dinosaurs out there.  On NewEgg, there are still hundreds of switches that don't do gigabit on all ports, or at all.

FYI, 802.11ac speeds are supposedly similar to gigabit speeds.  I don't see it in real practice but it's in the ballpark.

---

### Post by 1clue on 2014-08-14
An interesting side note:  100 mbps Internet is available here too.

Based on their 30 mbps service, which typically delivers 35/6 rates, it's feasible that you could saturate your ethernet switch without saturating your external Internet connection.

---

### Post by pqwoerituytrueiwoq on 2014-08-14
wireless N is not faster than a 10/100 switch, this is due to the overhead in wireless, about 80% of wifi speed is overhead, you will not get much if any over 64% of a 10/100 speed using wireless N

---

### Post by 1clue on 2014-08-15
Didn't know that, but it really makes no significant difference IMO.  If they're that close, there's hardly any reason to use wired except security.

This is crazy to me.  Why sell obsolete hardware?  I can see "also" having a 10/100 because you always have something like a printer, and maybe a couple other devices that don't need full speed, but in the main it should be gigabit.

---

### Post by pqwoerituytrueiwoq on 2014-08-15
hardwire has a vastly lower latency than wifi (ping time)
hardwire is more reliable also

BTW with 300Mbps wireless N at about 50ft i cant get over ~30Mbps on a 60Mbps uplink

most people dont care about speed as much as they care about a connection, typical people are happy with 2Mbps or better

BTW MBR is not a partition, it is a partition table

---

### Post by 1clue on 2014-08-17
I guess I'm not most people.  I use video over VPNs with simultaneous data transfer in my job and need the speed.  I have 30mbps outside and have considered bumping it to 50 or 100 to get more outbound speed.  I also move a lot of data across my lan for work, and 100mbps isn't even close to adequate.

MBR:  You knew what I was talking about though, which is the point.  There's almost no reason to keep MBR partition tables around on modern hardware, and usually very good reasons to use GPT.  Don't really feel like we need to cover that on this thread.

---

### Post by speedwell68 on 2014-08-18
> **pqwoerituytrueiwoq said:**
> wireless N is not faster than a 10/100 switch, this is due to the overhead in wireless, about 80% of wifi speed is overhead, you will not get much if any over 64% of a 10/100 speed using wireless N

QFT.

I have three Raspberry Pi media centres, their ethernet ports are 10/100.  Two of them are hardwired, the third is wireless.  The router the wireless one connects to is 300 N.  The two wired ones will copy a file over the network twice as fast as the wireless one.

---

### Post by t0p on 2014-08-18
> **1clue said:**
>  they're that close, there's hardly any reason to use wired except security.

Ah, don't go thinking that wired will make you safe and secure!  Apparently the old "bounce a laser beam off a window pane" trick is [so advanced now they can hear the click-clack of your keyboard and decipher all your secret inputs]("http://kabelmast.wordpress.com/2014/08/05/laser-bugging-the-passive-way-recovering-audio-from-video/")! And then there are the more traditional espionage techniques - [COLOR=#444444][FONT=Arial][like burglary, sex and blackmail]("http://www.spybusters.com/Laser_Beam_Eavesdropping.html")!   :D[/FONT][/COLOR]

---

### Post by 1clue on 2014-08-18
@t0p, Come on.  I never implied that going to wired ethernet was the only thing I had to do for security, that's silly.  All I was saying is that with wireless anyone with a wifi adapter and a little knowledge can hack your network.  With Ethernet, that specific exposure is gone.

@Speedwell68, I just got into rpi as well with 3xB+ boards.  Not doing media with any of them, but I'm curious as to how well they work?  Any truly good quality audio from them?

---

### Post by uRock on 2014-08-18
I have two 48 port fast Ethernet switches and three 24 port switches. My ISP service is ~3.8MB/s, though they are now offering up to 1 gig. Anything faster than that would be wasting my money. It handles Netlix in HD on multiple devices at once, while still being able to open my security cam server from my phone. I prefer hard wired as well. For me, the downfall of my network would be the fast Ethernet ports on my 2651XM.

---

### Post by nadrach on 2014-08-18
The LAN speed question has been around for as long as I can remember. When 10 Mbps was the norm (which in my case involved SCO Xenix on a Telecomms carrier system) anything over 30% or 3 Mbps actual traffic was considered excessive congestion, because of the inherent design limitations of LAN data packet transfer. One colleague considered LAN as the electronic equivalent of a sewage farm and a windmill, everyone gets a bit and you hope that what arrived at your gate was yours and didnt smell too much. The coming new super uprate to 100 Mbps was greeted with, "Ah ... faster delivery!" But then, he'd sat on a standards committee that considered an alternative point-to-point idea called ATM (I think ... and nothing to do with cash delivery), but went with 100 Mbps  "chuck-it-and-see-who-gets-it" LAN because "we already have the wiring". When early retirement subsequently appeared in the run-up to Y2K, he took it so fast there was a "Bang" on his departure.
Gigabit suffers from backwards compatibility, so still runs into horrendous contention at 30% of capacity.
I get to use a network that involves a VPN punching through a superfast broadband, but the various data mismatches reduce it at times to little better than modem speed. A side-effect of measuring this situation to find a cure has exposed that WiFi is generally hard-wired for a 10:1 favouring of download versus upload. So if you have a NAS on your home router and try to upload a file (especially a large one such as a video file) by WiFi, the buffering that results not only chokes the data flow, but may also corrupt.
The only system that seems to break the mould is/are PowerLAN units. Data flow on these seems to be even-handed (possibly because the manufacturer has no idea which unit will be attached to what and cannot preselect a preferred direction?) and I have had better transmission in a domestic network built with several of these units than with ethernet switches and conventional cabling.
About the only thing I would consider better is to rip out all the CAT5, etc., and use domestic fibre. When that becomes cost-effective, bye-bye LAN; and for me that cannot happen too soon.

---

### Post by 1clue on 2014-08-18
@nadrach,

I remember this time.  In my case it was Linux and IBM A/IX and IBM OS/400.  I also remember when 1Mb/s phone lines were being used even in the office.

I've never set up a VPN on my own, so I don't know about the mismatch.  The ones I use seem to be pretty balanced but are mostly to and from commercial businesses, which to me implies that the balance can be tuned.  Certainly generic ISPs have an imbalance especially on home or small business networks.  I run into that all the time, with or without VPN.

I use 802.11ac for home networking, but that's not the same subnet as my business stuff.  The business stuff (still in my home) runs on wired gigabit ethernet (soho, not managed) and in a couple cases I bond a couple adapters together to relieve congestion point-to-point.  I regularly feel that wired gigabit is not nearly fast enough, but can't afford anything faster.

My ISP is advertised as 30/5, I almost always get 35/6 or better on speed tests, and in real-world transfers to/from a VPN I often get about 80% of that if my math is right with respect to the encryption overhead involved.  I don't know about non-vpn data rates because all my big data is to/from a VPN endpoint.

Skype/Webex/etc is not so high in bandwidth I think.  Skype is terrible for CPU overhead though, I regularly have my laptop go into thermal shutdown.  My wife lives on the wifi side of things, as does all our home-oriented junk.  But there's a lot of that:  My wireless router has had 37 devices listed in the device list, and they were all known to be mine.  TVs, BD-Rs, phones, laptops, cameras, Raspberry Pis, yadda yadda.  That traffic stays out of my gigabit ethernet subnet unless (in the case of 2 rpi's) it's providing a business service.

---

### Post by speedwell68 on 2014-08-20
> **1clue said:**
> @Speedwell68, I just got into rpi as well with 3xB+ boards.  Not doing media with any of them, but I'm curious as to how well they work?  Any truly good quality audio from them?

I am using 3 standard model Bs.  I am running them on Openelec 4.0.7.  The audio is over the HDMI lead into the TV and is perfect, IMHO.  I did use the analogue audio and TBH I found it a little noisy.  However one of the improvements of the B+ is that they have cleaned up the analogue audio.

I will say that a RPI as a HTPC is not an out of the box solution.  But if you are prepared to get your hands dirty with the OS and XBMC they can be truly awesome.  Mine are overclocked to 1Ghz, I have modified the config.txt for better HDMI operation and have modified advancedsetting.xml to include dirty regions.

---

