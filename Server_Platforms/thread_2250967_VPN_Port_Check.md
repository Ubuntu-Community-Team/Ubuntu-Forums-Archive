---
title: "VPN Port Check"
date: 2014-11-01
forum: Server Platforms
---

### Post by SilvaNights on 2014-11-01
Hiya,

I have been Googling around and either can't find an answer or am not 100% that the information is correct.

I have a Ubuntu Server connecting to a VPN _**as a client**_ using OpenVPN.
I am trying to determine if a port is using the connected VPN connection.
I do not know if all ports use a connected VPN and therefore are safe from a snooping and security side between me and the VPN server?
The service provider says all ports are open for use in their documentation.

I have read some documentation about enabling the management on the OpenVPN daemon but have failed to do this.
I also read some information about adding "push redirect-gateway def1" to the OpenVPN client but this seems to have failed.

Thanks,

tom,

---

### Post by SeijiSensei on 2014-11-01
"Ports" don't use connections.  What determines whether something is carried over the VPN is the routing table on the machine.  What does "route -n" tell you?

I use a VPN to connect between my home office and my servers operating in the cloud.  All my other traffic goes out through my normal gateway.  YMMV.

---

### Post by SilvaNights on 2014-11-01
Hi,

Thanks for your reply.
Here is the output of route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         178.73.212.97   128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
128.0.0.0       178.73.212.97   128.0.0.0       UG    0      0        0 tun0
178.73.212.96   0.0.0.0         255.255.255.224 U     0      0        0 tun0
178.73.212.201  10.0.0.1        255.255.255.255 UGH   0      0        0 eth0

---

### Post by SeijiSensei on 2014-11-02
That's a pretty messy routing table.

First 173.73.212.96/27 is a [public network located in Sweden]("https://apps.db.ripe.net/search/query.html?searchtext=178.73.212.0#resultsAnchor").  I don't know why you are connecting to it over the tunnel.

Also you have two default gateways.  Some traffic goes through 10.0.0.1 over the ethernet and some goes through the Swedish ISP.  Have you spoken with your VPN provider about what the correct routings should look like?

---

### Post by SilvaNights on 2014-11-04
I assumed it was normal to have 2 gateways if you have an active VPN connection as one would be for the VPN network and one for the network you are running it from? (Please feel free to correct me)
If not how would I go about "killing" one of the gateways? (And which one?)

I have asked about what the correct routing table should look like, currently awaiting a response.

Many thanks for your continued input.

---

### Post by SeijiSensei on 2014-11-05
The "default gateway" handles traffic that doesn't match any other routes.  There should be only one on any machine.  If you can make the upstream end of the tunnel the default gateway, that would send all your traffic over the tunnel.  The trick to is make sure you also have an explicit route to the public address of the VPN server so the tunnel itself can be created.

---

