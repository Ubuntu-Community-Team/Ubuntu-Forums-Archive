---
title: "Samba, bind9, dhcpd, etc. playing nice"
date: 2006-10-08
forum: Server Platforms
---

### Post by jelevin on 2006-10-08
Mostly for fun I'm moving a new ubuntu server into a functioning home wireless windows network (mixed xp pro, xp home, w2k).  All of this is behind a NAT router that provides a gateway to my cable-modem internet service.

My goals were:
[LIST]
[*]Use samba to set up shared file space, some for the entire family as well as personal areas.
[*]Use bind9 to provide DNS service, especially to provide local cacheing of the IP addresses.
[*]Use dhcp3 to provide IP addresses to provide IP addresses to family computers as well as wifi-enabled guests.
[/LIST]

After a lot of playing around I think I have all of this working, but I have a sense that I've made it more difficult than it needs to be.  Is there a good overview of how all of this stuff works together?  What are the issues as to whether samba should be a windows domain controller? What is WINS versus DNS service?  What needs to be in the hosts file and resolv.conf?  How can I tell if the DNS cacheing is working?  Where do I use the name servers provided by my ISP and where do I use my own server as the name server?  Should I be using dnsmasq instead of bind9+dhcp3?

Any pointers would be appreciated.

---

