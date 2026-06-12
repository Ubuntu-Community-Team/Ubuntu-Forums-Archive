---
title: "Network bridge doesn't work if host machine changes IP (static DHCP)"
date: 2017-02-08
forum: Virtualisation
---

### Post by kevpatts2 on 2017-02-08
I have a problem with a KVM/QEMU host that I need to change the IP address of.

The host uses DHCP and the DHCP server sets it's MAC address to x.y.z.111. This was fine and the client machines picked up DHCP aswell as x.y.z.112 and x.y.z.113.

When I changed the DHCP server to give the host a new address (x.y.z.34) and rebooted the host, it gets this IP but the client machines can no longer connect to the outside world. They fail to DHCP and don't get any IP. If I force the correct IP (using sudo ifconfig x.y.z.112 for example) they can then ONLY ping the host machine at x.y.z.34, but nothing else outside on the same subnet.

I completely purged libvirt, qemu and anything to do with them, reinstalled and the same issue persisted. Everything to do with the bridge and routes look correct.

To resolve I changed the DHCP server to give it x.y.z.111 again and the clients started to work!

I can change the clients IP addresses without issue, but get this problem if I change the host.

I've googled but not found someone having the same problem. Can anyone help? I need to change the IP.

---

