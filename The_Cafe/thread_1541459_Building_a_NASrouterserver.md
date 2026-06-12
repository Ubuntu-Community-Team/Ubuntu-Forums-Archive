---
title: "Building a NAS/router/server"
date: 2010-07-29
forum: The Cafe
---

### Post by tenmilez on 2010-07-29
I had this idea to build a machine that would replace my wireless router and add some functionality and I'm wondering if I'm overlooking something that would make this a stupid idea (besides the price).

What I hope to achieve is to have a box that does everything my Linksys wireless router does now (wired and wireless access/DHCP server/firewall) while providing the ability to host multiple dedicated servers for games, hosting ventrilo and/or teamspeak dedicated servers, and having a SAMBA share.

I hope that I would be able to take my box to a LAN party, plug everyone in or connect via wireless, they get all their network settings and could be redirected to a home page that details all the servers available on that machine play on.

At home it would be my router/firewall/NAS with more finely controlled access and nifty things like upsidedownternet.

The hardware would be:
Intel i3 550
ZOTAC H55ITX-A-E LGA 1156 Intel H55 HDMI Mini ITX Intel Motherboard
4GB DDR3 1333mhz
32GB SSD for the OS
5x1TB HDD for the NAS storage
Dual 1000Mbps PCIexpress NIC (undecided on which I will use)
802.11b/g/n mini PCIexpress NIC
8port 1000Mbps switch

The idea behind the wired network would be to have one port as the uplink and another connected to the switch to multiply the ports.

---

### Post by Bachstelze on 2010-07-29
It is generally considered a Bad Idea&#8482; to have your firewall/gateway run additional services.  It is a critical part of your network, and any additional services you run, especially big and unreliable things like game servers, will pose a risk in terms of stability, security and performance.

Your Linksys router is probably good enough, run your game and storage servers behind it.

---

### Post by aeiah on 2010-07-29
just make sure you get a good wireless card. an atheros card that uses the madwifi drivers might be advisable. maybe one of those powerful alfa usb cards or maybe even something with two radios (to enable diversity)

you can direct people to a page offering services by using a captive portal thing, like they do for wifi hotspots. i assume if you're going to lan parties though, that no one will want to use wifi, especially since you may be limited to wireless g (unless wireless n access point mode is available under linux for certain cards)

also, whilst it's tempting to use this machine for everything, you may get better performance and stability with cheaper hardware + a good quality wireless router and a hardware gateway running openwrt or dd-wrt. you could probably fit it into the case somehow, and may give you better performance.

i have a small Buffalo WHR-HP-G54DD that comes with dd-wrt. didnt cost too much more than a wifi card and might be better than a wireless card. power it from an internal psu rail or something.

---

### Post by CharlesA on 2010-07-29
> **Bachstelze said:**
> It is generally considered a Bad Idea™ to have your firewall/gateway run additional services.  It is a critical part of your network, and any additional services you run, especially big and unreliable things like game servers, will pose a risk in terms of stability, security and performance.

Your Linksys router is probably good enough, run your game and storage servers behind it.

+1. If the box is compromised, you are totally screwed.

---

### Post by handy on 2010-07-29
> **Bachstelze said:**
> It is generally considered a Bad Idea™ to have your firewall/gateway run additional services.  It is a critical part of your network, and any additional services you run, especially big and unreliable things like game servers, will pose a risk in terms of stability, security and performance.

Your Linksys router is probably good enough, run your game and storage servers behind it.

+1

The more complex you make your firwall/router the more vulnerable it becomes.

I use an old PIII box that runs headless with IPCop doing the specialised firewall router job. I also use a ReadyNAS Duo, as my energy efficient NAS/torrent slave, box. This system works extremely well for my needs (though they aren't the same as yours I know).

---

### Post by demosthenese on 2010-07-29
Your hardware seems overkill for this task.

I've done something similar using clear-os and a mini-itx platform. Low power and fanless is important if you want to leave it on 24/7.

Have a look at [http://www.clearfoundation.com/]("http://www.clearfoundation.com/") for details on the operating system.

[http://www.ulverston.myzen.co.uk/mini-itx/index.htm]("http://www.ulverston.myzen.co.uk/mini-itx/index.htm") has a walkthrough for building a server, but you will need to buy an itx board with multiple ethernet ports if you want to run a router too.

---

### Post by 98cwitr on 2010-07-29
do you really need an SSD and 4GB of RAM? Seems rather expensive for what you're looking to do.

---

### Post by CharlesA on 2010-07-29
> **98cwitr said:**
> do you really need an SSD and 4GB of RAM? Seems rather expensive for what you're looking to do.

No kidding. Not to mention that anything with 5 or 6 hard drives in it is going to be fairly large and heavy.

Why even bother with ITX?

---

### Post by wirepuller134 on 2010-07-29
I agree nothing else needs to run on the edge of the network.  We use Untangle here for our network, to segment it into 4 sections.  this is done on an older P4 machine with 2 GB of ram to handle the traffic.  Our bandwidth usage varies but is usually around 18 Gb a day with around 25 users on daily.

---

### Post by tenmilez on 2010-07-29
I see a couple things in here I've never heard of before so I'm going to read up on those. 

I won't be throwing out my Linksys router so should my new box go down it could be swapped out to bring me back online. I don't run anything critical that a few minutes down time be devastating. 

As far as the overkill hardware: if it were intended to be purely a router/firewall/NAS I could choose older parts, but I'm hesitant to do that when I intend to put dedicated servers on it for games/voice. I've considered the SSD and I may use a HDD that I already have. 

The case I have picked out is m-ITX only and will support all the hardware I've listed. Heavy, yes, but not large at all. Compared to my other machines it should still be lighter anyway. 

I do appreciate the feedback. I've got about a month before I return to the states to do some more research on this. Thanks for the ideas.

---

