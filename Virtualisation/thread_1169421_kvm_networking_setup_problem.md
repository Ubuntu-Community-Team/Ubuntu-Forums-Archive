---
title: "kvm networking setup problem"
date: 2009-05-25
forum: Virtualisation
---

### Post by mark thomas1 on 2009-05-25
I have  a server with two ethernet cards: eth0 (internet) and eth1 (LAN, 192.168.x.x). I'd like my guest vm to be accessible over the lan, eg at 192.168.1.2

I set the guest to use 192.168.1.2 as the IP with 192.168.1.1 as the gateway, but after starting it I don't get a ping and can't ssh in (I used "--addpkg vim openssh-server"  for ubuntu-vm-builder to add ssh). I'm thinking there's something wrong with my network setup, but I can't see what.

Here's my /etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address x.x.x.x
        netmask x.x.x.x
        network x.x.x.x
        broadcast x.x.x.x
        gateway x.x.x.x
        dns-nameservers x.x.x.x

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet static

        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        bridge_ports eth1
        bridge_stp off
        bridge_maxwait 5

```After restarting the network, this is the output of ifconfig:

```
br0       Link encap:Ethernet  HWaddr 00:22:19:b7:83:8a
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:feb7:838a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:398 (398.0 B)

eth0      Link encap:Ethernet  HWaddr 00:22:19:b7:83:88
          inet addr:x.x.x.x Bcast:195.159.134.223  Mask:255.255.255.224
          inet6 addr: fe80::222:19ff:feb7:8388/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3526 (3.5 KB)  TX bytes:5316 (5.3 KB)
          Interrupt:16 Memory:f8000000-f8012700

eth1      Link encap:Ethernet  HWaddr 00:22:19:b7:83:8a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f4000000-f4012700

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2336 (2.3 KB)  TX bytes:2336 (2.3 KB)

virbr0    Link encap:Ethernet  HWaddr d2:42:67:45:09:2c
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::8c4a:66ff:fe8a:50a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1488 (1.4 KB)  TX bytes:468 (468.0 B)

vnet0     Link encap:Ethernet  HWaddr d2:42:67:45:09:2c
          inet6 addr: fe80::d042:67ff:fe45:92c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:1908 (1.9 KB)  TX bytes:12688 (12.6 KB)

```Any help please?

---

### Post by veloce on 2009-05-25
How have you set up your vm virtual nic?  I think by default it expects the bridge to be vibr0 and you need to tell it to use br0.

I'm using virt-manager and there's a nice drop down box with all the virtual networks to choose from and one of the options is "br0 eth0".

---

