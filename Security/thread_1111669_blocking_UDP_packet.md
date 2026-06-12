---
title: "blocking UDP packet"
date: 2009-03-30
forum: Security
---

### Post by sailwind on 2009-03-30
I want to deny a particular malicious UDP packet. I can readily identify this packet from the rest by looking at the data section, where data offset 2 is 0xaa, data[5] is 0xbb, etc. Are there any tools or code samples that can do this? 

Basically, instead of seeing the packet in the following tcpdump, I want to block it. I started to write a proxy but realized I would need to keep sessions and that's a nightmare. Is there an easier way to do this? The firewalls I've seen only block based on port, not on data payload. 


 tcpdump -i eth1 udp[2:1] = 0xaa and udp[5:2] = 0xbbcc

---

### Post by bodhi.zazen on 2009-03-30
Well, a partial answer is yes, you are correct, iptables, and thus all the config tools, block packets by protocol / ip address and not data or payload.

Yes, proxies are considered the best, although less then ideal solution.

Can you block these packets by ip source (blacklist), or protocol ?

the only udp I can think of that you may need would be DNS or possibly samba, so would it work to block all udp and accept traffic on only those protocols you want ?

---

### Post by lensman3 on 2009-03-30
There used to be a iptables project to scan and block the data part of a packet.  There was some talk on using this to block virus's.  I don't know if anything became of it.

---

### Post by lovinglinux on 2009-04-01
> **bodhi.zazen said:**
> the only udp I can think of that you may need would be DNS or possibly samba, so would it work to block all udp and accept traffic on only those protocols you want ?

I don't think is the case here, but some online multiplayer games rely on udp to work properly.

---

### Post by koenn on 2009-04-01
> **sailwind said:**
> I want to deny a particular malicious UDP packet. 
Maybe if you explain why you want to block this particular packet or what it does that you don't want happening, there's a solution to achieve that result without trying to filter payload.

---

### Post by The Cog on 2009-04-01
iptables can do this. Something like (guessing):
> iptables -A INPUT -p udp -m u32 --u32 "2 & 0xFF = 0xAA && 5 & 0xFF = 0xBB" -j DROP
Use man iptables and look for the -u32 tests

---

