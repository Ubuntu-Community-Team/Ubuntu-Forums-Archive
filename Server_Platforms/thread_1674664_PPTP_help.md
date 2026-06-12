---
title: "PPTP help"
date: 2011-01-24
forum: Server Platforms
---

### Post by djanie78 on 2011-01-24
I got a pptp server with 2 NIC. eth0 to my LAN and eth1 to a netgear router that has a couple more ubuntu servers attached. Am coming in from the internet through the netgear router which in turn fowards all PPTP traffic to the PPTP server. The idea is to be able to PPTP into the PPTP server, obviously and be able to see the boxes on the the netgear router. I am able to achieve this.
My problem is PPTP users can see my LAN as well which is on eth0. I should be able to get the the PPTP server from the LAN as well. All this is ok. How do i stop PPTP users from seeing anything on the LAN ie eth0. 

I looked at iptables but am probable not configuring it properly

internet--->netgear---->PPTP server<----->LAN

Any help pleaseeeeeeee.

---

