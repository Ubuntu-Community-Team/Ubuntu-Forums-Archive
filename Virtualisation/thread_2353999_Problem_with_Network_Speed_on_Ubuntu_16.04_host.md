---
title: "Problem with Network Speed on Ubuntu 16.04 host"
date: 2017-02-27
forum: Virtualisation
---

### Post by Neural oD on 2017-02-27
Hi All

I've been scratching my head, and have looked all over the internet, but can't come up with a solution. Hopefully someone here can help out. I'm fairly new in the kvm virtualisation space, but know my way around ubuntu and linux. 
Let me describe what's happening. 
I've set up ubuntu 16.04 as a server host for KVM vm's. I set up bridged networking, so that my local network can access the virtual machines and visa-versa. The Bridge is recognised, and I have comms as I want to. The issue is that I can't get more than 10Mb/s to either the host or the virtual machines. What I'm suspecting is that in ubuntu the bridge is set up, and ubuntu can't recognise the virtual nic's or bridge as being able to handle more than this speed. 
This is from the host: 
lshw -c Network
```
 *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5719 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eno1
       version: 01
       serial: 40:a8:f0:27:ed:64
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5719-v1.46 NCSI v1.3.16.0 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:51 memory:f6bf0000-f6bfffff memory:f6be0000-f6beffff memory:f6bd0000-f6bdffff memory:f4000000-f403ffff
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5719 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: eno2
       version: 01
       serial: 40:a8:f0:27:ed:65
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5719-v1.46 NCSI v1.3.16.0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 memory:f6bc0000-f6bcffff memory:f6bb0000-f6bbffff memory:f6ba0000-f6baffff memory:f4040000-f407ffff
  *-network:2 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5719 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eno3
       version: 01
       serial: 40:a8:f0:27:ed:66
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5719-v1.46 NCSI v1.3.16.0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:51 memory:f6b90000-f6b9ffff memory:f6b80000-f6b8ffff memory:f6b70000-f6b7ffff memory:f4080000-f40bffff
  *-network:3
       description: Ethernet interface
       product: NetXtreme BCM5719 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0.3
       bus info: pci@0000:03:00.3
       logical name: eno4
       version: 01
       serial: 40:a8:f0:27:ed:67
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5719-v1.46 NCSI v1.3.16.0 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:52 memory:f6b60000-f6b6ffff memory:f6b50000-f6b5ffff memory:f6b40000-f6b4ffff memory:f40c0000-f40fffff
  *-network:0
       description: Ethernet interface
       physical id: 3
       logical name: vnet0
       serial: fe:54:00:d6:21:44
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=yes multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1
       description: Ethernet interface
       physical id: 4
       logical name: vnet4
       serial: fe:54:00:b0:ff:53
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=yes multicast=yes port=twisted pair speed=10Mbit/s
  *-network:2
       description: Ethernet interface
       physical id: 5
       logical name: vnet3
       serial: fe:54:00:43:7d:4d
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=yes multicast=yes port=twisted pair speed=10Mbit/s
  *-network:3
       description: Ethernet interface
       physical id: 6
       logical name: vnet2
       serial: fe:54:00:7b:a0:98
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=yes multicast=yes port=twisted pair speed=10Mbit/s
  *-network:4
       description: Ethernet interface
       physical id: 7
       logical name: vnet1
       serial: fe:54:00:c6:ac:b5
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=yes multicast=yes port=twisted pair speed=10Mbit/s

```
As can be seen the physical nics have a Gbit/s capacity, but somehow the virtual(vnet) have only 10Mbit/s. 
I've tried using ethtool etc, to no avail. 

Could someone please point me in the right direction. I don't think there's a problem with the virtio drivers I'm using, cause the guests, seem to be showing the correct speeds, however the host virtual nics seem capped at that 10Mbit/s 

Any help would be appreciated.

---

### Post by KillerKelvUK on 2017-02-27
Hey, think this is bogus tool outputs instead of an actual speed limitation...unless you've performance tested to prove it?

Regardless I get the same results from my 16.04 host, I run two Ubuntu vm's with virtio and a Windows 10 vm also with virtio.  Host side says the vnet connections are 10Mbit/s, guest side is a different story...Ubuntu ethtool says the speed is unknown but Windows correctly reports the speed at 10.0Gbps.  Quick google on why linux doesn't report the link speed of a virtio network adapter and I find [http://serverfault.com/questions/738840/get-link-speed-of-an-virtio-net-network-adapter](http://serverfault.com/questions/738840/get-link-speed-of-an-virtio-net-network-adapter).  Have a read of the linked bug report and as I'm running a kernel greater than 4.4.0-25.44 ethtool can now set the speed of the link within the guest...

```

sudo ethtool ens3
[sudo] password for xxx: 
Settings for ens3:
	Supported ports: [ ]
	Supported link modes:   Not reported
	Supported pause frame use: No
	Supports auto-negotiation: No
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Other
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Link detected: yes
sudo ethtool -s ens3 speed 100000 duplex full
sudo ethtool ens3
Settings for ens3:
	Supported ports: [ ]
	Supported link modes:   Not reported
	Supported pause frame use: No
	Supports auto-negotiation: No
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100000Mb/s
	Duplex: Full
	Port: Other
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Link detected: yes

```

How's this play out for you?

---

### Post by Neural oD on 2017-02-27
I think my problem is that the vnet(virtual adapters) don't seem to be managed by ethtool. I had tried this earlier....see output:
```
anthony@UB1:~&#10219; sudo ethtool br4
[sudo] password for anthony: 
Settings for br4:
        Link detected: yes
anthony@UB1:~&#10219; sudo ethtool vnet4
Settings for vnet4:
        Supported ports: [ ]
        Supported link modes:   Not reported
        Supported pause frame use: No
        Supports auto-negotiation: No
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        MDI-X: Unknown
        Current message level: 0xffffffa1 (-95)
                               drv ifup tx_err tx_queued intr tx_done rx_status pktdata hw wol 0xffff8000
        Link detected: yes
anthony@UB1:~&#10219; sudo ethtool -s vnet4 speed 10000 duplex full
Cannot set new settings: Operation not supported
  not setting speed
  not setting duplex

```

Have you got bridging on your setup?

---

### Post by KillerKelvUK on 2017-02-27
Yeah using the linux-bridge package.

You're using ethtool host side in your snippet, my code snippet was guest side.

---

### Post by Neural oD on 2017-02-27
ok - I've tried on the host side, let me try running that on the guest side, problem is though, I've set up 3 guests - windows, bsd, and a test ubuntu server. Let me try running that on the test ubuntu server, and see what the output is

---

### Post by Neural oD on 2017-02-27
Hi - ran this on the guest - see pic, sorry haven't set up ssh to get the info across to me, so sending a pic....
[IMG]http://imgur.com/a/tKw14[/IMG]

[http://imgur.com/a/tKw14](http://imgur.com/a/tKw14)
link to pic

---

### Post by Neural oD on 2017-02-27
as you can see, the guest is reporting correctly the speed. I think the bottleneck is the speed that the vnet[0-4] are reporting on the host side.
I've done speed tests using nc and iperf to the host & the guests - and it's maxing out at around 10Mbit/s

---

### Post by KillerKelvUK on 2017-02-27
Actually that screenshot you linked to imgur, if that's from your guest they you've not set the guest up to use virtio for the NIC, am expecting something like...

```

*-network               
       description: Ethernet interface
       product: Virtio network device
       vendor: Red Hat, Inc

```

---

### Post by Neural oD on 2017-02-27
sorry - my bad, I'd forgotten that one guy had asked me to change the emulation in the guest to e1000, to test....
Here is the link once I changed the emulation: 
[http://imgur.com/a/XYDas](http://imgur.com/a/XYDas)

---

### Post by Neural oD on 2017-02-27
herewith the speed test I ran on the guest, after the change back to virtio:
```
&#10008; anthony@Lenovo-z51 &#57520; ~ &#57520; pv -t -r -a -b /dev/zero | nc -v -v -n 192.168.10.55 2223 >/dev/null
Connection to 192.168.10.55 2223 port [tcp/*] succeeded!
^C02MiB 0:00:27 [11.2MiB/s] [11.2MiB/s]

```

---

### Post by Neural oD on 2017-02-27
I feel that if I can change those vnet speed settings(on the host) this issue will be resolved.....just not sure how to do that...

---

### Post by KillerKelvUK on 2017-02-27
Have you done any explicit files transfer using nfs or samba and rated them?  That command you used to "test" the speed has given me 10 different results 10 times, as the networking involved here is virtual a proportion of performance is going to be around the compute resources you've allocated to your guest.  I think ultimately there may not be anything broken...

I've just transferred a file from an NFS server (NAS) to my vm using pv and 5Gb took 81 seconds to complete which is about 65MB/s transfer rate.  The NAS here will be a bottle neck as its a cheap Asustor 4 bay box and the guest vm has 2 vcpus running at 3.2Ghz per vcpu.  All this whilst the host reports the vnet speed as 10Mbit/s. 

```

Host view below.

*-network:0
       description: Ethernet interface
       physical id: 1
       logical name: vnet0
       serial: xx:xx:xx:xx:xx:xx
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=yes multicast=yes port=twisted pair speed=10Mbit/s

```

---

### Post by Neural oD on 2017-02-28
@KillerKelvUK - sorry for the delay, I'd left site this side, was late in the evening, and very spotty comms where I stay atm(Deep in the bush in Africa) :P

To get back to your question, no I haven't tried with samba or nfs. I had just tried the nc and ipref, both gave me consistent same results. I will try that this morning, as per your advise. I was trying some other things, came across some info on the net, with someone with similar issues, they'd said that when they re-installed, the problems went away. I don't really want to do that - but if I'm forced, might have to. Have spent many hours on this, so I'll try a couple of other things, before going nuclear on the system....

---

