---
title: "Ubuntu 20.04 server using wrong IPv6 EUI-64 address"
date: 2022-03-15
forum: Server Platforms
---

### Post by scsiraidguru on 2022-03-15
Ubuntu 20.04 fully patched
I have one server that is getting a strange EUI-64 IPv6 address.  This server is secondary dns server.  

ens32: 2601:402:8201:1d50::/64   This have proper EUI-64 that match the mac.  This points to the correct interface on the firewall.  
ens34: 2601:402:8201:1d52::/64   This have proper EUI-64 that match the mac   This points to the correct interface on the firewall

ens34 is also getting 2601:402:8201:1d51::/64.   This address is wrong IPv6 address, 1d51 is not on ens34.   It is using ens34 mac address and has a IP -6 route too.  

I checked the netplan setup it only has entries for ens32 and ens34.

Firewall does have a 2601:402:8201:1d51: interface but this server is not on it.  Nothing is currently using it.  

I checked my IPv6 DHCP and DNS servers for errors.   Both are fine.  I was waiting till Ubuntu 22.04 came out next month to install a new server and move everything but this is throwing a lot of errors on the firewall and is affecting routing of server packets.  I might create a new server and move the contents of this server to it.   

What could be bringing another IPv6 subnet into ens34?

---

### Post by slickymaster on 2022-03-15
Thread moved to **Server Platforms** for a better fit

---

### Post by The Cog on 2022-03-15
I would be inclined to use tcpdump -r wireshark and see if the firewall (or anything else) is putting out router advertisments on that network, advertising the 1d51 prefix.

---

