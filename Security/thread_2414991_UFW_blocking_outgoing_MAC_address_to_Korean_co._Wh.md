---
title: "UFW blocking outgoing MAC address to Korean co. What's up with this?"
date: 2019-03-18
forum: Security
---

### Post by wally1960 on 2019-03-18
This is what my UFW log shows:
```
[   76.525541] [UFW BLOCK] IN=enp2s0 OUT= MAC=f0:79:59:93:39:7c:f8:18:97:ae:02:8d:08:00 SRC=140.90.107.147 DST=192.168.1.65 LEN=88 TOS=0x00 PREC=0x00 TTL=47 ID=14112 DF PROTO=TCP SPT=443 DPT=53594 WINDOW=8 RES=0x00 ACK URGP=0
```

I checked and this MAC address is to a South Korean electronics company. UFW is set to deny incoming and allow outgoing. I'm a newby so if this is a dumb question please excuse me.

---

### Post by Doug S on 2019-03-18
Machine Address Codes (MAC)s are local only. That you reverse looked up what you got in your log only means that the network interface card at either LAN packet source or destination was made in Korea.

For TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake. Thus it is not unusual for a lingering packet to arrive after the session has been closed and forgotten. I would guess that is what occurred here.

---

### Post by wally1960 on 2019-03-18
Thanks for explaining this Doug. This happens quite a few times when I boot up my machine. When I start up Firefox, it seems to take increasing longer to get it up and going. Any Ideas as to what I should be looking for in the log?

---

### Post by Doug S on 2019-03-18
> **wally1960 said:**
> When I start up Firefox, it seems to take increasing longer to get it up and going. Any Ideas as to what I should be looking for in the log?No. Actually, I doubt that there would be any related log entry at all.

---

### Post by jeremy31 on 2019-03-18
I don't think it is possible to see a MAC address from outside of your own network.  Your info also shows SRC=140.90.107.147 DST=192.168.1.65, the DST is likely the computers IP inside the network and the SRC seems to be from noaa.gov

---

### Post by 1clue on 2019-03-18
Typically a mac address is only viewable from the network you're on. Meaning, as soon as it goes through a router of some sort, the "remote" mac becomes the mac of that router. 

The only way I can think of where you could have access to a mac address on another router, is if you have a VPN with 'TAP' access. In that case, your VPN remote endpoint (which is a router of sorts) makes a virtual network card, gives you a virtual MAC address and you appear to be on that network.

I'm going to make a big guess that based on how you worded your post, you're not using a VPN to get to Korea.

---

### Post by TheFu on 2019-03-19
MAC is ethernet.  This is a LAN-only, protocol.  It is usually possible to spoof a MAC address - hackers do this all the time when they visit cafes or coffee shops and hack other customers. As said above, MACs are supposed to be unique in the world. Each vendor has 1 or more prefixes, and then uses serial numbers to make up the MAC.  MACs are about as close to individual identification for a computer on a network as we can get, for good or bad.  Within a LAN, MACs **must** be unique. Ethernet depends on this fact.

You can learn more about ethernet on wikipedia or

If you want a primer on how most IP networking works, [https://twit.tv/shows/security-now/episodes/25](https://twit.tv/shows/security-now/episodes/25) - There is an audio file and human-created transcripts in text, pdf, and html formats, if you prefer.  There are 2 follow-on episodes to explain routing and a few other topics related to networking.  Highly recommended to understand this stuff, since it lays out how almost all networks, everywhere, work.

[https://en.wikipedia.org/wiki/OSI_model#Description_of_OSI_layers](https://en.wikipedia.org/wiki/OSI_model#Description_of_OSI_layers) shows the OSI 7-layer stack.  Much of this was made up, since we usually only care for 3-4 layers in the real world.  Lower layers are the the basis for higher layers.
Ethernet is layer2
IP is layer3.
TCP and UDP are both layer4.

Then people say TCP/IP ... they mean layers 4, 3, 2, 1.

Nobody knows this stuff when starting out and other systems hide the details from end-users.  That's one of the great and terrible things about Unix systems. All the nitty details are there to be seen.

---

