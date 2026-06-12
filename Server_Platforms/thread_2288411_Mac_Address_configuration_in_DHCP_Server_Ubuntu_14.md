---
title: "Mac Address configuration in DHCP Server Ubuntu 14.04 LTS"
date: 2015-07-27
forum: Server Platforms
---

### Post by Shailesh_Jain on 2015-07-27
Hi All,


I have configured the DHCP 3 server on Ubuntu 14.04 LTS and releasing the IP Address on all device.


Now I want to register the mac address to only 150 device not for all and I don't want to put the manually mac address on dhcpd.conf file for the same. 


So please can someone help me how can I do this.


Thanks & Appreciation in Advance.

---

### Post by TheFu on 2015-07-27
arp

---

### Post by Shailesh_Jain on 2015-07-27
arp ? I can't understand,
[COLOR=#000000]
I don't want to put the manually mac address on dhcpd.conf file for the same. It is possible to create one file for the MAC Address and then use this file in dhcpd.conf file. 
[/COLOR]
[COLOR=#000000]Thanks & Appreciation in Advance.[/COLOR]

---

### Post by slickymaster on 2015-07-27
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by TheFu on 2015-07-27
You don't say which dhcp server is being run (dhcp3 or isc) ... different servers have different capabilities.

The initial question asked how to put 150 MAC addresses without manually typing them - at least that is what I think it meant. By using arp, you'd get a list of all MACs on the subnet. Then you could copy/paste them into a config file.

There is an "include" directive for ISC's server and it doesn't appear to have limits as to what can be included.
[https://lists.isc.org/pipermail/dhcp-users/2006-November/002365.html](https://lists.isc.org/pipermail/dhcp-users/2006-November/002365.html) There have been bugs with this in certain releases from what I've read. Don't know if that is still an issue or not.  What have you tried?

---

