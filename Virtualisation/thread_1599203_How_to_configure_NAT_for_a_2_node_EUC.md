---
title: "How to configure NAT for a 2 node EUC?"
date: 2010-10-17
forum: Virtualisation
---

### Post by nutznboltz on 2010-10-17
When installing EUC on two computers via the server ISO so that the first computer has the CC/CLC/Walrus/SC and the second computer has the NC on it and you are using the CC/CLC/Walrus/SC as a network gateway for the NC how should the NAT be set up?

That configuration is shown as figure 2 on the wiki page
[http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0](http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0)

See the caption to figure 2 which reads ``Figure 2 shows node machines on a private subnet using the front-end machine as a gateway to the public network. Note that the front-end machine has two Ethernet devices (eth0 is on the public network; eth1 is on the private network) and uses NAT to allow the nodes access to the public network.''

Near the top of that wiki page is a note that reads ``Note that the administrator must ensure that the virtual subnet IP address space does not contain, is not contained by, and does not conflict with any part of the physical network IP address space.''

But it is unclear if the NC eth0 is using the ``virtual subnet IP address space'' network or an additional network.

By default the server ISO has a NAT for 172.19/16 like this

$ grep 172.19 eucalyptus.local.conf
VNET_SUBNET="172.19.0.0"

and

$ sudo iptables -n -L -t nat
Chain PREROUTING (policy ACCEPT)
target prot opt source destination
DNAT tcp -- 172.19.0.0/16 169.254.169.254 tcp dpt:80 to:169.254.169.254:8773

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

Chain POSTROUTING (policy ACCEPT)
target prot opt source destination
MASQUERADE all -- 172.19.0.0/16 !172.19.0.0/16

Should the NC eth0 be on 172.19.0.0/16 or should an additional NAT be configured into netfilter via iptables?

---

### Post by nutznboltz on 2010-10-18
The Eucalyptus 2.0 documentation needs to do better job of explaining the CC <--> NC network.

When I look for anything about the CC <--> NC network in
[http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0](http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0)
I see in the section for STATIC configuration in that documentation a remark which insinuates that VNET_SUBNET is the one to put the NC eth0 on. They do not state anywhere in that document explicitly what the CC <-> NC network is, but this statement looks like a clue to what their intent is:

``It is also necessary to instruct Eucalyptus about the subnet being used by the CC and NC. To do this, you must configure VNET_SUBNET, etc., as described earlier in Section 3.3: About VNET_ options. ''

That seems a lot more sane than the insinuation that VNET_SUBNET is unused you get from reading the MANAGED configuration section which states only this about VNET_SUBNET:

`` It is also necessary to instruct Eucalyptus about the unused subnet. To do this, you must configure VNET_SUBNET, VNET_ADDRESSPERNET, etc., as described in the above section: About VNET_ options. ''

The only other thing mentioned about what VNET_SUBNET is an ambiguous statement:

``VNET_SUBNET, VNET_BROADCAST, VNET_NETMASK 
These three options—network address, the broadcast address on the network, and the subnet mask, respectively—work together to define the configuration of a specific network. It is necessary to specify all three options when Eucalyptus requires a virtual subnet. ''

---

