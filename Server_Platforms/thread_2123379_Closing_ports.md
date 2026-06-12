---
title: "Closing ports"
date: 2013-03-07
forum: Server Platforms
---

### Post by jcarson99 on 2013-03-07
Hi, 

I have samba installed but it opens ports 139 and 445 when I start it up. I tried using ufw rules (sudo ufw deny 139) but that didn't do anything.

I then tried an iptables rule (iptables -A INPUT -i ppp0 -p tcp --dport 139 -j DROP) and when I do a portscan from outside my network using "nmap -sS" it says those two ports are now 'filtered'. I'm not sure what 'filtered' means.

Anyone know how to close the port or tell samba not to open those ports when it starts up. I want those ports open to my home network but not to the world.

Thanks

P.S. I am using Ubuntu Server 12.04 LTS

---

### Post by diesch on 2013-03-07
"filtered" means that *nmap* assumes those ports are filtered by a firewall as a it didn't receive a *ICMP Port Unreachable* answer. That is causes by the target *DROP* which just drops the TCP package instead of sending a ICMP error message, which violates the TCP standards.

Use *REJECT* instead of *DROP* if you want to be standard conform and don't want to tell everybody that you are using a package filter.

---

### Post by jcarson99 on 2013-03-07
Thanks for the explanation.

I tried REJECT instead of DROP but it still said filtered. I decided to look it up and came across a [website]("http://diaryproducts.net/about/operating_systems/unix/nmap_port_scanner_iptables_firewall") that said to try appending '--reject-with tcp-reset' to my iptables rule. I did that and the port appears closed now.

> iptables -A INPUT -i ppp0 -p tcp --dport 139 -j REJECT --reject-with tcp-reset

---

