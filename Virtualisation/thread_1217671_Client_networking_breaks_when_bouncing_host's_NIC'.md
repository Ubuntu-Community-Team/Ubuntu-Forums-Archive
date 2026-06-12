---
title: "Client networking breaks when bouncing host's NIC's"
date: 2009-07-19
forum: Virtualisation
---

### Post by freakalad on 2009-07-19
Not sure if this is a bug, or a mis-configuration on my part.

Have multiple clients running on system (both Linux/Unix & win), connecting to LAN via br0 (as per docco suggestions)

We have multiple gateways on the LAN, each connecting to a different ISP (for testing & redundancy reasons).

Frequently I need to change the gateway for br0, & keep the rest of the config the same, including br0's static IP. I achieve this by having the different configs in files, say,  /etc/network/interfaces.GW1 & interfaces.GW2, and simply copy these configs over the existing interfaces file & restart the networking service: `sudo /etc/init.d/networking restart` or a force-reload

The networking for my host comes up fine & br0 has the new gateway configures, but networking to the clients become unresponsive, and in some severe cases the clients crash (incl. win BSoD)

I've tried bouncing only the libvirt service, but to no avail.
I need to kill-9 all running KVM sessions & manually restart the KVM daemon, then libvirtd, in order to get going again

---

