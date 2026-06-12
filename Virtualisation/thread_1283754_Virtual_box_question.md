---
title: "Virtual box question"
date: 2009-10-05
forum: Virtualisation
---

### Post by RedSingularity on 2009-10-05
How can i set my Ubuntu server install to have its own IP on my network within the virtual machine?  Right now it has a crazy IP i have never seen.  For example it should have 192.168.1.4 but it has something like 10.0.1.2

Something with the network settings of virtual box?  (NAT vs Bridged?)

---

### Post by Perryg on 2009-10-06
That address belongs to the NAT address range built in VBox.  Switch the guest to use Bridged (you must have a router) and you should be in your local net address scheme.  After that if you really want to make it easy the set the guest IP address to static and you are good to go.
You need to shut down the guest and change this in the guest settings.

---

### Post by RedSingularity on 2009-10-06
Great.  Thanks buddy :)

---

