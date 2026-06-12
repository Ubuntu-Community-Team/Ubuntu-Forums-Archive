---
title: "Web Content Filtering Solutions"
date: 2008-08-08
forum: Server Platforms
---

### Post by gyzer on 2008-08-08
I have no idea if this thread should be in this section, but this is the best place I can think to put this.
 
I'm planing on building a IPcop router/firewall and I'm really excited about it and everything. The one thing thought I'd like to have, not based on the machines, is some sort of web content filtering. I know there's Dansguardian but that seems to be causing people problems so I was wondering if there were some other ideas or solutions people know about.
 
I do know that there are DNS services out there that if you have your clients point to, it can be setup to do content filtering and stuff, but the problem with that is, I only want to do content filtering for one computer, no all the others, and from what I've read, those DNS services only work blanketly over an entire public ip address.
 
The setup for my network is going to include a ubuntu based file server, so even if there is some sort of solution I could do via that would work, but again, this has to be able to target just one computer on the network, not the entire network.
 
Any help or sugestions would be welcomed!

---

### Post by windependence on 2008-08-08
Take a look at untangle. [www.untangle.com](www.untangle.com)

-Tim

---

### Post by gyzer on 2008-08-09
Does Ipcop and untangle work well together, or is that just over complicating things?

Untangle looks really really nice. My only concern, is that with IPcop you have 4 interfaces you can deal with in the firewall that have some predefined perameters. Red, Gree, Blue, and Orange. Red is the interface going out to the net, green is your home network, blue is a wireless network that cannot access the green network unless you create specific pinholes or you vpn into green, and orange is a DMZ.

I really like the idea of the seperate wireless network that IPcop offers. Can you do something similar to that with Untagle? Like maybe just use the DMZ as the wireless network?

Thanks for the sugestion.

---

