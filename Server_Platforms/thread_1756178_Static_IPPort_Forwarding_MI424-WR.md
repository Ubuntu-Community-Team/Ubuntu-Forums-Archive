---
title: "Static IP/Port Forwarding MI424-WR"
date: 2011-05-11
forum: Server Platforms
---

### Post by Chamwiz on 2011-05-11
So, I have a MI424-WR modem/router combo from verizon for their fios service.  I'm able to log into the router and set a static ip address for my ubuntu web server.  I then set the eth0 to use the same ip address (from the /etc/network/interfaces file).  The problem I'm having is that for some reason the server and router are not communicating with each other.  The router does not show the server in its active connections.  Ifconfig on the server does not list the designated ip address to the eth0 device.  And when I run "route -n" it tells me that the server is not connected to anything.

If anyone has tried to run a web server through the MI424-WR router before, and was successful, I'd appreciate any help you can offer.  (and any ideas other people might have as well :-P)

---

### Post by Sylslay on 2011-05-12
for some reason the server and router are not communicating with each other???

As I understood You set same IP for serwer and router.

Can You post here config files for interfces and 

IP
Gate
Netmask from Router and DNS As well..

[http://ubuntuforums.org/showthread.php?t=1384085](http://ubuntuforums.org/showthread.php?t=1384085) 

somting about: Re: 3g broadband sharing with 9.10 desktop & networkmanager

just have look:
[SIZE="3"][SIZE="3"]router has to works for Desktop as his gatway, and I used in this example two diffrent DNS setup,
General DNS from ISP for router and Google/OpneDNS for Desktop.[/SIZE][/SIZE]

But I newer manage to setup dynamicDNS for router to have webserwer online with same domain-name.

Good luck.

---

