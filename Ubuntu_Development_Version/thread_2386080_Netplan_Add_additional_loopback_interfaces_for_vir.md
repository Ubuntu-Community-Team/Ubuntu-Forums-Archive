---
title: "Netplan: Add additional loopback interfaces for virtual networks."
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by nbritton on 2018-02-28
Hello,

I'm virtualizing Mirantis Cloud Platform (OpenStack) on a single test node running Ubuntu 18.04 as the hypervisor. I need to create three separate virtual (loopback) networks (Deployment, Management, and Tenant) for the virtual machines. I will have one VM with four network interfaces (Internet, Deployment, Management, and Tenant) that will be running ClearOS for edge routing (and OpenVPN) between the real and virtual networks. How do you configure all of this with netplan? Below is the configuration:

Physical devices: Dell quad port rNDC (two 10GbE and two 1GbE port)
10GbE: br0 --> bond0 --> ens1 / ens2 (presently unconnected)
1GbE: br1 --> bond1 -- ens3 / ens4 (plugged into the Internet) 

Networks:
br0: unconnected
Internet (br1): VLAN 1, 192.168.1.2/24 (Internet)
Deployment Network (br2): VLAN 1, 10.0.0.2/24 (MaaS PXE Bootp / DHCP server will be running on this network)
Management Network (br3): VLAN 10, 10.0.1.2/24 (Openstack control plane network)
Tenant Network (br4): VLAN 20, 10.0.2.2/24 (Public network)

ClearOS router / gateway:
10.0.0.1 (br2/VLAN1), 10.0.1.1 (br3/VLAN10), 10.0.2.1 (br4/VLAN20).

---

### Post by nbritton on 2018-03-02
So apparently you don't need a loopback, dummy, or tap interface. netplan will happily create a floating bridge with no interfaces attached to it by using a null value [] in the interfaces section. It hangs for a few minutes at boot, but otherwise everything works as anticipated. Below is my netplan configuration file:

```

network:
  version: 2
  renderer: networkd

  ethernets:
    eno3:
      dhcp4: no
    eno4:
      dhcp4: no

  vlans:
    br3-vlan10:
      id: 10
      link: br3
      addresses: [10.0.1.2/24]
    br4-vlan20:
      id: 20
      link: br4
      addresses: [10.0.2.2/24]

  bonds:
    bond1:
      interfaces: [eno3, eno4]
      #parameters:
      #  mode: 802.3ad

  bridges:
    br1:
      interfaces: [bond1]
      dhcp4: no
      addresses: [192.168.1.186/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [192.168.1.1]
    br2:
      interfaces: []
      addresses: [10.0.0.2/24]
    br3:
      interfaces: []
    br4:
      interfaces: []

```

Here is ifconfig output:

```

bond1: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
        ether ae:b7:d6:20:2a:fb  txqueuelen 1000  (Ethernet)
        RX packets 10271  bytes 1113826 (1.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 704  bytes 111391 (111.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.186  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::b85a:acff:fec6:b06a  prefixlen 64  scopeid 0x20<link>
        inet6 2605:6000:101e:4260:b85a:acff:fec6:b06a  prefixlen 64  scopeid 0x0<global>
        ether ba:5a:ac:c6:b0:6a  txqueuelen 1000  (Ethernet)
        RX packets 2728  bytes 495517 (495.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 618  bytes 103785 (103.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.2  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::e01e:cff:fe62:c75d  prefixlen 64  scopeid 0x20<link>
        ether e2:1e:0c:62:c7:5d  txqueuelen 1000  (Ethernet)
        RX packets 19  bytes 1012 (1.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18  bytes 1384 (1.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::8822:95ff:fe39:2543  prefixlen 64  scopeid 0x20<link>
        ether 8a:22:95:39:25:43  txqueuelen 1000  (Ethernet)
        RX packets 27  bytes 1548 (1.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 31  bytes 2390 (2.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::ecb6:a3ff:fe59:e00c  prefixlen 64  scopeid 0x20<link>
        ether ee:b6:a3:59:e0:0c  txqueuelen 1000  (Ethernet)
        RX packets 27  bytes 1548 (1.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 31  bytes 2390 (2.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br3-vlan10: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.1.2  netmask 255.255.255.0  broadcast 10.0.1.255
        inet6 fe80::8822:95ff:fe39:2543  prefixlen 64  scopeid 0x20<link>
        ether 8a:22:95:39:25:43  txqueuelen 1000  (Ethernet)
        RX packets 19  bytes 1012 (1.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18  bytes 1384 (1.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


br4-vlan20: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.2  netmask 255.255.255.0  broadcast 10.0.2.255
        inet6 fe80::ecb6:a3ff:fe59:e00c  prefixlen 64  scopeid 0x20<link>
        ether ee:b6:a3:59:e0:0c  txqueuelen 1000  (Ethernet)
        RX packets 19  bytes 1012 (1.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18  bytes 1384 (1.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eno3: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether ae:b7:d6:20:2a:fb  txqueuelen 1000  (Ethernet)
        RX packets 8831  bytes 831112 (831.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 352  bytes 54651 (54.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 250  memory 0xdb000000-db7fffff


eno4: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether ae:b7:d6:20:2a:fb  txqueuelen 1000  (Ethernet)
        RX packets 1440  bytes 282714 (282.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 352  bytes 56740 (56.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 15  memory 0xdc000000-dc7fffff


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 20  bytes 1816 (1.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20  bytes 1816 (1.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:df:38:68  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:feed:9972  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:ed:99:72  txqueuelen 1000  (Ethernet)
        RX packets 87  bytes 4984 (4.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7211  bytes 762165 (762.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:fe3e:49a6  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:3e:49:a6  txqueuelen 1000  (Ethernet)
        RX packets 19  bytes 1278 (1.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 31  bytes 2390 (2.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:fea4:f3a7  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:a4:f3:a7  txqueuelen 1000  (Ethernet)
        RX packets 27  bytes 2002 (2.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 44  bytes 3468 (3.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vnet3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:feed:dbc6  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:ed:db:c6  txqueuelen 1000  (Ethernet)
        RX packets 27  bytes 2002 (2.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 44  bytes 3468 (3.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Here is ping output to show that it works (10.0.0.1 is on vlan1, 10.0.1.1 is on vlan10, and 10.0.2.1 is on vlan20):
```

root@lab:~# ping 10.0.0.1 -c 3
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=0.893 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.312 ms
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=0.349 ms


--- 10.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2024ms
rtt min/avg/max/mdev = 0.312/0.518/0.893/0.265 ms
root@lab:~# ping 10.0.1.1 -c 3
PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
64 bytes from 10.0.1.1: icmp_seq=1 ttl=64 time=1.22 ms
64 bytes from 10.0.1.1: icmp_seq=2 ttl=64 time=0.577 ms
64 bytes from 10.0.1.1: icmp_seq=3 ttl=64 time=0.292 ms


--- 10.0.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 0.292/0.697/1.224/0.391 ms
root@lab:~# ping 10.0.2.1 -c 3
PING 10.0.2.1 (10.0.2.1) 56(84) bytes of data.
64 bytes from 10.0.2.1: icmp_seq=1 ttl=64 time=0.739 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=64 time=0.339 ms
64 bytes from 10.0.2.1: icmp_seq=3 ttl=64 time=0.222 ms


--- 10.0.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2029ms
rtt min/avg/max/mdev = 0.222/0.433/0.739/0.222 ms

```

---

### Post by daxtens on 2018-05-17
[edit: removed all my probably-wrong info]

---

### Post by cariboo on 2018-05-17
Thread closed, as Bionic has been released

---

