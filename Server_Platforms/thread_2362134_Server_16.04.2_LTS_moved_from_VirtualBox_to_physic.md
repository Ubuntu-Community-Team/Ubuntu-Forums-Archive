---
title: "Server 16.04.2 LTS moved from VirtualBox to physical machine and cannot bring up NIC"
date: 2017-05-24
forum: Server Platforms
---

### Post by KMStory on 2017-05-24
I ended up fixing this while preparing my write-up of my problem; I'm posting it here in in case someone else runs into a similar issue.

[size=+3]**Current Machine:**[/size]
Dell Optiplex 320
Ubuntu Server 16.04.2 LTS
Kernel: 4.4.0-62-generic

[size=+3]**Problem:**[/size]
I can't bring up or configure the ethernet adapter in any meaningful way.

[size=+3]**Background:**[/size]
I'm an IT intern (and the only IT person entirely) at a non-profit community center/daycare. I'm trying to set up a Web server to host an asset management system (Snipe IT) and help desk ticket system (Open Supports) on the internal network. I started with a VM in virtualbox to test and prep, then I captured the VM image with FOG and deployed it to a spare physical machine. I didn't do anything to prep my VM, which was a huge oversight, since the VM's bridged adapter is obviously unavailable on the new machine. The OS sees the NIC and loads the correct drivers, but I can't get any IPv4 address on it, through DHCP or static configurations.

[size=+3]**Command outputs:**[/size]
<ifconfig>:
Nothing listed besides the loopback info

<ifconfig -a>:
```

eth0	Link encap:Ethernet HWaddr 00:1a:a0:1f:65:dd
	inet6 addr: 2603:300f:1602:4700:21a:a0ff:fe1f:65dd/64 Scope:Global
	inet6 addr: fe80::21a:a0ff:fe1f:65dd/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets: 31356 errors:0 dropped:429 overruns:0 frame:0
	TX packet:23 errors: 0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:3818438 (3.8 MB) TX bytes:2118 (2.1 KB)
	Interrupt:21

```

<dmesg>
(Gathered using:
	sudo dmesg | grep b44
	sudo dmesg | grep ssb
	sudo dmesg | grep IPv
	sudo dmesg | grep pcnet32
And reconstructed in order)

```

2.304290] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
2.308344] ssb: core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
2.308355] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
2.308364] ssb: core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
2.348345] ssb: Sonics Silicon Backplane found on PCI device 0000:02:09.0
2.353859] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
...
2.397639] b44 ssb0:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1a:a0:1f:65:dd
...
107.930900] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
110.800191] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
110.800201] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
110.800358] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
172.168350] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
172.168362] e1000: Copyright (c) 1999-2006 Intel Corporation.
180.454701] pcnet32: pcnet32.c:v1.35 21.Apr.2008 [email]tsbogend@alpha.franken.de[/email]

```

<sudo lshw>
```

*-pci:1
...
	*-network
		description: Ethernet interface
		product: BCM4401-B0 100Base-TX
		vendor: Broadcom Corporation
		physical id: 9
		bus info: pci@0000:02:09.0
		logical name: eth0
		version: 02
		serial: 00:1a:a0:1f:65:dd
		size: 100Mbit/s
		capacity: 100Mbit/s
		width: 32 bits
		clock: 33MHz
		capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
		configuration: autonegotation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
		resources: irq:21 memory:dfcfe000-dfcfffff

```


[size=+3]**File contents:**[/size]

/etc/udev/rules.d/
Completely empty. 

/run/network/ifstate
```

lo=lo

```

Syslog:
```

May 24 07:01:35 FBG-IT ifup[900]: /bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-pre-up.d/ethtool
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-pre-up.d/ifenslave
May 24 07:01:35 FBG-IT ifup[900]: + [ meta = meta ]
May 24 07:01:35 FBG-IT ifup[900]: + exit 0
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-pre-up.d/vlan
May 24 07:01:35 FBG-IT ifup[900]: Configuring interface lo=lo (inet)
May 24 07:01:35 FBG-IT ifup[900]: /bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-pre-up.d/ethtool
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-pre-up.d/ifenslave
May 24 07:01:35 FBG-IT ifup[900]: + [ inet = meta ]
May 24 07:01:35 FBG-IT ifup[900]: + IF_BOND_SLAVES=
May 24 07:01:35 FBG-IT ifup[900]: + [  ]
May 24 07:01:35 FBG-IT ifup[900]: + [  ]
May 24 07:01:35 FBG-IT ifup[900]: + [ -z  ]
May 24 07:01:35 FBG-IT ifup[900]: + exit
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-pre-up.d/vlan
May 24 07:01:35 FBG-IT ifup[900]: /bin/ip link set dev lo up
May 24 07:01:35 FBG-IT ifup[900]: /bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/000resolvconf
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/ethtool
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/ifenslave
May 24 07:01:35 FBG-IT ifup[900]: + [ inet = meta ]
May 24 07:01:35 FBG-IT ifup[900]: + [  ]
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/ip
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/openssh-server
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/upstart
May 24 07:01:35 FBG-IT ifup[900]: /bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/000resolvconf
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/ethtool
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/ifenslave
May 24 07:01:35 FBG-IT ifup[900]: + [ meta = meta ]
May 24 07:01:35 FBG-IT ifup[900]: + exit 0
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/ip
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/openssh-server
May 24 07:01:35 FBG-IT ifup[900]: run-parts: executing /etc/network/if-up.d/upstart

```

Plus the information I gathered from dmesg

<sudo ethtool -i eth0>
```

driver: b44
version: 2.0
firmware-version:
expansion-rom-version:
bus-info:0000:02:09.0
supports-statistics:yes
supports-test:no
supports-eeprom-access: no
supports-register-dump: no
supports-priv-flags: no

```

[size=+3]**Attempted solutions:**[/size]
I've tried configuring IPV4 settings in /etc/network/interfaces (it wasn't listed there to begin with), but that does nothing.

I tried creating /etc/udev/rules.d/70-persistent-net.rules file using this example: [https://gist.githubusercontent.com/droneboost/8704933a3c498127400806000e6cbd50/raw/0a30c28f43a3e451689669578899bb1cc4d1027e/HowTo:%2520Fix%2520a%2520missing%2520eth0%2520adapter%2520after%2520moving%2520Ubuntu](https://gist.githubusercontent.com/droneboost/8704933a3c498127400806000e6cbd50/raw/0a30c28f43a3e451689669578899bb1cc4d1027e/HowTo:%2520Fix%2520a%2520missing%2520eth0%2520adapter%2520after%2520moving%2520Ubuntu) and plugging in the information I gathered from the commands I ran, but it didn't make any difference.

When I run <sudo ifup -a>, the only change is that <ifconfig> then shows the same output that <ifconfig -a> showed before.

I added eth0=eth0 to /run/network/ifstate, but that did nothing.


I tried running the script given as a solution to a similar problem here: [https://communities.vmware.com/message/436507#436507](https://communities.vmware.com/message/436507#436507)
I then rewrote /etc/iftab to contain:
```

eth0 SYSFS{device} 0000:02:09.0 SYSFS{device/driver} b44 SYSFS{address} 00:1a:a0:1f:65:dd SYSFS{type} 1

```

[size=+2]**This final solution is what worked for me.**[/size]


After each attempted solution, I've tried:
```

sudo service networking restart
sudo ifdown eth0 && sudo ifup eth0
sudo ifconfig eth0 down && sudo ifconfig eth0 up
sudo reboot

```

---

### Post by KMStory on 2017-05-24
While collecting all this information and writing this out, I decided to manually rewrite /etc/iftab, since the script hadn't worked.
I rewrote /etc/iftab to contain:

eth0 SYSFS{device} 0000:02:09.0 SYSFS{device/driver} b44 SYSFS{address} 00:1a:a0:1f:65:dd SYSFS{type} 1

Then, I did a simple <sudo ifup eth0> and it worked! I did forget to include "auto eth0" in my /etc/network/interfaces when I configured it, which prevented it from being started on boot. I added that, and now everything works well!

---

