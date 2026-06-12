---
title: "domain resolution in ubuntu server"
date: 2009-09-18
forum: Server Platforms
---

### Post by drakeo11 on 2009-09-18
Hi,

I'm having trouble associating my GoDaddy domain with my remote Ubuntu server.  I'm trying to use openDNS's name servers.

I've made the following changes:[INDENT]sudo cp /etc/resolv.conf /etc/resolv.conf.auto
[/INDENT][INDENT]sudo gedit /etc/dhcp3/dhclient.conf
[/INDENT][INDENT] prepend domain-name-servers 208.67.222.222,208.67.220.220;

[/INDENT]Anyone advice would be greatly appreciated.  My server admin is away for the weekend, and I really need to fix this ASAP.

Many thanks.

---

### Post by drakeo11 on 2009-09-18
Nevermind... 

](*,)

---

