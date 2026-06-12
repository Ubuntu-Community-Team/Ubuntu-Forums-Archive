---
title: "Node added to MAAS, doesn't work?"
date: 2012-05-29
forum: Server Platforms
---

### Post by Tovam on 2012-05-29
I am trying to get an Ubuntu private cloud running, but things don't work as I expected them to. I am not sure if the problem lies with the servers or with me.
I am using Ubuntu Server 12.04 64 bit, on a couple of Intel Blade servers with a cd as the install medium.

First I installed the Maas server. It runs fine and I can access the MAAS management through http without a problem.
Then I proceed to installing the first node. I follow the same process, selecting "multiple server install with Maas", giving it a hostname and a static ip and so on. Then it gives the option to add the node to an existing Maas, and I select my first server. The second server sigterms, which seems to be intended behaviour. That's I start to get confused.

The Maas server says that one node has been added to the Maas, but the node is turned off and doesn't come back on (wakeup on lan is enabled). When I manually boot the node, it still contains a previous install.
This is what confuses me; Why isn't there anything installed on the first node? Is this an error of some kind, or is it intended behaviour (since I read that the sigterm is intended as well)? Then how will the server be able to use the resources of the node?

Can someone tell me if the problem lies with the server, or if I am simply understanding the concept of Maas wrongly? Either way, can someone explain what I have to change to get it to work?
I checked Google, but I mainly got results of older releases of Ubuntu Server, and even then they didn't answer my questions.
Thanks.

---

### Post by Tovam on 2012-05-29
I found a note that says the disk of the node should be empty and that the node should be set for wakeup on lan and PXE boot. This makes a lot more sense. I will experiment some more and hope that solves it.

---

### Post by griffinmt on 2012-10-14
I am finally getting around to doing the same thing that you are doing. But as it turns out, my network interface does not support PXE. What I want to do is build a bootable CD (or even diskette) that will simulate the PXE process and network load my server image. There is no bootable system on the server hard drive, just in case.

Any ideas??

Martyn

---

