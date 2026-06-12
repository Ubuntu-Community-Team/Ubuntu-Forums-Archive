---
title: "DHCP Server Assigns Highest Address First"
date: 2007-06-25
forum: Server Platforms
---

### Post by chris.zeman on 2007-06-25
I have 3 servers all doing the same thing and I can't figure out why. My address pool starts at .100 and ends at .254. The servers all start assigning addresses at .254. It's not critical to me that they start assigning at .100; I just thought it was rather odd.

Chris

---

### Post by MJN on 2007-06-26
According to the dhcpd.conf man page there is no predefined order:
 
*The DHCP server generates the list of available IP addresses from a hash table. This means that the addresses are not sorted in any particular order, and so it is not possible to predict the order in which the DHCP server will allocate IP addresses. Users of previous versions of the ISC DHCP server may have become accustomed to the DHCP server allocating IP addresses in ascending order, but this is no longer possible, and there is no way to configure this behavior with version 3 of the ISC DHCP server.*
 
Mathew

---

### Post by chris.zeman on 2007-06-26
Wow. Thanks for the info. I just looked at the list of the leases and, sure enough, the addresses were all over the place. I find it surprising that the order in which it assigns the addresses isn't configurable in some way.

Chris

---

