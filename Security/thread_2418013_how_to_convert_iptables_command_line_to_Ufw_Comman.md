---
title: "how to convert iptables command line to Ufw Command line"
date: 2019-04-30
forum: Security
---

### Post by mukky on 2019-04-30
i'm newbie in Ubuntu, I'm using Ubuntu 18.04 on my server,

i have a questions that maybe some Master Ubuntu Expert in this forum could kindly help me out. 

[1]. Is IPtables command line are different with Ufw command line ?..
[2]. If so, how could i translate bellow command line into Ufw command line ?.. (i couldn't have Gui Ufw since i'm using Ubuntu 18.04 server version without GUI).

//VPS\\
sudo iptables -P FORWARD DROP
sudo iptables -A FORWARD -i eth0 -o wg0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i wg0 -o eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 


//port 80 
sudo iptables -A FORWARD -i eth0 -o wg0 -p tcp --syn --dport 80 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport  80 -j DNAT --to-destination 192.168.4.2 
sudo iptables -t nat -A POSTROUTING -o wg0 -p tcp --dport  80 -d 192.168.4.2 -j SNAT --to-source 192.168.4.1


//port 443
sudo iptables -A FORWARD -i eth0 -o wg0 -p tcp --syn --dport 443 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport  443  -j DNAT --to-destination 192.168.4.2 
sudo iptables -t nat -A POSTROUTING -o wg0 -p tcp --dport  443  -d 192.168.4.2 -j SNAT --to-source 192.168.4.1


//client\\
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.4.2
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j DNAT --to-destination 192.168.4.2
sudo iptables -t nat -A POSTROUTING -o wg0 -p tcp --dport 80 -d 192.168.4.2 -j SNAT --to-source 192.168.4.1
sudo iptables -t nat -A POSTROUTING -o wg0 -p tcp --dport 443 -d 192.168.4.2 -j SNAT --to-source 192.168.4.1

Thank you.

---

### Post by TheFu on 2019-04-30
ufw is designed to be simple. It cannot do everything that iptables can.
Both are interfaces into the kernel firewall. 
It is best to pick one to be used on a system and not use the other on that same system.

---

