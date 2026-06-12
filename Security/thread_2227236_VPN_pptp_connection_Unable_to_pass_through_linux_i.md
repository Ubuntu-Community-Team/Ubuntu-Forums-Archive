---
title: "VPN pptp connection Unable to pass through linux iptables"
date: 2014-05-31
forum: Security
---

### Post by waleed_tottihotma on 2014-05-31
Hello guys

I have set up a windows VPN server behind Linux - Ubuntu box that is working as firewall and proxy server. Now I want people from outside to be able to connect to the VPN server, but the connection is not being established and I get on the client an error 619. I have checked the problem on the internet and it seems a firewall issue. 
 
here is below the information about my setup
 Firewall-External-IF-IP: 172.16.1.100
 Firewall-LAN-IF-IP: 192.168.1.1
 VPN-Server-IP: 192.168.1.10

 So what can I do to allow VPN connection to pass through Ubuntu iptables firewall to the VPN Server.?

 hope that I find the solution here ....!! :(

---

### Post by bashiergui on 2014-06-01
> Firewall-External-IF-IP: 172.16.1.100That is a private range IP. It will not route over the internet. 

Have you forwarded the VPN port through your router so that it's facing the internet?

---

### Post by waleed_tottihotma on 2014-06-03
> **bashiergui said:**
> That is a private range IP. It will not route over the internet. 

Have you forwarded the VPN port through your router so that it's facing the internet?


I have a DSL router in front of my firewall that has a public IP address and has the port 1723 forwarded to the firewall EXT-interface 172.16.1.100 and GRE protocol allowed.

---

### Post by bashiergui on 2014-06-03
Disable the iptables rule and see if you can connect. Then post your iptables rules to see if anyone sees the problem.

---

