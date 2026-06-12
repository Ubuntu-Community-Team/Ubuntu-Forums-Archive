---
title: "Internal Static IP's and DHCP"
date: 2008-01-29
forum: Server Platforms
---

### Post by jaytek13 on 2008-01-29
I have a few questions about assigning internal static IP's when the router acquires the IP information through DHCP.

First, I have 2 computers connected to the router. Would it be advised that I set each of these to have an internal static IP?

Second, does setting an internal static IP below the router's range mean the WAN IP will not change?

The context of this is that I just set up LAMP and want to be able to play around with hosting a website. I had to redirect http requests to an alternate port because the ISP blocks port 80, but I would like to be able to put an A record in to refer to a static IP... I guess what I'm asking is if setting the internal IP's below the routers range will allow me to have a static IP without having to pay for it?

---

### Post by DDuong on 2008-01-29
In my internal network, all my PCs have static IPs.  The only time that DHCP assigns an IP address is when I connect my laptop to it or if someone comes over for a lan party or something.  To answer your question, sure, you can go ahead and assign static IP addresses to your PCs.  It shouldn't hurt.

Your WAN IP will never change since that's assigned to you by your ISP.  Your internal IP address is seperate from your WAN's IP address anyways.

---

### Post by Iowan on 2008-01-29
I'm certainly no expert - caveat emptor.
Servers should probably have either a static lease or a static address.   A static address should be in the router's subnet, but outside it's DHCP range. You can (probably/maybe?) set up port forwarding in the router to access your server.  DynDNS is one way of reaching what would otherwise be a moving DHCP target address - unless your ISP has assigned you a static IP already. Your internal addresses shouldn't be directly accessible from outside your network.

---

