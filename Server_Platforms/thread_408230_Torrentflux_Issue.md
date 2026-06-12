---
title: "Torrentflux Issue"
date: 2007-04-13
forum: Server Platforms
---

### Post by Carrot06 on 2007-04-13
I have just built the server mentioned in my signature and am now having problems with torrentflux. When I initially installed torrentflux it worked perfectly, but now all torrents (even ones with 10000+ seeds) don't download. I have searched on these forums and on google, and tried different ways of opening ports and have not found anything that works.

I am able to surf the net from the desktop and even download torrents through uTorrent & Bittornado from my Desktop PC, but I cannot download torrents using torrentflux (bittornado) on the server. Also, every port checker I've used says my ports 6881-6884 are not open.

Any ideas as to why I can't download torrents on the server but can on the desktop?


My setup is as follows:
[COLOR="Red"]DLink DSL-300 modem
||
|| ethernet
||
DLink DI-624+ router (DHCP enabled with Static IP addresses, and ports 6881-6884 open via the virtual server)
||
|| wireless ** laptops also connected by wireless **
||
Server (no firewall, port forwarding turned on, LAMP with samba, ssh, webmin and torrentflux, Network Hardware: wireless pci card & usb ethernet card)
||
|| ethernet
||
Netgear Switch
||
|| ethernet
||
Desktop PC, XBOX, PS2[/COLOR]

---

### Post by drdnl on 2007-04-24
Hi there, possibility we suffered from the same issue:

when you add a download does it stay "queued"  indefinitely?

If so, login as admin, go to queue, set queue manager to false, save settings, then set it to true, save again. This should restart your queue manager. Now stuff starts downloading again...

This solved the no downloading problem for me, however I dont know whether you suffer from the same issue. Good luck with it :)

---

