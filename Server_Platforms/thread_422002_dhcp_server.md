---
title: "dhcp server"
date: 2007-04-24
forum: Server Platforms
---

### Post by tocleora on 2007-04-24
We installed dhcp3 and have it where eth0 is plugged into a cisco switch and the computers connected to the switch can get dhcp.  We've connected Internet to eth1, however we are unable to get internet access on the dhcp server computer or the clients.  We tried to set up eth1 to be the dhcp server since I figure eth0 would be the primary card and what the browser would look for internet on(?) but setting the dhcp server to "listen" to eth1 didn't seem to do what we wanted it to, it only seems to work if the switch is plugged into eth0.  I saw a how-to on how to set up dhcp server but nothing related to getting internet working with it.  Our intention is to also set up firewall and make this what I believe would be called a gateway?  Any help would be greatly appreciated!

---

### Post by Big Ed on 2007-04-24
> **tocleora said:**
> We installed dhcp3 and have it where eth0 is plugged into a cisco switch and the computers connected to the switch can get dhcp.  We've connected Internet to eth1, however we are unable to get internet access on the dhcp server computer or the clients.  We tried to set up eth1 to be the dhcp server since I figure eth0 would be the primary card and what the browser would look for internet on(?) but setting the dhcp server to "listen" to eth1 didn't seem to do what we wanted it to, it only seems to work if the switch is plugged into eth0.  I saw a how-to on how to set up dhcp server but nothing related to getting internet working with it.  Our intention is to also set up firewall and make this what I believe would be called a gateway?  Any help would be greatly appreciated!

It's very rarely a good idea to use a server as a firewall/gateway.  The firewall has to be locked down pretty tight and a server has to have ports open.  You would be better off with the server by itself and running something like Coyote for your firewall on a separate box:

[http://www.coyotelinux.com/products.php?Product=coyote](http://www.coyotelinux.com/products.php?Product=coyote)

It's free for personal use.

Or Smoothwall:  [http://www.smoothwall.org/](http://www.smoothwall.org/)

Or Firestarter:  [http://www.fs-security.com/](http://www.fs-security.com/)

Google "linux firewall" and you'll get a ton of hits.

That being said, if you do want to use one box for both purposes, you'll have to configure the routing to tell it which packets go where.  You'll likely need to use the "route" command:

[http://linux.about.com/od/commands/l/blcmdl8_route.htm](http://linux.about.com/od/commands/l/blcmdl8_route.htm)

Really, a separate firewall distribution is a _lot_ easier to configure.

Ed

---

