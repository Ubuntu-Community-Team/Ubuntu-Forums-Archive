---
title: "what kind of traffic control or firewall large ISPs use?"
date: 2007-11-28
forum: Server Platforms
---

### Post by netlogic on 2007-11-28
I don't know if anyone here has any experiences with setting up a large network of firewalls, but I am curious how companies like Verizon, ATT and Comcast manage their security and traffic control. This applies to even the large disaster recovery companies like Sunguard or other firms that might need to protect their Sonet rings. Is the cluster of rack mount firewalls only solution to do this? Do you assume they use BSD or Linux firewalls? I am guessing controlling 300gigs of traffic data would least require 64gigs of ram and quad core processors. Anybody here has an experience of setting up a network of firewalls? Your opinions are greatly appreciated.

---

### Post by Dark Hornet on 2007-11-28
Hello...I work on the backbone for one of said LARGE companies...with that said...it depends...lol.  In other words, most internet traffic is managed at the router level.  The network transit traffic usually is not blocked, with certain obvious exceptions--private IP blocks, redistributed i-bgp routes, etc.  In addition, customers of any ISP can only advertise out what the ISP allows them to advertise....this is achieved usually at the Gateway level using route-filters (Juniper), or prefix-lists (cisco).  So I guess to answer your question, ISPs do not have (for normal traffic) racks of firewalls.  The routers usually handle a lot of this functionality.  

Now please keep in mind that traffic can and is "shaped" in many different ways, using many different protocols such as MPLS, VPN tunnels, etc.

I hope I have answered your question...please feel free to ask anything else that comes to mind.  :)

---

