---
title: "Iptables and nmap"
date: 2010-08-22
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-22
The following are my iptables rules configured on a server

*filter
:INPUT  DROP [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
#  Loopback 
-A INPUT -i lo -j ACCEPT
# in and out if established  eth0
-A INPUT -m state -i eth0 --state ESTABLISHED,RELATED -j ACCEPT
-A  INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -s  mycompany.dyndns.com -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -s  172.158.24.56 -p tcp -m tcp --dport 22 -j ACCEPT
COMMIT

This  iptable rules are working fine as expected but when my IT manager  checked with the tool nmap to see what ports are open, it listed some  unknow ports(443,995 ...)
It was also showing some ports as  filtered(it itself can't decide if the port is open or close)

am I  doing any mistake in the firewal config?
Is there any other way so  that only allowed ports are listed if checked? ... plz need help...

---

