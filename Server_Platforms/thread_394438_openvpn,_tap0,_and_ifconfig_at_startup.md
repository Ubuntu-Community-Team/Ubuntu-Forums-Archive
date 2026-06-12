---
title: "openvpn, tap0, and ifconfig at startup"
date: 2007-03-26
forum: Server Platforms
---

### Post by bunnynuts on 2007-03-26
To accommodate windows vista I have changed my routed vpn to a bridged and have found success in such. However, I now need to assign a specific ipaddress to tap0 for to access the samba share using:

ifconfig tap0 10.x.x.x netmask 255.255.255.xxx up

I'm certain that making my desired IP the default is not too difficult...but I'm not sure how to go about it.

Any help is appreciated.

Thanks

---

