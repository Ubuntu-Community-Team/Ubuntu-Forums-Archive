---
title: "Instance remains &quot;pending&quot; after launch until it terminates"
date: 2010-12-22
forum: Ubuntu Cloud and Juju
---

### Post by ajdecon on 2010-12-22
Hello all,

**Summary: when I attempt to run instances on a stock UEC cluster, instances remain in "pending" state until they move to state "terminated", having never been "running".**

I am attempting to set up Ubuntu Enterprise Cloud on a small cluster of four systems, with one "head node" running the cloud, cluster and walrus controllers, and three "compute nodes" running the node controller only.  All nodes are identical Dell Poweredge 1950 servers.  The head node is named euc-head, and the compute nodes are named euc-node-1, euc-node-2, and euc-node-3.  All nodes are fresh installs of UEC from the CD, formatting the drives before installation.

The networking configuration is as follows:
* euc-head: two network interfaces. eth1 is configured as the primary interface with IP address assigned by DHCP. eth0 is the interface used to communicate with the compute nodes, and has static IP address 10.50.50.1.
* euc-node-x: one network interface, eth0, assigned to static IP address 10.50.50.2-4.
* The eth0 interfaces of all nodes are VLAN'd together at the switch to avoid exposing the DHCP server to the larger network. eth1 of euc-head is exposed to the rest of the (corporate) network.

The default UEC installation produces a Eucalyptus installation in MANAGED-VLAN mode.  While public-key exchange occurred at boot time, the compute nodes did not auto-register their node controllers; I had to do this manually via 
$ sudo euca_conf --register-nodes "10.50.50.2 10.50.50.3 10.50.50.4"

I was able to bundle and upload an image successfully (using the supplied Debian image on the Eucalyptus website), but when I run the instance, it remains pending for a long time (> 1 hour) before terminating, having never entered the state "running".

I would appreciate any guidance as to how to diagnose and fix this problem.  I don't see any obvious "smoking guns" in the logs but this is my first experience with Eucalyptus.  If particular logs would be useful, please let me know and I will post them.

Thanks,
Adam

---

### Post by Rusty au Lait on 2010-12-22
I have found increasing the space say from m1.small to c1.medium has worked for me. Also, see if euca-get-console-output gives you any information.

Welcome and good luck. I find UEC fascinating.

---

### Post by ajdecon on 2010-12-22
> **Rusty au Lait said:**
> I have found increasing the space say from m1.small to c1.medium has worked for me. Also, see if euca-get-console-output gives you any information.

Welcome and good luck. I find UEC fascinating.

Thanks for the suggestion, and the welcome.  Unfortunately a larger instance (m1.large) experiences the same problem.  As far as I can tell, euca-get-console-output does not work until the state reaches "running".

---

### Post by raymdt on 2010-12-23
Hi ajdecon,
which version of euca2ools did you use to bundle the image? 
If you are new to UEC, i suggest you to use first the images from ubuntu's store to become familiar with eucalyptus.
Regards

---

### Post by Rusty au Lait on 2010-12-23
Sorry. I went back and tried get-console on a pending instance. There are logs on the NCs in the same place as on the CLC. raymdt's suggestion to get an image that is known to work is where I would start.

I had problems with the two nics on the CLC. The iptables are complicated and caused me trouble setting up. I stopped using the second nic and have not returned to the problem since then (too lazy).
Here's someone else with a similar problem.
[http://ubuntuforums.org/showthread.php?p=9865313](http://ubuntuforums.org/showthread.php?p=9865313)

---

### Post by miszko on 2010-12-23
Check /var/log/eucalyptus/nc.log on nodes.
Did you have enabled vt-x in BIOS? 
Typical log errors (in nc.log) when vt-x isn't enabled in bios:
```

[EUCAERROR ] libvirt: internal error no supported architecture for os type 'hvm' (code=1)
[EUCAFATAL ] hypervisor failed to start domain

```

I had the same problem. Instance never run (long time pending, after few minutes - terminated). 


(Sorry for my bad english)

---

### Post by Yan Naing Kyaw on 2011-03-24
Hello all,
                
I am attempting to set up Ubuntu Enterprise Cloud on a small cluster of two  systems, with one "head node" running the cloud, cluster and walrus  controllers, and one "compute node" running the node controller  only.
Network Configuration are as follows:

1) In Cloud Controller
[LIST]
[*]/etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.78.213
netmask 255.255.255.0
network 192.168.78.0
broadcast 192.168.78.255
gateway 192.168.78.1
dns-nameservers 192.168.64.3
dns-search ucsy.edu.sites

/etc/default/image-store-proxy

DEMO_OPTIONS=""
export http_proxy=http://192.168.64.3:8080
export https_proxy=https://192.168.64.3:8080
export no_proxy=localhost,127.0.0.1
[/LIST]
2) Node Controller
/etc/network/interfaces
[INDENT]auto eth0
 iface eth0 inet static
 address 192.168.78.213
 netmask 255.255.255.0
 network 192.168.78.0
 broadcast 192.168.78.255
 gateway 192.168.78.1

I lunch instance of an image via Elasticfox , and then associate elastic IP. Instances get both public IP (192.168.78.245) and private IP(172.19.1.2). But it never reach to running state.

In node controller ,
                         /var/log/eucalyptus/nc.log

there are only two walrusrequest(), kernel and kernel-digest

ls /var/lib/eucalyptus/instances//admin/<instances-id>/ -a show:
                                                                      kernel kernel-digest

what I can do to fix the problem ????
Please help me .
I hope your replies.
Thanks you all.



[/INDENT]

---

