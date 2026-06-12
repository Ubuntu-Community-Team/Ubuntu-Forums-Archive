---
title: "Ubuntu Network Setup"
date: 2006-02-28
forum: Server Platforms
---

### Post by campnic on 2006-02-28
I have setup a few novel linux boxes without getting into any sophisticated network setups, but I want to try and setup a DHCP server that is better than the one that is included with my dsl package (as it does not allow mac address based static ip assigning).  That being said, my ubuntu box will have 2 nic cards, one I plan to connect directly to the dsl modem (eth0) and one I plan to have connected to my LAN (eth1).  eth0 will have a static ip (192.168.0.2) and will use the dsl modem as default gateway(192.168.0.1).  Now, here is where i get confused as I'm not particularly well versed in networking.  I haven't been able to find out what DNS servers i should use as my windows machines seem to be using the dsl modem as the primary and are getting assigned a dynamic one for the secondary.  On top of that, Im not sure how to expose my lan on eth1 to  the internet through eth0.

Maybe someone has a guide.  I searched for guides and posts but couldn't find any that seemed specific to what I want to do.  My newbiness also limits how much tinkering I feel safe doing, since I always break things.

EDIT:  Not sure if this is a how to or more of a configuration thing.

---

### Post by colo on 2006-02-28
udhcpd is a fine standards-compliant DHCP-daemon which should fulfill your need, from what I remember. Configuration is pretty much straightforward and self-explanatory.
-> [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=udhcpd&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=udhcpd&searchon=names&subword=1&version=all&release=all)

I don't know if there's a specific "Ubuntu as a NAT-router"-guide on the web (well, there most probably is, but I'm too lazy to figure out thwere, exactly), but the "Gentoo Home Router Guide" is excellently written and implementable on Ubuntu, as well.
-> [http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

---

