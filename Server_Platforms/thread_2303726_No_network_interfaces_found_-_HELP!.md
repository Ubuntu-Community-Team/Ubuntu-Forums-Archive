---
title: "No network interfaces found - HELP!"
date: 2015-11-21
forum: Server Platforms
---

### Post by soamz on 2015-11-21
Im trying to install Ubuntu server and it shows me this error. 

But the backside 2 gigabit ports are showing the light fine. 
How to fix this ??

[ATTACH=CONFIG]265700[/ATTACH]

---

### Post by cariboo on 2015-11-22
We need more information before we can help you. If you have a Live CD I'd suggest you boot from that, and run the following command:

```
sudo lshw -C network
```

post the output in your next post.

The output should look similar to this:

```
sudo lshw -C network
[sudo] password for cariboo: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 09
       serial: e0:3f:49:a4:8d:f7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.0.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
```

**Note:** I'm running Xenial with kernel 4.2.0-19, which doesn't use the standard device names any more, my NIC is seen as enp2s0 instead of eth0.

---

