---
title: "dhcpd does not have a leases file"
date: 2015-05-21
forum: Server Platforms
---

### Post by barroncm on 2015-05-21
Ubuntu 14.04 server running isc-dhcp server. I am not getting a leases file. The package doent even create it. I have tried creating it as well with no luck having leases written to it.
Any ideas or help would be great!

---

### Post by Doug S on 2015-05-22
Well, you will have to tell us some more about your setup.

For example: My system only writes lease information to the file for allocations from the dynamic pool (which I have for guests). Leases from the MAC based stuff (which is most of my LAN most of the time) are not written to the leases file.

---

