---
title: "Ethernet connection slow when vmware has its own nic?"
date: 2008-04-26
forum: Virtualisation
---

### Post by supremedalek on 2008-04-26
I bought a Cogent EM 4400 TX 4 port pci card (seen by ubuntu 7.10 as eth1 to eth4) so I could have vmware use its own nic instead of sharing it
with the host OS (7.10 desktop). Reason I chose this card is because it supposedly is supported by ubuntu. So, I went to the vmware config
program and told it to use eth1 and eth2, both in bridge mode, instead of eth0:

```
Your computer has multiple ethernet network interfaces available: eth0, eth2,
eth3, eth4, vmnet1, vmnet8, wlan0. Which one do you want to bridge to vmnet2?
[eth0] eth2

The following virtual networks have been defined:

. vmnet0 is bridged to eth1
. vmnet1 is a host-only network on private subnet 192.168.215.0.
. vmnet2 is bridged to eth2
. vmnet8 is a NAT network on private subnet 192.168.209.0.

Do you wish to make additional changes to the current virtual networks
settings? (yes/no) [yes] no
```

When I restart the only machine I have under vmware, a centos 5 box, and ssh to it, it feels at least twice as sluggish as it was when it was sharing the nic with the host OS. What should I check for? Currently eth1 is associated to the centos client, with static IP in it, but has no IP under ubuntu so that, I hope, there would not be any fighting for it. eth2 is not even connected to my switch.

---

