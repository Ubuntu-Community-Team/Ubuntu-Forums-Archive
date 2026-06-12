---
title: "OpenVPN with DHCP and firewalls."
date: 2011-12-22
forum: Server Platforms
---

### Post by artheus on 2011-12-22
Hi.

I've been following the Ubuntu Community OpenVPN guide to set up a simple OpenVPN setup.

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

I've checked that I can connect, and it works.
I am not using the bridge adapter etc, I am just connecting to the eth0 as the server is connected directly to the WAN with a static IP.

Where I want to go from here is to setup the server so I can, with a firewall, externally block all ports but the OpenVPN port 1194.
When I'm connected to the VPN I want to be able to connect to the services ssh and samba ( which is blocked from the outside world ).

I really don't know what to look for here, I've been searching the internet for an answer but I don't know the correct buzzwords, obviously.

At the server-end I only have the server with a network card, which is connected directly into the WAN port in my wall. Set-up with a static IP.

I am using Ubuntu 11.10 Server Edition on the server.

If there is anything other than this I can easily do for increased security, please inform me about that too.

Cheers!

/Artheus

---

