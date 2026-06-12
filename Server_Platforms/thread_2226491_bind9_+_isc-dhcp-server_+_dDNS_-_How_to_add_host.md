---
title: "bind9 + isc-dhcp-server + dDNS - How to add host?"
date: 2014-05-27
forum: Server Platforms
---

### Post by m-dw on 2014-05-27
I have successfully got bind running, both as a caching server and as Primary Master for my local (internal) zone which I've called something like "home.local".  Same server is running isc-dhcp-server and I have got dhcp updating the local DNS zone by following the instructions at [https://wiki.debian.org/DDNS](https://wiki.debian.org/DDNS).

I now want to add a new server in a subdomain (server.vpn.home.local).  It's actually the same server accessed by a different IP address over a VPN connection.  The idea is that I can keep the same config on my laptop so I can access the same services over the VPN with no config changes on the laptop.  The VPN connection adds a search suffix of vpn.home.local and points to the tunnel interface of the VPN/DHCP/DNS server as an additional DNS derver.

Adding a host called server.vpn to the db.home.local file doesn't work.  Do I need to set up another zone file (db.vpn.home.local) to allow forward lookups, or is there a way to force the new name into the files in /var/cache/bind?

---

