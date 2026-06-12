---
title: "SSH connection from Outside (Dual-Stack lite)"
date: 2019-11-10
forum: Ubuntu/Debian BASED
---

### Post by hassoya on 2019-11-10
[COLOR=#242729][FONT=Arial]I would like to set a SSH connection to my Raspberry Pi via PuTTY while i am not in my local network.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**A**: A PC (outside my Network)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**B**: A virtual Server ubuntu 18.04 and a static IPv4 adress (outside my network)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**C**: Raspberry Pi 4, Raspbian Buster (home network)
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The Port for SSH on RPI is Port 1249. The Firewall-Settings in my router has been set.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Since my router has only external IPv6 IP-Adress (Dual-Stack), I have rent a vserver which is outside my network. 
The vserver is changing the IPv4 requests into IPv6 via 6tunnel (4to6). That makes it possible to reach my cloud server 
trough my router and I dont need to use a DynDNS service.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now to my question. How can I make a SSH Tunnel between:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]A->B (I think this would be a IPv4 connection via PuTTY)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]B->C (?..I can only adress the IPv6 IP of my Raspberry)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I have read the topics about SSH forwarding. But I dont know how to solve it with the Dual-Stack problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]If you need more Info pls let know.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**Thx for your help.**[/FONT][/COLOR]

---

### Post by TheFu on 2019-11-11
Why not just use IPv6 from the client to the server directly?
I don't know if PuTTY supports IPv6, but any Linux ssh client should.  Windows and Linux has supported IPv6 for at least a decade.

I can't test IPv6 stuff. We disable it in all our network gear and OS settings because we don't have the skill to secure it.

---

