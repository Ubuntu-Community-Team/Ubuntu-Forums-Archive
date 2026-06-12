---
title: "windows guest networking interferes with host network"
date: 2008-07-17
forum: Virtualisation
---

### Post by bobdobbs on 2008-07-17
Hi.

I've got an XP guest in vmware desktop, 6.04.
Host os is Heron.

After setting it up, I didnt test the network.

After I rebooted the host, I found that I couldn't get the host onto the network.

Turns out that the vmware setup had added a couple of network interfaces.

When I removed them using ifconfig, the host can then access the net.

But, my guest OS now has no connectivity.

How can I get my guest OS online ?


Thanks.

---

