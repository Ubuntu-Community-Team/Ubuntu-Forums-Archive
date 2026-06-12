---
title: "precise/quantum-gateway problems with maas and juju"
date: 2014-08-06
forum: Ubuntu Cloud and Juju
---

### Post by Andrew_Brimer on 2014-08-06
Hello,

I have built out openstack on an IBM bladeserver with HS21 blades. It is precise/havana and all goes well in regards to juju not complaining. When I examine the networking in Horizon there are no networks/subnets/routers preset. I create my external network as well as the private net with a router in between. The gateway port set for the router shows DOWN. I have my gre tunnels set. I am pretty sure that my primary problem is that everything is going over eth0. My quantum node has eth0 without ip assigned and a br0 with the ip assigned to it. This is the same subnet as my gre tunnel endpoints and so if I make br0 a port for ext_net in ovs-vsctl I loose my tunnel endpoint for the quantum node.

I know that my main problem is that I have a very good understanding of the cli commands for maas, juju, nova, quantum, etc but I don"t think that I fully understand how to provide for eth1 in maas and juju so that my gre runs over a separate interface and subnet. I'm pretty sure that I have my network config messed up such that quantum is unable to do it's job.

I have my full configuration for the compute node, cloud controller node, and the quantum node. It is in gist on my github account and I can provide a link for anyone willing to look through. Also, if someone could explain to me the steps required to successfully define eth1 early in the maas, juju deployment lifecycle so that the quantum-gateway charm has what is needed to configure my networking during deployment rather that me trying to hack through after the fact.

Any help would be greatly appreciated.

Regards,

Andrew Brimer

---

### Post by chris240 on 2014-09-03
Hi,

I am having the same issue with Horizon

---

