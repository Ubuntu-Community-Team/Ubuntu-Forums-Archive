---
title: "Open source firewall with wan failover"
date: 2008-04-03
forum: Security Discussions
---

### Post by hkgonra on 2008-04-03
I am familiar with and like IPcop and smoothwall for a firewall but I am looking for a good open source firewall with wan failover. 
I have two different isp connections coming in and I want a firewall that will handle switching and possibly even load balancing. 
This would be for a business with 5 servers and about 50 pc's.
Anyone have any suggestions ?

---

### Post by netlogic on 2008-04-03
Shorewall with Heartbeat should do the trick. If you are looking for a distro, I heard pfsense supports it. I never used it that way, so I don't know too much about the stability.

good luck

---

### Post by hkgonra on 2008-04-03
Shorewall looks like it is all CLI. I will be honest that scares the heck out of me.

---

### Post by netlogic on 2008-04-03
try pfsense

---

### Post by kevross_33 on 2008-04-04
go to google and search for mhaddons. It provides addons for ipcop (get guardian for IPS and rules selection). In the older distros there is a high availability addon between two ipcops that may be what you are looking for. Have to give it a try.

---

### Post by eDRoaCH on 2008-04-11
I am in the process of checking out a brand new one, ebox, in all the spare time I do not have. 

I havent actually gotten it up and running past testing yet, so I cant give you a solid answer, but it does say it supports wan fallover at least and is based on debian so has all the goodness of apt-get.

From playing with the GUI so far I am very impressed. I just got too sick of IPcop over the years (after i switched from Astaro) you may want to google it up and give it a shot.

pfsense scared me when I did a test instal...

---

### Post by hkgonra on 2008-04-11
> **eDRoaCH said:**
> I am in the process of checking out a brand new one, ebox, in all the spare time I do not have. 

I havent actually gotten it up and running past testing yet, so I cant give you a solid answer, but it does say it supports wan fallover at least and is based on debian so has all the goodness of apt-get.

From playing with the GUI so far I am very impressed. I just got too sick of IPcop over the years (after i switched from Astaro) you may want to google it up and give it a shot.

pfsense scared me when I did a test instal...


How would you say it compares to ipcop ?
I have used that off and on for years and always liked it ease of use.

---

### Post by foolano on 2008-04-13
Hi,

eBox allows you to set up a multipath configuration. You can add as many gateways as you want. If you enable the load balancing feature, the traffic will be balanced between the different gateways. You can even set a weight for every gateway to decide how much traffic you want to send through it. And also, you can use the multigateway rules which allow you to decide which kind of traffic you want to send through every gateway, something like:

traffic from 192.168.0.4/32 destination http via gateway_1
traffic from * destination irc via gateway_2

---

### Post by netlogic on 2008-04-13
I prefer a dedicated firewall and only allow a ssh key authentication for administration. I will not go into a detail. I am not a fan of putting everything in one machine. however, ebox is a nice concept.

---

### Post by foolano on 2008-04-14
If you want to go with a dedicated solution, which is very reasonable, you can install just ebox-firewall. That's the good thing about being modular. Of course, eBox is handy if you want to configure it through its web interface, if you prefer the console to do this I'd recommend something else.

*apt-get install ebox-firewall* will _only_ install the firewalll module and its GUI which is only accessible through your internal interfaces.

---

### Post by HermanAB on 2008-04-14
Hmm, instead of WAN Failover, it is actually better to use WAN Load Balancing.  If you are paying for two links, why not use both?

Details are in the Advanced Routing Howto on tldp.org.  I also attempted to write a guide here: [http://aeronetworks.ca/doublebarrel.html](http://aeronetworks.ca/doublebarrel.html)

Cheers,

Herman

---

### Post by hkgonra on 2008-04-29
Also is there any firewall that will allow me to do this ? 
[http://info.bluezonesoftware.com/docs/html/draw2.htm](http://info.bluezonesoftware.com/docs/html/draw2.htm)

I am currently using a sonicwall but it is aging and needs replacement. 
I know IPcop cannot handle this setup. Is there any open-source firewalls that will ?

---

### Post by socceroos on 2008-07-14
> **hkgonra said:**
> Also is there any firewall that will allow me to do this ? 
[http://info.bluezonesoftware.com/docs/html/draw2.htm](http://info.bluezonesoftware.com/docs/html/draw2.htm)

I am currently using a sonicwall but it is aging and needs replacement. 
I know IPcop cannot handle this setup. Is there any open-source firewalls that will ?
Hey hkgonra,

Looking at the link you've provided, I don't see how IPCOP won't support it. It seems to be a simple set of firewall rules. IPCOP supports setting up DMZ's (calls them the 'orange' network), green is your LAN and red is the WAN. You need to realise that you will need static WAN IP addresses for this setup to work though (get them from your ISP).

Short of that, pfSense will also do this using a nice web GUI for you. I really like pfSense as it will do WAN failover, auto-updates, *awesomely* flexible firewall rules, etc. using a great GUI interface. Plus its built on top of FreeBSD which is (IMO) >= best server distro ever.

---

### Post by socceroos on 2008-07-14
> **HermanAB said:**
> Hmm, instead of WAN Failover, it is actually better to use WAN Load Balancing.  If you are paying for two links, why not use both?

Details are in the Advanced Routing Howto on tldp.org.  I also attempted to write a guide here: [http://aeronetworks.ca/doublebarrel.html](http://aeronetworks.ca/doublebarrel.html)

Cheers,

Herman
Herman, this is only useful in some cases. Sure, if you've got two fat broadband connections with ample download limits then it would be a great idea. But, if you're a small business that has one broadband connection and one 'backup' connection if the main line goes down and your backup connection has a very small download limit then it would be financial suicide (here in Australia it would be anyway) to load-balance your WAN's.

---

### Post by hkgonra on 2008-07-15
> **socceroos said:**
> Hey hkgonra,

Looking at the link you've provided, I don't see how IPCOP won't support it. It seems to be a simple set of firewall rules. IPCOP supports setting up DMZ's (calls them the 'orange' network), green is your LAN and red is the WAN. You need to realise that you will need static WAN IP addresses for this setup to work though (get them from your ISP).

Short of that, pfSense will also do this using a nice web GUI for you. I really like pfSense as it will do WAN failover, auto-updates, *awesomely* flexible firewall rules, etc. using a great GUI interface. Plus its built on top of FreeBSD which is (IMO) >= best server distro ever.


IPcop won't do it because it won't allow the servers in orange to have an external IP address.

---

