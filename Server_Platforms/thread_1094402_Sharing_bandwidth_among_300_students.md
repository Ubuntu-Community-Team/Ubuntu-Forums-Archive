---
title: "Sharing bandwidth among 300 students"
date: 2009-03-12
forum: Server Platforms
---

### Post by slimg on 2009-03-12
**Scenario**: A school with 300 students and one internet connection.

**Problem**: Some students use more bandwith than others (P2P, streaming etc.) and end up choking the internetconnection for the other students.

**Sollution**: A VPN-server with two nic's: LAN and WAN, and each studen would be given their own VPN-account.

**Sollution explained further**: The server caps the bandwidth between WAN and each VPN-connection based on the number of VPN-connections on the VPN-server at any given time.

**The math**: total internet connectionspeed / VPN-connections = internet connectionspeed cap for each VPN-connection

**Example**: If the internet connectionspeed is *100* MBps, and there are *17* VPN-connections, each VPN-connection will be capped to *5,88* MBps (*100* MBps / *17*)

So each time a new VPN-connection is established or disconnected, the speedcap for all the connected VPN-connected students would decrease or increase.

Questions I'm having:
[LIST]
[*]Is this a good idea?
[*]Will this work?
[*]Is there any distro out there that does this?
[*]Is there a better sollution to my problem?
[*]What software do I need to get something like this up and running?
[/LIST]

I'll apprechiate any constructive repliy that _might_ help me out

---

### Post by BkkBonanza on 2009-03-12
Do you have a reason you want to use VPNs? Generally you just need QoS (quality of service) functionality in your router to give you traffic shaping to control bandwidth for users and certain types of usage. I'm not sure about appropriate routers for 300 users but I know for a few users people often use a Linksys WRT54GL with modifed open source firmware to get the QoS function. I'm pretty certain that if you have a linux based router solution then you can do the traffic shaping. Perhaps someone else has info on specific software to do that. In this case it sounds like your'e wanting to use VPN software only for the side effect of control traffic when there are routers and software designed to control traffic. The QoS traffic shaping is usually more sopphisticated as well. For example, it allows assigning priorities for certain ips and ports so that maybe email has higher priority than web access and p2p file sharing has lowest priority or some fixed limit so that it can't interfere with web use.

I'd suggest googling and looking into terms QoS and "traffic shaping" routers.

Cheers.

---

### Post by DrMaJ on 2009-03-12
Hi slimg,

Not to take any credit away from Ubuntu (its a great desktop/server platform), but I have created a similar environment & would recommend using OpenBSD 4.3 & PF for this type of service.

Website: [http://www.openbsd.org](http://www.openbsd.org)
PF: [http://www.openbsd.org/faq/pf/](http://www.openbsd.org/faq/pf/)
Recommended reading: [http://home.nuug.no/~peter/pf/en/](http://home.nuug.no/~peter/pf/en/)

Regards,

MaJ.

---

### Post by TwiceOver on 2009-03-12
I like m0n0wall or even pfsense for this type of situation.

---

### Post by HermanAB on 2009-03-12
You should start by installing Squid-Cache.

Cheers,

Herman

---

