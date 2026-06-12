---
title: "Serving up dhcp for an adjacent subnet?"
date: 2008-02-28
forum: Server Platforms
---

### Post by jcostom on 2008-02-28
Greetings all...

My server is running Gutsy, and serves up DHCP for the local LAN, let's say it's 1.1.1.0/24.  I need to create an additional subnet, reachable via a router that has an interface in 1.1.1.0/24.  I'd like to have the dhcpd on the server hand out addresses for the new subnet as well.  Is this as simple as setting the router's interface in the new subnet (say, 2.2.2.0/24) as a dhcp relay, pointing to the server, 1.1.1.20?  Assume all the proper routes are in place. :)

So, to recap:

Current LAN is 1.1.1.0/24
Server is 1.1.1.20
Server runs dhcpd, with a pool of 1.1.1.50 - 1.1.1.100

Adding a router:
e0: 1.1.1.254
e1: 2.2.2.1

On the e1 interface, there's a configuration for a dhcp relay, which I'll point to 1.1.1.20.

I plan to create a subnet declaration and pool for 2.2.2.0/24 in the dhcpd.conf.  Is that all I must do to make this work?  Thanks much for the tips.

---

### Post by faulkes on 2008-02-28
You've pretty much nailed it.

I read through it and the only thing I was looking for was the dhcp relay statement (which
makes me think it's a cisco).  Should be good to go.

Faulkes

---

### Post by jcostom on 2008-02-28
Ok, thanks much!  Seemed pretty straight forward, but you know how that goes sometimes...

---

