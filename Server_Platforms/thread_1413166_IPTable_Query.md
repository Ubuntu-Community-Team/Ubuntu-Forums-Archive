---
title: "IPTable Query"
date: 2010-02-22
forum: Server Platforms
---

### Post by breit on 2010-02-22
Hi Guys,
 
If possible i'd like someone to take a look at my iptable rules, these aren't tested, im pretty sure they'll work, but i want to check before i add them:
 
Eth1 LAN
Eth0 WAN
 
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -A INPUT -j ACCEPT -m state --state NEW,ESTABLISHED,RELATED -o eth1 -p tcp --dport 8080
iptables -A OUTPUT -j ACCEPT -m state --state NEW,ESTABLISHED,RELATED -o eth0 -p tcp --dport 80
iptables -A INPUT -j ACCPET -m state --state ESTABLISHED,RELATED -i eth0 -p tcp --sport 80
iptables -A OUTPUT -j ACCEPT -m state --state ESTABLISHED,RELATED -o eth1 -p tcp --sport 80
 
Thanks in advance :D
 
Edit:
Also is UFW avaliable on the older servers 6.06 LAMP?

---

### Post by d3v1150m471c on 2010-02-22
Why did you reassign port 80?

---

### Post by breit on 2010-02-22
Oops i just realised i didn't nearly give enough info :S
 
The machine is acting as a content filter and i want to force users to go through Dansguardian and Squid.

---

### Post by koenn on 2010-02-22
it's been a long day and my head feels a bit foggy, so maybe I'm wrong here but  I'm not sure  -A INPUT  will work with -o (~output interface)

---

### Post by breit on 2010-02-22
Nope your right, thanks, amended below:
 
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -A INPUT -j ACCEPT -m state --state NEW,ESTABLISHED,RELATED -i eth1 -p tcp --dport 8080
iptables -A OUTPUT -j ACCEPT -m state --state NEW,ESTABLISHED,RELATED -o eth0 -p tcp --dport 80
iptables -A INPUT -j ACCPET -m state --state ESTABLISHED,RELATED -i eth0 -p tcp --sport 80
iptables -A OUTPUT -j ACCEPT -m state --state ESTABLISHED,RELATED -o eth1 -p tcp --sport 80

---

