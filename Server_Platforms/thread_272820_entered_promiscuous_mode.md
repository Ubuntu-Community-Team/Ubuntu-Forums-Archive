---
title: "entered promiscuous mode"
date: 2006-10-07
forum: Server Platforms
---

### Post by McHenry on 2006-10-07
On startup my server hangs at "Configuring network interfaces" for 10 or more seconds. The following enteries are logged in /var/log/messages

I cannot find a solution to this problem and hope help may be available...

Thanks

Oct  7 13:24:29 declan kernel: [42949388.140000] Bridge firewalling registered
Oct  7 13:24:29 declan kernel: [42949388.150000] bridge: can't decode speed from eth0: 65535
Oct  7 13:24:29 declan kernel: [42949388.150000] device eth0 entered promiscuous mode
Oct  7 13:24:29 declan kernel: [42949388.150000] device tap0 entered promiscuous mode
Oct  7 13:24:29 declan kernel: [42949388.200000] br0: port 2(tap0) entering learning state
Oct  7 13:24:29 declan kernel: [42949389.500000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct  7 13:24:29 declan kernel: [42949389.500000] tg3: eth0: Flow control is on for TX and on for RX.
Oct  7 13:24:29 declan kernel: [42949389.500000] br0: port 1(eth0) entering learning state
Oct  7 13:24:29 declan kernel: [42949403.200000] br0: topology change detected, propagating
Oct  7 13:24:29 declan kernel: [42949403.200000] br0: port 2(tap0) entering forwarding state
Oct  7 13:24:29 declan kernel: [42949404.500000] br0: topology change detected, propagating
Oct  7 13:24:29 declan kernel: [42949404.500000] br0: port 1(eth0) entering forwarding state
Oct  7 13:24:29 declan kernel: [42949405.850000] NET: Registered protocol family 10
Oct  7 13:24:29 declan kernel: [42949405.850000] lo: Disabled Privacy Extensions
Oct  7 13:24:29 declan kernel: [42949405.850000] IPv6 over IPv4 tunneling driver

---

### Post by SticknClutch on 2006-10-09
try disabling promiscuous mode:

```
ubuntu:$ sudo ifconfig eth0 -promisc
```

From the ifconfig man page:
> [-]promisc
              Enable  or  disable  the  promiscuous  mode  of the interface.  If selected, all packets on the network will be received by the
              interface.


---

### Post by McHenry on 2006-10-09
Thanks.

The question remains why did it enter this mode to start with ?

/var/log/messages logs the following which appears to be the cause:

Oct  9 14:22:39 declan kernel: [42949388.480000] Bridge firewalling registered
Oct  9 14:22:39 declan kernel: [42949388.490000] bridge: can't decode speed from eth0: 65535

Any insight into what the bridge problem is ?

Thanks

---

