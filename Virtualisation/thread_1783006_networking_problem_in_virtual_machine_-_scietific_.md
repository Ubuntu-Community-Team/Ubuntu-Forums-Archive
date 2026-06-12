---
title: "networking problem in virtual machine - scietific linux"
date: 2011-06-15
forum: Virtualisation
---

### Post by oren tal on 2011-06-15
Hi, I am running scientific linux guest on ubuntu host.

The problem is that the guest machine doesn't have any ip except from the loopback.


I want that the guest OS will be in the same local network of the host and not part of internal network that virtualbox create.
In other words I want other computers in the same local network of the host to be able to connect the guest OS as if anther computer was added to the network.

How can I do that?

I tried bridge but for some reason it doesn't work for me.

---

### Post by Perryg on 2011-06-16
For what you are wanting you will need to use Bridged. Set it to Bridged and then figure out what needs to be done.  Can the guest see the network adapter ?  (lspci) Have you configured the guest network adapter?

---

