---
title: "Vm server2 ubuntu 8.04 server : Vlan setup"
date: 2008-10-31
forum: Virtualisation
---

### Post by colinlr on 2008-10-31
Has anyone had any success with setting up VLAN's on virtual machines?
Basically I have 2 apache servers mounting an nfs share for content all on different subnets. A loadbalancer then didtributes the request to 1st available server. I have just added a new ubuntu server 8.04 with vmserver 2 which homes 2 new web servers which I plan to add to the load balancer.
Basically I am pretty stumped with how to setup vlans on these new servers.
Logic tells me to setup up the VLAN's on the metal (vmserver) and then this would hopefully "bridge through to the new virtual servers"
Does anyone know if this is the case or does one need to setup vlan on the vmserver and then the virtual servers aswell?
Any help or suggestions will be most appreciated.

---

