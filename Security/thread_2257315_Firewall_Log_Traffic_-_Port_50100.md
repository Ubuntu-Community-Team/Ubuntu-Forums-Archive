---
title: "Firewall Log Traffic - Port 50100?"
date: 2014-12-18
forum: Security
---

### Post by greg67 on 2014-12-18
I've been seeing a lot of traffic dropped by my firewall with a destination port of **50100**.  Below is example with some modifications to protect.

**Any idea what this could be?**  

```

Dec 18 20:24:06 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=182.253.72.138 DST=1.1.1.1 LEN=132 TOS=0x00 PREC=0x20 TTL=118 ID=11909 PROTO=UDP SPT=55346 DPT=50100 LEN=112 
Dec 18 20:24:07 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=2.139.33.97 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=50 ID=60788 PROTO=UDP SPT=45685 DPT=50100 LEN=111 
Dec 18 20:24:13 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=1.58.164.136 DST=1.1.1.1 LEN=129 TOS=0x00 PREC=0x20 TTL=46 ID=31299 PROTO=UDP SPT=6881 DPT=50100 LEN=109 
Dec 18 20:24:16 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=192.222.146.73 DST=1.1.1.1 LEN=129 TOS=0x00 PREC=0x20 TTL=50 ID=0 DF PROTO=UDP SPT=6881 DPT=50100 LEN=109 
Dec 18 20:24:20 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=216.73.205.121 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=48 ID=35077 PROTO=UDP SPT=59696 DPT=50100 LEN=111 
Dec 18 20:24:24 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=70.71.9.21 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=53 ID=46763 PROTO=UDP SPT=43611 DPT=50100 LEN=111 
Dec 18 20:25:04 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=177.95.120.156 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=112 ID=2437 PROTO=UDP SPT=61658 DPT=50100 LEN=111 
Dec 18 20:25:09 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=37.48.64.42 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=51 ID=14734 PROTO=UDP SPT=46833 DPT=50100 LEN=111 
Dec 18 20:25:38 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=122.225.97.76 DST=1.1.1.1 LEN=40 TOS=0x00 PREC=0x20 TTL=100 ID=256 PROTO=TCP SPT=6000 DPT=22 WINDOW=16384 RES=0x00 SYN URGP=0 
Dec 18 20:25:47 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=122.150.33.97 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=46 ID=28596 PROTO=UDP SPT=58485 DPT=50100 LEN=111 
Dec 18 20:25:49 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=122.150.33.97 DST=1.1.1.1 LEN=131 TOS=0x00 PREC=0x20 TTL=46 ID=22891 PROTO=UDP SPT=58485 DPT=50100 LEN=111 
Dec 18 20:26:05 tomato kernel: DROP IN=vlan2 OUT= MAC= SRC=95.87.51.35 DST=1.1.1.1 LEN=134 TOS=0x00 PREC=0x20 TTL=112 ID=37764 PROTO=UDP SPT=64312 DPT=50100 LEN=114 
D

```

---

### Post by TheFu on 2014-12-19
It could be anything.  More info - like is this a DHCP address or static?  How long has the IP been yours? Does anyone on the LAN run bittorrent or a VPN?

---

### Post by kevdog on 2014-12-19
In looking up things, the 50100 port is used by the game Fighter Ace II.  Is someone playing this on your network?  By looking at your logs, the DST 1.1.1.1 would make me think its some broadcast packet or something.

---

### Post by greg67 on 2014-12-19
To answer some questions...

- 1.1.1.1 is just a dummy address I inserted to protect WAN address.  This is traffic with destination of my WAN IP address.
- Occasionally use Transmission, not actively though.  No VPN.
- No one plays the game Fighter Ace II, as fun as that sounds.  I saw that when Google'd the port.  

Going to attempt to release my external IP to see if its a focused attempt on me or bogus/leftover traffic.

---

### Post by bashiergui on 2014-12-19
It's traffic from foreign addresses to you, and they're all clients looking to bind to a service you would have listening on UDP port 50100. If you don't have a service listening on UDP port 50100, then nothing will happen on your computer. You can see in the logs that your firewall dropped all the traffic. So I can't get too excited about it.

If it's a focused attempt on you and you don't have anything listening on port 50100, then you have nothing to worry about. If they start scanning all your ports or try to bind to ports you do have listening, that's where I would use stronger firewall rules and only allow in traffic on expected ports from expected IPs.

---

### Post by greg67 on 2014-12-19
I ended up changing WAN MAC and it solved problem.

---

### Post by TheFu on 2014-12-19
> **greg67 said:**
> I ended up changing WAN MAC and it solved problem.

a) that probably forced a new WAN IP, so the traffic is still going to the old IP (which you don't have anymore)
b) please mark the thread SOLVED.

It was most likely left over torrent traffic.

---

### Post by greg67 on 2014-12-20
> **TheFu said:**
> a) that probably forced a new WAN IP, so the traffic is still going to the old IP (which you don't have anymore)
b) please mark the thread SOLVED.

It was most likely left over torrent traffic.

A)  That's why I did it.
B)  Done.

---

