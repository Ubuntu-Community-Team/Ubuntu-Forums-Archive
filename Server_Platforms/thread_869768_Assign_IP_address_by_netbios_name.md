---
title: "Assign IP address by netbios name?"
date: 2008-07-25
forum: Server Platforms
---

### Post by drakoes on 2008-07-25
I am working on a new server to take the place of a machine running wingate.  It will do proxy, authentication for resource access as well as handle dhcp and dns.

Is it possible with DHCP3 to assign an address to a computer by it's netbios name?

I know I can assign an ip address by the MAC address but there are a lot of computers on the network (about 50 with statics) and if I could avoid having to collect all of the mac addresses on the network that would be great.  The wingate currently does it by netbios name.

Is it possible?

---

### Post by koenn on 2008-07-25
dnsmasq can do that too (judging from its config file), provided the clients actually send their name with the dhcp request, of course.
I'm not sure about dhcpd3

alternatively, you will find all hosts' mac addresses in the lease file of your current dhcp server, so you don't actually have to look for them "all over the network"

---

