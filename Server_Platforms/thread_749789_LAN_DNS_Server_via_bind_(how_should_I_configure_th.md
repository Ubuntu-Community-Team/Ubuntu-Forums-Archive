---
title: "LAN DNS Server via bind (how should I configure this?)"
date: 2008-04-08
forum: Server Platforms
---

### Post by liquid circuit on 2008-04-08
I have just set up a headless dedicated file/torrentflux server for the first time, and I am looking for some advice.

My home network is verrry basic; internet hits my little D-Link router (DI-524, 192.168.0.1), and all nodes connect to the router.  Currently I've got one server (Ubuntu, 192.168.0.103), one desktop (Ubuntu/WinXP, 192.168.0.101), and one laptop (Mac OS X, connecting via WiFi, 192.168.0.102).  Super simple.

I'd like the server to act as a DNS server, so that instead of accessing torrentflux (from within the intranet) by going to "http://192.168.0.103/torrentflux/," we could enter something like "http://www.lan.com/torrents/" or "http://torrents.lan.com/."

I have installed bind9, and was starting to configure it according to some tutorials on the web, but as soon as I started editing /etc/bind/zones/lan.com.db I got confused and started to rethink how this was all going to work.

Could someone give me some guidance please? Am I thinking about this all wrong?  Is the fact that the DNS server and the torrentflux server are on the same IP address going to cause a problem for this type of setup?  I am also thinking of playing with basic web development, so [www.lan.com](www.lan.com) (intranet only) would be a portal to the services on the lan with links to torrentflux/ftp/whatever

I can't really wrap my head around this as it is all very new to me.  Any help would be greatly appreciated.

---

