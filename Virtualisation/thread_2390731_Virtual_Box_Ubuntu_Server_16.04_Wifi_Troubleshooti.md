---
title: "Virtual Box Ubuntu Server 16.04 Wifi Troubleshooting"
date: 2018-05-01
forum: Virtualisation
---

### Post by edumcg on 2018-05-01
Hello, I already installed Ubuntu Server 16.04 (guest) in VirtualBox on my Windows 7 host machine. 
Now I'm having trouble with connecting to internet.
On my VM Seetings I have 1 Bridged Adapter and have selected Realtek RTL8188CE 802.11b/g/n Wifi Adapter. On Advanced I have Promiscuous Mode denied and Cable Connected unchecked.
Here are some logs that could help with the diagnose of my problem.
cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)


source /etc/network/interfaces.d/* 


#The loopback network interface
auto lo
iface lo inet loopback


#The primary network interface
auto enp0s3
iface enp0s3 inet static
address 10.147.168.121
netmask 255.255.192.0
gateway 10.147.128.1
dns-nameservers 8.8.8.8 8.8.4.4

```
ls /sys/class/net
```

enp0s3     lo

```
sudo route -n
```

Kernel IP routing table 
Destination      Gateway              Genmask           Flags  Metric  Ref  Ude     Iface
0.0.0.0            10.147.128.1      0.0.0.0               UG     0         0     0        enp0s3
10.147.128.0   0.0.0.0               255.255.192.0    U       0         0     0        enp0s3

```
ip route list
```

default via 10.147.128.1 dev enp0s3 onlink linkdown
10.147.128.0/18 dev enp0s3  proto kernel scope link  src 10.147.168.121 linkdown

```
ping 8.8.8.8
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data
From 10.147.168.121 icmp_seq=1 Destination Host Unreachable
```
ping google.com
```

ping: unknown host google.com

```
sudo lshw -C network
```

*-network
  description: Ethernet interface
  product: 82540EM Gigabit Ethernet Controller
 vendor: Intel Corporation
  physical id:3
  bus info: pci@0000:00:03.0
  logical name: enp0s3
  version: 02
  serial: 08:00:27:07:9f:a4
  capacity: 1Gbit/s
  width: 32 bits
  clock: 66MHz
  capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
  configuration autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI ip=10.147.168.121 latency=64 link=no mingnt=255 multicast=yes   port=twisted pair
  resources: irq:9 memory:f0000000-f001ffff ioport:d010(size=8)

```
From Windows when I type ipconfig I noticed that the ip con my machine is the same as the one on my vm. I tried to change my ip of my vm to 10.147.168.122 but it stayed the same. 
I also copied and pasted the netmask and gateway from there.
Could someone please tell me if this is accurate?
Some guidance would be appreciated.

---

### Post by wildmanne39 on 2018-05-01
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by TheFu on 2018-05-04
Welcome to the forums.

If cable connect isn't checked, then that device isn't made available to the VM.  Check it and reboot the VM.

Also, the guest will only see a fake-NIC, not the wifi device.  This is VM abstraction.  It is best to use a virtio device for disk and network stuff for virtual machines.  Better performance and lower overhead. If there isn't a virtio device (I don't use vbox), then pick an Intel PRO/1000 device.  This is extremely well supported across all OSes, but has slightly higher overhead than virtio devices.

---

### Post by SeijiSensei on 2018-05-04
The emulated PRO/1000 is the default adapter in VirtualBox.

---

