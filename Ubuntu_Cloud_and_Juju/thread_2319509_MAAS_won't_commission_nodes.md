---
title: "MAAS won't commission nodes"
date: 2016-04-04
forum: Ubuntu Cloud and Juju
---

### Post by Gary_Haegens on 2016-04-04
Hi All, my first post which follows weeks of frustration following the simple process of installing MAAS and commissioning nodes.  I have built a single install based on LXC and all virtual nodes come up as ready.  I have other hardware to use to build an environment and nothing I do will get a single server to ready state.
I have the first/maas node as a Dell 2900 Tower.  All is well with the build and install.  I try to discover or manually add a Dell R710 and it fails every time.  I have even rebuilt the first node to be sure it was not the build that causes the issue.

So can someone advise how to set up the maas node and new/R710 node so that it will commission successfully.
What I did was set up the network as specified (even though the install of MAAS is version 2, with no up to date doco,  and I don't know how to roll back to an earlier version).
I specified the impi version and added the mac addresses of the primary nic and iDrac nics plus access account and password details.  It successfully manages power and pxe boots the server then the server sits there doing nothing and a commission timeout occurs.

Does anyone have a similar issue or any clue where to look to resolve this issue?  Thanks in advance.

---

### Post by Gary_Haegens on 2016-04-05
OK, we resolved the issue.The issue is that we were using a switch that had a flat vlan and was not doing any forwarding or other smarts, e.g. no definition for 192.168.10.1 existed anywhere.  This means that any definition of the private gateway to , e.g. 192.168.10.1, will fail when the node is trying to commission.  Ergo we set the gateway of the private network to the private address (192.168.10.21) of the MAAS server in the MAAS network definitions and restarted the nodes and voila, we have commissions.  So thanks all.

---

