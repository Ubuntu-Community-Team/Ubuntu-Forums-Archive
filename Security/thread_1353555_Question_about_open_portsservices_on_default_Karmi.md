---
title: "Question about open ports/services on default Karmic install"
date: 2009-12-12
forum: Security
---

### Post by jimmy the saint on 2009-12-12
nmap revealed that 

```
1011/tcp filtered unknown
2068/tcp filtered advocentkvm
4343/tcp filtered unicall
```

are "filtered."  I was wondering if someone could shed some light on them for me.  Especially port 1011.  

Thanks

JTS

---

### Post by BkkBonanza on 2009-12-12
Where are you running nmap from? On another machine in the LAN or some public location (different than your public IP)? 

Filtered means that nmap is getting no response from that port. This indicates a firewall is probably dropping packets for those ports. This is different than a closed port where nothing is listening. So if scanning from another public IP it could be your ISP or router that is filtering. If from the LAN then more likely is firewall software on the machine is filtering, ie. dropping packets.

The applications listed for each port are usually just guesses based on what applications are known to default to those port numbers. It doesn't indicate that those applications are actually present. In the case of 1011 it seems that nmap has no default application listed for that number. This doesn't really mean anything either.

For security people often will drop (filter) all packets to all ports not in use so that no information about the presence of the machine is leaked.

---

### Post by jimmy the saint on 2009-12-13
I should have been more descriptive.  

I ran 

```
nmap -A ***-***-***-***
```

From one laptop to another on the same home LAN.  Both have relatively fresh Ubuntu Karmic Koala installations.

---

