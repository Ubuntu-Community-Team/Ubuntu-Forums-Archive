---
title: "dhcp dnsmasq and firestarter"
date: 2006-03-29
forum: Server Platforms
---

### Post by djlosch on 2006-03-29
i have a ubuntu box as router for my network

internet
   |
ubuntubox
   |
switch
  | | | |
workstations

i setup dhcp and dns forwarding through dnsmasq, and using firestarter opened ports 53, 67, 68 incoming from the lan, and 53, 67, 68 outgoing to everyone.  however, when i restart the ubuntubox, or plug a new machine into the network, i have to shut down the firewall to let the new workstation on the network.  once it gets the ip, everything works fine.  nothing is showing up in events for firestarter.  **what do i do to not have to shutdown the firewall to let someone join?**

on a related note, i have "Enable dhcp for the local network" unchecked in firestarter. if i check it and hit ok, then i get a message "Failed to start firewall.  unknown error has occurred.  please check your network device settings and make sure your internet connection is active."  but as i said, once the clients get on the network, there's no problem.  it's just getting on the network.

---

### Post by Iowan on 2006-03-29
You've probably already figured this out, but it sounds like your DHCP  is coming from outside and the router blocks it.  My server acts as DHCP server, too (although not as firewall/router), but I (think I) had to install a package to do it (DHCP3?).
Are using the reserved IP addresses (192.168.x.x, 10.x.x.x, 172.16.x.x) for your network?

---

### Post by djlosch on 2006-03-29
the ubuntubox (acting as router) has the internal ip of 192.168.1.1 and external ip of whatever my cable company gives me (dynamic).  i set the range to assign to dhcp was 192.168.1.200-254.  with the firewall off, all is fine, but when the firewall is on, the internal machines dont get anything when they try and pull an ip (well they do but its that garbage ip in winxp that gives 'limited connectivity')

---

### Post by djlosch on 2006-03-29
i switched to guarddog and guidedog and everything works fine now.

just follow the howto on the guarddog site.

DONT FORGET TO MAKE THE LAN ZONE

---

### Post by zazuge on 2008-02-03
Sorry for this late reply but so no one will have problems setting up firestarter with dnsmasq

> 
Firestarter has an explicit option to "Enable DHCP for the local 
network" however this turned out to just (re)start ISC dhcpd if you had 
it installed.  No firewall rules related to the protocol are added by 
this option, so it seems a bit of a red herring.

My eventual solution was to add the following line to 
/etc/firestarter/user-pre to explicitly allow the DHCP broadcasts early 
in the INPUT table:
IPT -A INPUT -i $INIF -p udp -s 0.0.0.0 --sport 68 -d 255.255.255.255 --dport 67 -j ACCEPT


[http://lists.thekelleys.org.uk/pipermail/dnsmasq-discuss/2005q3/000431.html](http://lists.thekelleys.org.uk/pipermail/dnsmasq-discuss/2005q3/000431.html)

---

