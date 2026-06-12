---
title: "stand alone ubuntu-server as a firewall w/ iptables"
date: 2007-09-12
forum: Server Platforms
---

### Post by kirbs on 2007-09-12
:guitar:

Hey folks, I have been trying to set up a feisty fawn server as a stand alone firewall. my network looks like this

(the vast internet)
             |
(linksys wireless router) -)))     wireless clients
   |             |
two wired machines

I want to have it like this:


(the vast internet)
             |
(firewall-server)
             |
(linksys wireless router) -)))     wireless clients
   |             |
two wired machines


I have two NICs, eth0 is the internet, eth1 is plugged into the router. I can dhclient eth0 and receive an IP.
I don't know how to set up my router or firewall correctly! The router assigns addresses to internal machines but they do not have internet access. I don't think the router is getting any packets from the server?
I have tried some iptables commands and echo-ing 1 to ipv4 forward. Any suggestions as to router and firewall settings?

I use dd-wrt on my linksys wrt54g linux router.
thanks for the time!

---

### Post by robert_pectol on 2007-09-12
This may help you:

[http://rob.pectol.com/content/view/5/28/](http://rob.pectol.com/content/view/5/28/)

On top of that, use something like dnsmasq on the firewall/router to provide dhcp and DNS services to your internal machines.  Good luck.

---

### Post by kirbs on 2007-09-12
thanks alot, i'll let you know how it goes

---

