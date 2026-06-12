---
title: "Help with connection"
date: 2005-10-28
forum: Server Platforms
---

### Post by RamiroS on 2005-10-28
Hello. I recently setup Breezy as a server. Did all the initial stuff and everything works fine... dhcp gives addresses to the network and the client computers get the ip.... but there is no internet connection. 

From the clients machines I can ping the server and get response from it.

Is this an iptables misconfiguration? dhcp is not working fine? dns? how can I know? what can I do?

thanks

---

### Post by diebels on 2005-10-28
Is the server acting as a router? If so you need to set up NAT. A lot of firewall software do that for you.

---

### Post by dbee on 2005-10-29
But there is "no internet connection" in what sense ?
Can you connect to the internet from your Ubuntu server or is it that you don't have the router config working ?

check your iptables config 

iptables -L

It's blank by default though, so it shouldn't be a problem.

---

### Post by LordHunter317 on 2005-10-29
What else gets information from this DHCP server?  Do those other boxes work?

---

### Post by RamiroS on 2005-10-30
[QUOTE=diebels]Is the server acting as a router? If so you need to set up NAT. A lot of firewall software do that for you.[/QUOTE]
Yes... it should share the connection from the cablemodem to the rest of the network.

Can you recommend me a firewall?

---

### Post by RamiroS on 2005-10-30
[QUOTE=dbee]But there is "no internet connection" in what sense ?
Can you connect to the internet from your Ubuntu server or is it that you don't have the router config working ?

check your iptables config 

iptables -L

It's blank by default though, so it shouldn't be a problem.[/QUOTE]

Yes, the server can connect to the Internet... the machines get an ip from the server , can ping the server, but cannot ping outside... for example yahoo.com

---

### Post by ToXedVirus on 2005-11-05
[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

maybe there is an error with your iptables configuration.

otherwise there is the dns server problem, the computers in the inner network maybe dont get the dns server ips, so the computer cant reach any dns server to lookup wtf yahoo.org is ...

---

### Post by n4dhp on 2005-11-08
Assuming your router address is 192.168.0.1, use the command:
/sbin/route

If the result does not display an ip address under the gateway column,
try this

sudo /sbin/route add default gw 192.168.0.1
Bill

---

