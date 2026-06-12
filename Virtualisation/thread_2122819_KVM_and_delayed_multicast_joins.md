---
title: "KVM and delayed multicast joins"
date: 2013-03-06
forum: Virtualisation
---

### Post by khimaera on 2013-03-06
Hi all,

I have a KVM host and a guest both running 12.04 LTS.

At startup, a user process joins a multicast group. 

When I start the process manually, I can see the multicast join packets sent when the socket is created.
When I reboot the guest OS, the process is restarted, and I can also see the join packets sent immediately.

The strange thing is that when I reboot the host, the guest is restarted automatically, the user process is also started, but the multicast join packets are not sent immediately. 
I have to wait for up to 3-4 minutes to see them with wireshark.

Do you have any idea ?

Thanks...

---

### Post by khimaera on 2013-03-06
I have done some testing...

A tcpdump capture in the guest indicates that multiple multicast joins are sent in the first minutes.
They are correctly received on the vnet0 on the host, but the host bridge does not forward them.

After a few minutes,the bridge starts forwarding it.

Strange...

---

### Post by khimaera on 2013-03-07
Found it !

No more delay when you disable multicast snooping on the host:

echo 0 > /sys/devices/virtual/net/br0/bridge/multicast_routerecho 0 > /sys/devices/virtual/net/br0/bridge/multicast_snooping

---

