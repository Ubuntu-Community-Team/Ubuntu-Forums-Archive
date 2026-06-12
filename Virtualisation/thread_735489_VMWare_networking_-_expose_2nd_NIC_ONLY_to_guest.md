---
title: "VMWare networking - expose 2nd NIC ONLY to guest"
date: 2008-03-25
forum: Virtualisation
---

### Post by trd79 on 2008-03-25
Hi,

I am trying to test a router/firewall setup within VMWare. In order to do this I have installed a 2nd NIC in my host machine. The idea is that this will be connected to the WAN and a guest machine will act as gateway to rest of network.

My problem is that I cannot seem to make the 2nd NIC available to the guest OS without it being visible to the host OS as well.

Set up is as follows:

Host:
eth0 - internal network - set up as normal, connects to VMNet0
eth1 - WAN - connected to VMNet2 (do not want this to be visible to host)

Guest:
eth0 - connected to VMNet2 - external side of gateway
eth1 - connected to VMNet0 - internal side of gateway

Currently the guest is working as planned, but only when eth1 is enabled and working on the host (allowing users on the host to connect to the WAN without going via the guest OS).

Hope this makes sense!

---

### Post by veloce on 2008-03-27
Yes it makes sense but I don't think you can do what you want.

I think the nic has to be available to the host to be visible to the guest.

The closest I think you'll get is to set up your routing on the host so that everything coming in on that nic is directed to the guest.

---

### Post by trd79 on 2008-03-28
Hi,

Cheers for the reply.
Think I have solved it with the following setup on the host:

```
ifconfig eth1 0.0.0.0 up
```

This way the interface is up and available to the VM, but host will not use the interface as no IP address.

Hope this is of use to someone else.

---

