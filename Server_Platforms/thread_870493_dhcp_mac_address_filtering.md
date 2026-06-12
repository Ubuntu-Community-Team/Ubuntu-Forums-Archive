---
title: "dhcp mac address filtering"
date: 2008-07-25
forum: Server Platforms
---

### Post by angelochen168 on 2008-07-25
Hi,

I'm looking for a dhcp server for ubuntu, I'd like to have following features:

1. A list of mac addresses being kept in the server, an ip will be assigned if the connecting machine has mac address listed.

2. In addition to A, a possibility to specify a static ip for a particular mac address.

3. if machine is not listed in the mac address, connection will be refused to the ubuntu server even user manually setup a ip within the valid range.(ubuntu server should refuse the connection if the ip is not issued by its dhcp server)

Possible?

Thanks,

---

### Post by koenn on 2008-07-26
1. and 2. are a piece of cake, any dhcp server can do that (look for dnsmasq or dhcp3-server

3. is difficult : on the network level, an IP address is an IP address, it doesn"t show whether it's been assigned through dhcp or set manually. 

You could probably do something along the lines of
- check IP addresses against the lease file of your dhcp server, and block those that aren't in it (by means of a packet filter (iptables), tcpwrapper (hosts.allow, hosts.deny) or something similar)
- let your dhcp server assign hostnames, and use those to filter (still, someone could also manually change the hostname of his system)
- find out how e.g. wireless access points apply MAC address filtering and see if you can do something similar ?

alternatively, see if you can set up some sort of host-based authentication (certs, key  pairs, ...), although I doubt you can let dhcp handle that.

---

