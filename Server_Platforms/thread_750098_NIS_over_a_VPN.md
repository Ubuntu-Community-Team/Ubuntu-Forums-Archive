---
title: "NIS over a VPN"
date: 2008-04-09
forum: Server Platforms
---

### Post by chrislynch8 on 2008-04-09
Hi,

We have a central server that runs a NIS server and we have another server that is connected over the VPN. On the Client server when I try to run the NIS client 

sudo /etc/init.d/nis start

I get this error.

"Starting NIS Servives: ypserv ypbind [Binding to ypserver.....Backgrounded] ypinit can't enumerate maps from 192.168.1.250. Please check that it is running.

It is running on the Central Server and we suspect that he issue is getting NIS Client to bind over the VPN possibly.

Has anyone got any idea on this issue or come across this before,

Rgds



**_[COLOR="Red"]Update[/COLOR]_**

I now have this resolved - the issues was due to the IP assigned in the VPN I was only allowing access VIA its LAN address and not it VPN IP address

---

