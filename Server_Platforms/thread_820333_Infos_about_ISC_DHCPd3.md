---
title: "Infos about ISC DHCPd3"
date: 2008-06-06
forum: Server Platforms
---

### Post by ripkars on 2008-06-06
Hello all,
Would anybody mind answering these questions about ISC DHCPd3? I've already read many dcs about this software but i've found nothing abi+out this...

[LIST]
[*]Let's suppose we have two different subnet declaration sections like this: "subnet x.x.x.x netmask x.x.x.x { .... }". What criteria is used to serve an unknown client that connects to the server asking for an IP assignment? In particular, from which of the two subnets is the server going to pick a valid IP?
[*]Under what circumstances is a client assigned the "unknown-client" status?
[*]Let's suppose now that a client connects to the dhcp server to obtain a valid IP. Let's also suppose that the client is not present in the dhcpd.conf file in any of the "host [name] { .... }" sections. The IP addresses which the server is going to consider for valid assignment are only those that appear in a "pool { range [from IP_start] [to IP2_end]; **allow unknown clients**; }" sections?
[/LIST]
Thanks everybody!

---

