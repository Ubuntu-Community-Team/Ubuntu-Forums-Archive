---
title: "DRBL and local DHCP"
date: 2012-03-05
forum: Server Platforms
---

### Post by hsafe on 2012-03-05
Hello there

I am new to the DRBL and am trying to set up a clonezilla image server in the network. I have already pretty grasped the set up process but need to know the below:
I am setting up a 10.04 server for this purpose with two NICs and it is within a lan & different ip range than 192.168.0.0 . I was wondering if there is a way not to conflict between the clients and normal DHCP so that bootpx clients will receive their range from eth1 when they want to pull the clonezilla image over the network.How can I do that ?Please help. Thanks

---

### Post by Sergius14 on 2012-03-05
Just stay each interface in different switches (or VLAN's).

DCHP is a MAC level protocol, so if you mix both interfaces in the same switch, both DHCP servers will be in the whole network.


In the most cases, clients are going to receive an IP randomly from each DHCP servers...

---

### Post by hsafe on 2012-03-12
But I thought they are fundamentally different I mean the bootpxe and dhcpdameon. I was thinking that the drbl server as in its configuration phase listens on the configed interface and activates itself on that. While it also correctly identifies the other interface as a WAN or Internet connection and segragates it. In another sample config I noticed that the drbl was configured to run on a subinternface and again different LAN IP setting like 192.168.1.0/24. My scenario is only different that mine is a "real" interface though. One side note is that the server never comes up with both though. Even tried to run only on the eth1 drbl interface only but no luck

---

### Post by hsafe on 2012-03-14
[http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)
 
Reading :
 
**Integration**
**The *PXE Client/Server Protocol* was designed so:**
[LIST]
[*]**it can be used in the same network as an existing DHCP environment without interference **
[/LIST]

---

### Post by Sergius14 on 2012-03-14
My recommendation is that you try first to make work drbl/pxe in a different switch/network/etc.

When you have make it worked, you can make the mix.

PXE can coexist with a standard DHCP as you said.


I think that your have something wrong with drbl than the network.

---

### Post by hsafe on 2012-04-09
As said and to test if I am mistaken put the interfaces into differnet LANs seperated by differnet switches and isolated form each other. But then it failed again and the client did not get any bootpxe IPs. 
Reading the varlogs came to something interesting which am posting here perhaps someone will advise :
 
pr 9 00:06:04 ubuntu-testserver dhcpd: No subnet declaration for eth1 (0.0.0.0).
Apr 9 00:06:04 ubuntu-testserver dhcpd: ** Ignoring requests on eth1. If this is not what
Apr 9 00:06:04 ubuntu-testserver dhcpd: you want, please write a subnet declaration
Apr 9 00:06:04 ubuntu-testserver dhcpd: in your dhcpd.conf file for the network segment
Apr 9 00:06:04 ubuntu-testserver dhcpd: to which interface eth1 is attached. **
Apr 9 00:06:04 ubuntu-testserver dhcpd: 
Apr 9 00:06:04 ubuntu-testserver dhcpd: 
Apr 9 00:06:04 ubuntu-testserver dhcpd: Not configured to listen on any interfaces!

---

