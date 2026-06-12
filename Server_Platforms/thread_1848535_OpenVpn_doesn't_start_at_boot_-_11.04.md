---
title: "OpenVpn doesn't start at boot - 11.04"
date: 2011-09-22
forum: Server Platforms
---

### Post by Merlus on 2011-09-22
VPN is configured and connects fine, but I need to start it manually each time.
There is .conf file in /etc/openvpn and /etc/default/openvpn is set to load all vpns.

I think it has something to do with openvpn coming up before the network, but I am not sure.

Can someone please offer more advanced advice of things I can check?

---

### Post by Merlus on 2011-09-23
adding bridge_maxwait 0 to /etc/network/interfaces has fixed the problem.

---

