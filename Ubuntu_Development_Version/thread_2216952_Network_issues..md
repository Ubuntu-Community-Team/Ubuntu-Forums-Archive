---
title: "Network issues."
date: 2014-04-14
forum: Ubuntu Development Version
---

### Post by seth7 on 2014-04-14
I don't know if this is a general problem with 14.04 but as far as I can tell, I've reinstalled 14.04 on a few different daily builds, and my wireless speed is painfully slow, but my wired eth0 speed is even slow. I mean I should be achieving 50 Mbps but even when wired in I'm only able to achieve 30 and my roommates wireless on windows 7 ::shutter:: gets 56 Mbps from speedtest.net

any ideas?

---

### Post by seth7 on 2014-04-15
I know I should have added this earlier but I had to run to work, but here is my hardware information from lshw in terminal [http://pastebin.com/d1TSz4Fi](http://pastebin.com/d1TSz4Fi)
and my kernel version is 3.13.0-24 generic, I did however noticed that a few kernel versions and a few dist-upgrades ago for that matter my wireless and wired interface was working with no slowdowns.

---

### Post by cariboo on 2014-04-15
Your pastebin output doesn't show your wireless adapter, if you could open a terminal and type the following command:

```
sudo lshw -C network
```

and paste the result in your next post, be sure to enclose the pasted info in [noparse]```

```[/noparse] tags.

---

### Post by seth7 on 2014-04-15
> **cariboo907 said:**
> Your pastebin output doesn't show your wireless adapter, if you could open a terminal and type the following command:

```
sudo lshw -C network
```

and paste the result in your next post, be sure to enclose the pasted info in [noparse]```

```[/noparse] tags.

```
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: 00:8c:fa:a2:e3:d3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:77 ioport:3000(size=256) memory:f1000000-f1000fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 64:5a:04:c2:29:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:79 ioport:2000(size=256)
```

---

