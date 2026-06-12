---
title: "Access internet from VM in UEC via a different n/w interface?"
date: 2012-02-21
forum: Ubuntu Cloud and Juju
---

### Post by davidbilla on 2012-02-21
Hi,

We set up a UEC cloud with 2 servers as shown in [https://help.ubuntu.com/community/UEC/CDInstall]("https://help.ubuntu.com/community/UEC/CDInstall") with server1 hosting the cloud controller(CLC), cluster controller(CC) and storage controller(SC) and server2 just hosting the node controller(NC).

server1 - 2 n/w interfaces - eth0(private router) and eth1(public/local/workplace n/w).
server2 - 1 n/w interface - eth0(private router).
Only the two servers are on the private router.

The VMs on the cloud share resources through the eth0 interfaces of server1 and server2. 

Is it possible to access the internet from the VMs through the other n/w card(eth1) of server1 that is connected to the outside world? 

For this, the public IPs of the VMs need to be in the range of (137.x.x.x) which is what the local/workplace network allocates to any machine. But the public addresses that we allocated are in the range (192.168.x.x) and can be seen in VNET_PUBLICIPS parameter in /etc/eucalyptus/eucalyptus.local.conf file. 

Will it be possible to access the workplace network just by changing this parameter to the required (137.x.x.x) addresses?

Thanks.

---

