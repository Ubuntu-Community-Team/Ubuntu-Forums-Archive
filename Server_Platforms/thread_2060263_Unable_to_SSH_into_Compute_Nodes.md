---
title: "Unable to SSH into Compute Nodes"
date: 2012-09-19
forum: Server Platforms
---

### Post by vbharadw on 2012-09-19
Hi there,

I am new to cluster management and administration.

We have a cluster that runs on 10.04.2 LTS. There is a head node and with 9 nodes connected to it. The cluster was working fine but presently we are unable to ssh into any of the compute nodes.

vbharadwaj@deepblue:~$ ssh deepblue-1-5
ssh: connect to host deepblue-1-5 port 22: No route to host

I have checked that the compute nodes were switched on.

I have also checked that the compute nodes are physically wired to the Netgear switch and that the head node is also wired to the switch.

I am able to remotely login to the head-node so I think SSH is working.

What are the diagnostic tests that I need to do to find out what is wrong with the system?

---

### Post by CharlesA on 2012-09-19
Check the firewall.

---

