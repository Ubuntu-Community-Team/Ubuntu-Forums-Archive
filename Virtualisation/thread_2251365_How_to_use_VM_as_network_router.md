---
title: "How to use VM as network router?"
date: 2014-11-03
forum: Virtualisation
---

### Post by equinoxneutraali on 2014-11-03
[COLOR=#333333][FONT=UbuntuRegular]A wireless network (which I have to use in order to be useful XD) seems to allow everything to work except for ubuntu. I've tried using the certificate and copying network settings (except for IP addresses, of course), but to no avail.
 I'm wondering if it's viable to set up a Windows VM in order to use the network, and how I'd go about getting it to access the network hardware in a fashion so that either the VM can access the network with a higher priority than the normal ubuntu OS, or how I would access the network from the normal ubuntu OS through the VM?
Other networks work fine, I should mention XD

[/FONT][/COLOR]

---

### Post by bashiergui on 2014-11-08
If you're having trouble getting wifi to work in ubuntu, then I recommend you search the forum for your computer details to see if there hasn't been a solution. 

I don't expect that a windows guest on an Ubuntu host would fix the problem. The guest will hook into the host's nic, and if the Host nic has no wifi connection neither will the guest.

---

