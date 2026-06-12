---
title: "pptp and ubuntu server 11.04 (textbased)"
date: 2011-09-11
forum: Server Platforms
---

### Post by robban35 on 2011-09-11
Hi!

I have a ubuntu server 11.04 running 24/7 and i just bought a vpn tunnel PPTP

i want the server to connect to the tunnel on boot , i have tried many ways like configure in webmin, configure in if.up.d etc but with no luck.

i can manually start the tunnel with following commands

sudo pon "tunnelname"
and a few seconds later

sudo route add default dev ppp0

this works perfect but how do i connect on boot?

robert

---

