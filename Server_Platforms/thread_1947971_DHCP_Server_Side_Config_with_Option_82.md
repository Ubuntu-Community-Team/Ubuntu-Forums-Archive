---
title: "DHCP Server Side Config with Option 82"
date: 2012-03-27
forum: Server Platforms
---

### Post by unagaraj on 2012-03-27
Could someone provide some tips on what the dhcpd.conf file should look like if I want to use DHCP option 82 to provide clients with IP addresses? 

Specifically, the clients need to get addresses in a particular range, but the relay agent can have an address that is not in this range. Can this be accomplished using Option 82 parameters?

Here's an example:
Comp1 is connected to a router on a VLAN that does not have an IP interface. The router has another VLAN that has an IP interface and connectivity to a DHCP server. Can the IP address of the VLAN that has connectivity to the DHCP server be used in the giaddr field of the DHCP packet? The option 82 fields will have Comp1's data encoded (mac address, port etc), so the DHCP replies can be properly forwarded out to the client.

Here's the crux though, the IP address that the DHCP server should give out should not be dependent on the GIADDR field. However, the server's reply should be sent to the relay agent address (that's in the giaddr).

Please let me know if I am not explaining myself clearly enough!

And thanks in advance for any replies!

Regards,
-Uday

---

### Post by unagaraj on 2012-03-27
Come on, all you server gurus, someone must be having an opinion on this!

Regards,
-Uday

---

