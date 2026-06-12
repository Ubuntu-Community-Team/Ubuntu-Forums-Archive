---
title: "A tail of two virtual NICs"
date: 2013-01-04
forum: Server Platforms
---

### Post by pagirard on 2013-01-04
Hi all,

I have a server onto which I have installed Ubuntu server, configured with 2 NIC (eth0 and eth1), each on a separate network:

```
eth0      Link encap:Ethernet  HWaddr 00:9c:02:a8:41:02  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::29c:2ff:fea8:4102/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2674042 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1712385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1076151792 (1.0 GB)  TX bytes:941180242 (941.1 MB)
          Interrupt:16 Memory:fbbe0000-fbc00000 

eth1      Link encap:Ethernet  HWaddr 00:9c:02:a8:41:03  
          inet addr:172.16.65.254  Bcast:172.16.65.255  Mask:255.255.255.0
          inet6 addr: fe80::29c:2ff:fea8:4103/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:636856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1487165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127210984 (127.2 MB)  TX bytes:1653925310 (1.6 GB)
          Interrupt:17 Memory:fbce0000-fbd00000 
```

Everything works fine there, now on this server, I have installed a virtual machine using VBox to install a Virtual-UbuntuServer, with 2 virtual NICs (let's call them v_eth0 and v_eth1)

And I have bridge them to their respective "real" NIC on the real server

```
NIC 1:           MAC: 08002731D119, Attachment: Bridged Interface 'eth0', Cable connected: on, Trace: off (file: none), Type: Am79C973, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
NIC 2:           MAC: 080027A6133A, Attachment: Bridged Interface 'eth1', Cable connected: on, Trace: off (file: none), Type: Am79C973, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
```

When I connect to the virtual machine, I can clearly see the two virtual adapters (using lshw -c network)
```
*-network:0             
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 40
       serial: 08:00:27:31:d1:19
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pcnet32 driverversion=1.35 duplex=full ip=192.168.1.28 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:d020(size=32) memory:f0000000-f0000fff memory:f0080000-f00fffff
  *-network:1
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth1
       version: 40
       serial: 08:00:27:a6:13:3a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pcnet32 driverversion=1.35 duplex=full latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:d060(size=32) memory:f0804000-f0804fff memory:f0880000-f08fffff
```


For simplifity, I have configured both adapters with dhcp but I can't seem to start eth1.

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#Linux network
auto eth1
iface eth1 inet dhcp
```

result of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:31:d1:19  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe31:d119/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:514443 (514.4 KB)  TX bytes:11731 (11.7 KB)
          Interrupt:19 Base address:0xd020 

eth1      Link encap:Ethernet  HWaddr 08:00:27:a6:13:3a  
          inet6 addr: fe80::a00:27ff:fea6:133a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22666 (22.6 KB)  TX bytes:10386 (10.3 KB)
          Interrupt:16 Base address:0xd060 
```

I have looked in the logs for any error related to eth1 but only found :
```
Jan  4 05:42:35 redmine kernel: [   10.590540] pcnet32: eth1: registered as PCnet/FAST III 79C973
Jan  4 05:42:35 redmine kernel: [   12.249245] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan  4 05:42:36 redmine kernel: [   12.571919] pcnet32 0000:00:08.0: eth1: link up, 100Mbps, full-duplex
```

I don't know what I am missing at this point, any help would be greatly appreciated. Sorry for the lengthy post but I'm trying to get as much information upfront.

---

