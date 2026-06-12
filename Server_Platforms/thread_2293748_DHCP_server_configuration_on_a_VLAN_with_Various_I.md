---
title: "DHCP server configuration on a VLAN with Various IP Series"
date: 2015-09-07
forum: Server Platforms
---

### Post by Johnson_prabu on 2015-09-07
how to configure many IP series on a DHCP server.

In my office i've configured a DHCP server which is working fine. I need to add more Class c private IPs on it. Can you guide it....

Current setup: DHCP server iP 192.168.3.9

DHCP Range - 192.168.3.11 - 200

[B]Req setup

need to add 192.168.2. * IP series on the same server.[/B]

---

### Post by howefield on 2015-09-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2015-09-07
It would help if you specify which program are you using for dhcp. The built-in in ubuntu? How was it called, isc-dhcp-something?

Also, do you plan to have different dhcp for different VLAN? Otherwise you will run into conflict with more than one dhcp on same LAN/VLAN. List the VLAN interfaces so that people have more info to help you.

---

### Post by SeijiSensei on 2015-09-08
Why not start with the remaining .3 addresses from 192.168.3.201-254?

You can't support multiple class-C address blocks on a single network interface.  If you need more than the 253 available addresses in a single class-C (/24), you should use a different network mask.  You could use 192.168.2.0/23 which gives you addresses from 192.168.2.1 through 192.168.3.254.  You can play around with masks using this convenient tool: [http://jodies.de/ipcalc](http://jodies.de/ipcalc)

---

