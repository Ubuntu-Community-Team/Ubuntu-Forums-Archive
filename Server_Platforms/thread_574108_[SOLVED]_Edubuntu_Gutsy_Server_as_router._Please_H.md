---
title: "[SOLVED] Edubuntu Gutsy Server as router. Please Help!"
date: 2007-10-12
forum: Server Platforms
---

### Post by batonac on 2007-10-12
I'm trying to set up one Edubuntu server as the firewall/NAT/router for my school network in this configuration:

[CENTER]Internet DSL Modem
|
|
|
(Eth1)
|
Edubuntu Server with NAT
|
(Eth0)
|
|
|
Network Switch
|
|
|
Thin Clients and Windows computers[/CENTER]


When I install Edubuntu Gutsy 7.10 on the server the thin clients work perfectly, but when i install Guarddog and Guiddog to set up my firewall and NAT, the thin clients will not boot.  Please help me setup Guarddog and Guiddog or tell me a different firewall/NAT to use.  Which ports do I have to let open on my server in order for LTSP to function correctly with FULL functionality (sound, storage media, printing, booting, X11)????? :confused:

---

### Post by elvis on 2007-10-12
I haven't used Guarddog/Guidedog, but I would say it  is blocking your internal LAN members from accessing the server.  You will need to add a rule in to allow access from all people on your subnet.

For instance, if your machines are all on the 192.168.0.something network, add a rule in that all machines with IP addresses matching 192.168.0.0/24 (or 192.168.0.0 subnet 255.255.255.0) may talk to your eth0 device.

I much prefer Shorewall (aka Shoreline Firewall) as a firewall/NAT management system:
[http://www.shorewall.net/](http://www.shorewall.net/)

Not only is it highly cofigurable, it uses very intelligent config files that are easy to read and give the user an excellent overview of their network at a glance.  Best of all, the documentation provided on the Shorewall website is quite simply some of the best I've ever seen in an open source project.  Highly recommended for any setup from a simple 2-network-card firewall to the most complex of multi-network/multi-port WANs.

---

### Post by Hugolp on 2007-10-15
I agree. Shorewall is one of the best options to manage the linux firewall.

Hugo

---

### Post by batonac on 2008-04-02
I finally just started using Untangle  on as separate computer ([http://www.untangle.com](http://www.untangle.com))

thanks!

---

