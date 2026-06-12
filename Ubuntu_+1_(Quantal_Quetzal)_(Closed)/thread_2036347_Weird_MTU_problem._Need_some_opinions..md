---
title: "Weird MTU problem. Need some opinions."
date: 2012-08-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-01
I've been talking alone about some weirdness in browsing and general Internet usage (incomplete pages, packet losses, etc) in the latest Alpha. I think I got to the cause of it. 

```

[17:48:25] ahsl@AL-DESK01:[/usr/lib]: lspci -vvvv | grep -i ethernet -A 10
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 51
    Region 0: I/O ports at e800 [size=256]
    Region 2: Memory at fafff000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at faff8000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
**    Kernel driver in use: r8169**

[17:48:34] ahsl@AL-DESK01:[/usr/lib]: lsmod | grep -i r8169
r8169                  61681  0 
[17:48:46] ahsl@AL-DESK01:[/usr/lib]: ifconfig | grep eth0 -A 8
eth0      Link encap:Ethernet  HWaddr f4:6d:04:3b:03:23  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe3b:323/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  **MTU:1500 ** Metric:1
          RX packets:10122921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7056602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10000 
          RX bytes:9442583282 (9.4 GB)  TX bytes:764659358 (764.6 MB)

[17:49:01] ahsl@AL-DESK01:[/usr/lib]: ping -M do -s **$(expr 1500 - 28)** -c1 google.com
PING google.com (74.125.229.164) **1472(1500**) bytes of data.

--- google.com ping statistics ---
1 packets transmitted, 0 received, **100% packet loss**, time 0ms

[17:50:03] ahsl@AL-DESK01:[/usr/lib]: ping -M do -s **$(expr 1024 - 28)** -c1 google.com
PING google.com (74.125.229.169) **996(1024**) bytes of data.
1004 bytes from mia04s04-in-f9.1e100.net (74.125.229.169): icmp_req=1 ttl=53 time=146 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, **0% packet loss**, time 0ms
rtt min/avg/max/mdev = 146.168/146.168/146.168/0.000 ms

```So, fine, I got a weird strange MTU with my ISP, go fix it, that's the standard answer. The problem is: I don't. PP works OK with MTU 1500 in the same PC. I'm actually under a TP-LINK TL-R470T+ with four WAN connections to different broadband ISPs/Modems (ADSL, Cable (x2), Fiber). I can pmtu discover from this machine to the router. I can even jumbo frame.  

I'm puzzled. It's tempting to tag this is as a new bug, but I'd like to hear some opinions. I'm not skilled in networking.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-01
> **joco1500 said:**
> It's the devil!!!!!!!!!!!!!!!!!!!!!!
Dad?

---

### Post by ventrical on 2012-08-01
:)

I am not running quite the large setup as you are but all  networking seems to be running well here. That's one thing I have noticed since I started using Ubuntu in general - no networking or internet problems. The only anomoly I had  was during Precise official release - the servers were jammed and I thought there was something wrong with my ISP.

  Our systems  with Bell in Canada run through India.  In fact India is a rather large hub and they just had that major power outage. I am just proposing that perhaps if  one of your pipes is patched in through their hubs ?? mabey that may explain the temporary bug ?

Power is back on BTW :)

---

### Post by pressureman on 2012-08-01
Quite a few firewalls will refuse to forward fragmented ICMP, as it has been associated with various attacks in the past (see [https://en.wikipedia.org/wiki/IP_fragmentation_attacks](https://en.wikipedia.org/wiki/IP_fragmentation_attacks) for some examples).

I don't follow the Linux network stack development that closely, but is it possible maybe that recent kernel changes now prohibit fragmented ICMP by default?

---

### Post by effenberg0x0 on 2012-08-01
> **ventrical said:**
> :)

I am not running quite the large setup as you are but all  networking seems to be running well here. That's one thing I have noticed since I started using Ubuntu in general - no networking or internet problems. The only anomoly I had  was during Precise official release - the servers were jammed and I thought there was something wrong with my ISP.

  Our systems  with Bell in Canada run through India.  In fact India is a rather large hub and they just had that major power outage. I am just proposing that perhaps if  one of your pipes is patched in through their hubs ?? mabey that may explain the temporary bug ?

Power is back on BTW :)

Hey :) 
We don't go through India here, too distant. There are network things in Brazil called PIXs, PTTs and PTT-Metro. I don't know if it exists abroad. It's like this: The largest carriers, ISPs, Internet, hardware, software, TV, industry, whatever companies like Google, Yahoo, etc (PIXs) join to build joint server rooms in each of the major cities. This rooms are called PTTs and managed by all companies together. Each of them connect their Data Centers to this PTTs using fiber with redundandcy (it's mandatory to have two independent routes at least). Then all PTTs connect via fiber to form PTT-Metro (also with redundancy), which is country-wide. And PTT-Metro connects via submarine cables to US, Europe, etc (redundancy too). So when I try to reach / traceroute to stuff like google.com, any website hosted on major data centers, hosting companies, large companies like HP, Apple, GM, etc, I'm actually going from my ISP to the PTT it is connected to, then to PTT-Metro, and to the local data center of the target.  Most of the times I will get a response from the local Data Center / cluster. This system runs in parallel to the standard links and routing of the ISPs/Carriers, mostly to reduce latency and allow for SaaS and VoIP. Since they implemented this in 2005 it's rare to see any large-scale Internet problem here. 

Anyway, I can't explain why the same machine, same NIC, same driver, can use MTU1500 on PP and not on QQ Alpha, but I can only think of a local problem, not on the LAN or WAN. (Then again, I'm not a networking expert).  I really think there's something wrong with r8169 in this kernel.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-01
> **pressureman said:**
> Quite a few firewalls will refuse to forward fragmented ICMP, as it has been associated with various attacks in the past (see [https://en.wikipedia.org/wiki/IP_fragmentation_attacks](https://en.wikipedia.org/wiki/IP_fragmentation_attacks) for some examples).

I don't follow the Linux network stack development that closely, but is it possible maybe that recent kernel changes now prohibit fragmented ICMP by default?

I think you are right. It would explain why it works with PP and not with QQ. I still don't get why I would have a max "un-fragmented" 1024 MTU on QQ since my ISPs allow for 1500 (tested on PP). I'll study this and report back.
Thanks for the tip.

Regards,
Effenberg

---

### Post by ventrical on 2012-08-01
Pretty well got the same thing on my VIA ethernet controller.
Then this must confirm a bug of some sort.

```

03:03.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
dale@dale-desktop:/usr/lib$ ping -M do -s $(expr 1500 - 28) -c1 google.com
PING google.com (74.125.226.72) 1472(1500) bytes of data.
From mymodem (192.168.2.1) icmp_seq=1 Frag needed and DF set (mtu = 1492)

--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

dale@dale-desktop:/usr/lib$ ping -M do -s $(expr 1024 - 28) -c1 google.com
PING google.com (74.125.226.78) 996(1024) bytes of data.
1004 bytes from yyz06s07-in-f14.1e100.net (74.125.226.78): icmp_req=1 ttl=54 time=66.5 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 66.575/66.575/66.575/0.000 ms
dale@dale-desktop:/usr/lib$ 

```

---

### Post by ventrical on 2012-08-01
I seen this here:

[https://launchpad.net/ubuntu/quantal/i386/scamper](https://launchpad.net/ubuntu/quantal/i386/scamper)

It's in the repos.

---

### Post by pressureman on 2012-08-01
> **effenberg0x0 said:**
> I think you are right. It would explain why it works with PP and not with QQ. I still don't get why I would have a max "un-fragmented" 1024 MTU on QQ since my ISPs allow for 1500 (tested on PP). I'll study this and report back.
Thanks for the tip.

1024 bytes is a common ICMP size limit implemented on several firewalls (albeit optional).

640K, err, no wait... 1024 byte ping ought to be enough for anybody! ;-)

---

### Post by pressureman on 2012-08-01
You can see the history of the r8169 driver here:

[https://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=history;f=drivers/net/ethernet/realtek/r8169.c;hb=HEAD](https://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=history;f=drivers/net/ethernet/realtek/r8169.c;hb=HEAD)

In particular, this commit back in early March may be relevant:

[https://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=9c5028e9da1255dd2b99762d8627b88b29f68cce](https://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=9c5028e9da1255dd2b99762d8627b88b29f68cce)

I haven't checked whether that ended up in kernel 3.2 - probably not, considering the date of that commit.

Another possible candidate is this, just 8 days ago, which reverts an earlier commit:

[https://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=17bcb684f08649a2ab6a7dcd8288332e72d208f1](https://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=17bcb684f08649a2ab6a7dcd8288332e72d208f1)

1024+ byte pings are working fine for me on an Intel WiFi 5300 - even 1500+ byte pings that would fragment.

---

### Post by effenberg0x0 on 2012-08-01
> **pressureman said:**
> 1024 bytes is a common ICMP size limit implemented on several firewalls (albeit optional).

640K, err, no wait... 1024 byte ping ought to be enough for anybody! ;-)

Yes, I understand. Though I think 1500+ is kind of required in MPLS and some QoS implementations because of overhead added by queue info. I'm looking into IEEE stuff, it's a *lot* of text :\

Regards,
Effenberg

---

### Post by VinDSL on 2012-08-02
> **effenberg0x0 said:**
> I'm puzzled. It's tempting to tag this is as a new bug, but I'd like to hear some opinions. I'm not skilled in networking.
I'm running "tulip" drivers on an ADSL2+ connection, and experienced the same problems you described, for a year or so -- partial screen writes, having to click buttons 2-3 times before anything would happen, yada, yada, yada.  It was driving me crazy!

The cure was to set my MTU to 1492 (network-manager & Wicd).  ;)

```
vindsl@Zuul:~$ lspci -vvvv | grep -i ethernet -A 10
02:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Netgear FA310TX
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at a000 [size=256]
	Region 1: Memory at fc000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 40000000 [disabled] [size=256K]
	**[COLOR="DarkRed"]Kernel driver in use: tulip[/COLOR]**
	Kernel modules: tulip
vindsl@Zuul:~$ ping -M do -s $(expr 1500 - 28) -c1 google.com
PING google.com (74.125.224.164) 1472**[COLOR="DarkRed"](1500)[/COLOR]** bytes of data.
From qwestmodem.domain.actdsltmp (10.0.0.1) icmp_seq=1 Frag needed and DF set (mtu = 1492)

[B][COLOR="DarkRed"]--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms[/COLOR][/B]

vindsl@Zuul:~$ ping -M do -s $(expr 1492 - 28) -c1 google.com
PING google.com (74.125.224.160) 1464**[COLOR="DarkRed"](1492)[/COLOR]** bytes of data.
1472 bytes from safebrowsing.clients.google.com (74.125.224.160): icmp_req=1 ttl=57 time=67.1 ms

[B][COLOR="DarkRed"]--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 67.181/67.181/67.181/0.000 ms[/COLOR][/B]
vindsl@Zuul:~$ 

```

---

### Post by pressureman on 2012-08-02
> **VinDSL said:**
> The cure was to set my MTU to 1492 (network-manager & Wicd).  ;)


PPPoE introduces 8 bytes of encapsulation overhead. If you have a PPPoE DSL connection, and hosts on the LAN are sending 1500 byte packets to the outside world, the DSL router is forced to fragment them into two packets because of the PPPoE header overhead. It has to take 1492 bytes of the original packet, add the PPPoE header and push it onto the wire. Then it has to take the remaining 8 bytes from the original packet, add the PPPoE header, and send that as a second packet.

I've seen some ISPs (and IPv6 tunnel providers) who simply flat out won't handle fragmented packets - which is fair enough, because it requires additional CPU time on their edge routers to reassemble fragments.

You should use an appropriate MTU for your connection, since the TCP MSS (Maximum Segment Size) is calculated from the datalink layer's MTU. A correctly specified TCP MSS will ensure that you don't send TCP traffic that needs to be fragmented.

---

### Post by effenberg0x0 on 2012-08-02
> **pressureman said:**
> PPPoE introduces 8 bytes of encapsulation overhead. If you have a PPPoE DSL connection, and hosts on the LAN are sending 1500 byte packets to the outside world, the DSL router is forced to fragment them into two packets because of the PPPoE header overhead. It has to take 1492 bytes of the original packet, add the PPPoE header and push it onto the wire. Then it has to take the remaining 8 bytes from the original packet, add the PPPoE header, and send that as a second packet.

I've seen some ISPs (and IPv6 tunnel providers) who simply flat out won't handle fragmented packets - which is fair enough, because it requires additional CPU time on their edge routers to reassemble fragments.

You should use an appropriate MTU for your connection, since the TCP MSS (Maximum Segment Size) is calculated from the datalink layer's MTU. A correctly specified TCP MSS will ensure that you don't send TCP traffic that needs to be fragmented.

Pressureman, let me ask you a couple more things:

- Shouldn't an adequate MTU only be relevant in the broadband modem settings or, at most, in both the modem and the first router below it?

- If I have  Gigabit LAN ports on my router, and Gigabit NICs on the LAN clients, as well as proper cabling, and the router has enough CPU and memory to spare, does it really matter the MTU I set in the client? (I mean, considering the possibility of Jumbo Frames between server-client, from 1501 to 9000).

- Example: What if I set all LAN clients to more than 1500? I expect it to be fine on the LAN side. And the router would have to work more to talk to the modem (which would have the imposed ISP MTU limitation). Does it make sense?

- If a proper MTU setting (adequate to each Ubuntu user broadband ISP requirements) is indeed relevant and, thus, is sort of mandatory to ensure the best possible WAN/Internet experience, should some process of MTU auto-adjustment/discovery be part of the OS setup or, more likely, network-manager (when adding a new network)?

Sorry for the ton of questions and thanks for all the help! :)

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-02
> **VinDSL said:**
> I'm running "tulip" drivers on an ADSL2+ connection, and experienced the same problems you described, for a year or so -- partial screen writes, having to click buttons 2-3 times before anything would happen, yada, yada, yada.  It was driving me crazy!

The cure was to set my MTU to 1492 (network-manager & Wicd).  ;)

```
vindsl@Zuul:~$ lspci -vvvv | grep -i ethernet -A 10
02:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
    Subsystem: Netgear FA310TX
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at a000 [size=256]
    Region 1: Memory at fc000000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at 40000000 [disabled] [size=256K]
    **[COLOR=DarkRed]Kernel driver in use: tulip[/COLOR]**
    Kernel modules: tulip
vindsl@Zuul:~$ ping -M do -s $(expr 1500 - 28) -c1 google.com
PING google.com (74.125.224.164) 1472**[COLOR=DarkRed](1500)[/COLOR]** bytes of data.
From qwestmodem.domain.actdsltmp (10.0.0.1) icmp_seq=1 Frag needed and DF set (mtu = 1492)

[B][COLOR=DarkRed]--- google.com ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms[/COLOR][/B]

vindsl@Zuul:~$ ping -M do -s $(expr 1492 - 28) -c1 google.com
PING google.com (74.125.224.160) 1464**[COLOR=DarkRed](1492)[/COLOR]** bytes of data.
1472 bytes from safebrowsing.clients.google.com (74.125.224.160): icmp_req=1 ttl=57 time=67.1 ms

[B][COLOR=DarkRed]--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 67.181/67.181/67.181/0.000 ms[/COLOR][/B]
vindsl@Zuul:~$ 

```
Hi Vin, your results look more reasonable than mine. I envy you 1500-mtu-people lol... I'm stuck on 996 (1024). And only when booting this PC to QQ - It works fine with 1464 (1492) when booting the same hardware to PP. Should I call CISCO hotline? :P

Regards,
Effenberg

---

### Post by pressureman on 2012-08-02
> **effenberg0x0 said:**
> - Shouldn't an adequate MTU only be relevant in the broadband modem settings or, at most, in both the modem and the first router below it?

If your host MTU is larger than that permitted by your connection to the outside world, then fragmentation will have to occur *somewhere*, whether that somewhere is on the DSL router, or a router between your host and the DSL router. The question then is whether your ISP will accept fragmented packets. They *should*, but some don't.

> **effenberg0x0 said:**
> - If I have  Gigabit LAN ports on my router, and Gigabit NICs on the LAN clients, as well as proper cabling, and the router has enough CPU and memory to spare, does it really matter the MTU I set in the client? (I mean, considering the possibility of Jumbo Frames between server-client, from 1501 to 9000).

- Example: What if I set all LAN clients to more than 1500? I expect it to be fine on the LAN side. And the router would have to work more to talk to the modem (which would have the imposed ISP MTU limitation). Does it make sense?

If PMTU discovery is working correctly in your situation, then you should be able to get away with using Jumbo Frames on your LAN, whilst connecting to external hosts should figure out a smaller MTU. If PMTU discovery isn't working... then you really have no choice other than to manually set your host MTU to a lower value.

> **effenberg0x0 said:**
> - If a proper MTU setting (adequate to each Ubuntu user broadband ISP requirements) is indeed relevant and, thus, is sort of mandatory to ensure the best possible WAN/Internet experience, should some process of MTU auto-adjustment/discovery be part of the OS setup or, more likely, network-manager (when adding a new network)?

Yes. DHCP can advertise the MTU for the network via option 26. IPv6 routers can include an MTU size in their Router Advertisements.

---

### Post by VinDSL on 2012-08-02
> **effenberg0x0 said:**
> It works fine with 1464 (1492) when booting the same hardware to PP. Should I call CISCO hotline? :P
1492 is the current MTU/MRU spec AFAIK... ;)


SOURCE (picked at random): [http://tools.ietf.org/html/draft-arberg-pppoe-mtu-gt1492-03](http://tools.ietf.org/html/draft-arberg-pppoe-mtu-gt1492-03)
> Abstract

   [B][COLOR="DarkRed"]Point-to-Point Protocol Over Ethernet (PPPoE), as described in RFC
   2516 [1], mandates a maximum negotiated MRU of 1492.[/COLOR][/B] This document
   outlines a solution to relax that restriction and allow a maximum
   negotiated MRU greater than 1492 to minimize fragmentation in next
   generation broadband networks.


I've tried other MTU figures in the than 1500 range, but 1492 is the only one that works.

So if 1492 works for you, according to the spec (not the proposal), I'd be happy and call it a day.

If 1492 doesn't work, then I would judge that something is janky.

---

### Post by pressureman on 2012-08-02
> **VinDSL said:**
> I've tried other MTU figures in the than 1500 range, but 1492 is the only one that works.

So if 1492 works for you, according to the spec (not the proposal), I'd be happy and call it a day.

If 1492 doesn't work, then I would judge that something is janky.

VinDSL, MTU greater than 1500 bytes will absolutely not work, as 1500 is the maximum size of an Ethernet II frame, and almost certainly what your ISP's edge routers will be using. Also, don't confuse MTU with the size of the ping packet you're testing with. MTU is set on the interface, with ifconfig. If you send a ping packet larger than your host interface's MTU, the host's IP stack has no choice other than to fragment it.

The correct MTU for a PPPoE without any additional tunneling/encapsulation is 1492.

As effenberg0x0 already stated however, it was working fine on a precise kernel, so it sounds more like something that has changed in the driver, that is responsible for MTU > 1024 giving problems.

effenberg0x0, I would try pinging something local, so we can forget about any ISP factors. You should have 1500 byte MTU clear to the LAN interface of your DSL router, as that part of the network is just regular Ethernet. It's only PPPoE on the WAN interface (assuming the PPP session is being terminated there - you're not terminating the PPPoE on your actual host are you?)

Try pinging various sizes between say 900 and 1500 to the LAN interface of your router.

---

