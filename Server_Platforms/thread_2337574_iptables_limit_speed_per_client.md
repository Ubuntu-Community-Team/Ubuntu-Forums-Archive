---
title: "iptables limit speed per client"
date: 2016-09-19
forum: Server Platforms
---

### Post by sysrolix on 2016-09-19
Hi!

In my dhcp server has a static IP and MAC pairs.
I want to set my iptables to this pairs, mean: what is the syntax?
Drop, if ip and mac not match..
I want to set up and download speed for every ip address.
For example: 192.168.1.11 has 100Mbps down / 100mbps up and 192.168.1.13 has 10Mbps down and 5 Mbps up.
I want to generate this config script from sql database, which contain the IP MAC pairs. Another script will generate the IP-s for a new MAC address of client...
After that, I have two interface, WAN and LAN eth0 is WAN and eth1 is LAN.
I want to set my server to router mode, so I need forward.
I want to use bind, ftp, ssh, http so I need to allow these ports on iptables. Default construction, drop everything except, these ports from WAN and accept MAC IP pairs, drop every other...
port forward syntax in iptables
disable upnp?!
Finally, possible block torrent and vpn?
I found l7 layer, but how to can I install to kernel?!

So
dhcp: mac -> ip static
iptables: wan -> port
allow MAC ip pairs
drop others
custom bandwidth
routing, forward

Thanks very very!
Sorry for my bad English

---

