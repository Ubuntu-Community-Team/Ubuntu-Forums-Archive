---
title: "Is IP_ADVANCED_ROUTER enable in Ubuntu Server kernel image?"
date: 2007-01-17
forum: Server Platforms
---

### Post by deejaylinux on 2007-01-17
Hi forum,

My question is about routing in Ubuntu Server, I sent the same question to network&wireless forum but maybe it's better ask for here.

I like to set up my Ubuntu Server box acting as a router. The machine has two interfaces:

eth0 - wired card connected to 192.168.2.0 network.
eth1 - wireless card connected to 192.168.1.0 network, which has access to the Internet through 192.168.1.1 gateway.

The only think I want to do is redirect all traffic from eth0 to eth1. No filter. No NAT. Only routing.

I set 1 in the file /proc/sys/net/ipv4/ip_forward, but still it is not working. The route table is this:

192.168.2.0/24 dev eth0 proto kernel scope link src 192.168.2.1
192.168.1.0/24 dev eth1 proto kernel scope link src 192.168.1.3
default via 192.168.1.1 dev eth1

All help would be appreciated.

Thanks in advanced and regards

---

### Post by technodigifreak on 2007-01-17
> **deejaylinux said:**
> Hi forum,

My question is about routing in Ubuntu Server, I sent the same question to network&wireless forum but maybe it's better ask for here.

I like to set up my Ubuntu Server box acting as a router. The machine has two interfaces:

eth0 - wired card connected to 192.168.2.0 network.
eth1 - wireless card connected to 192.168.1.0 network, which has access to the Internet through 192.168.1.1 gateway.

The only think I want to do is redirect all traffic from eth0 to eth1. No filter. No NAT. Only routing.

I set 1 in the file /proc/sys/net/ipv4/ip_forward, but still it is not working. The route table is this:

192.168.2.0/24 dev eth0 proto kernel scope link src 192.168.2.1
192.168.1.0/24 dev eth1 proto kernel scope link src 192.168.1.3
default via 192.168.1.1 dev eth1

All help would be appreciated.

Thanks in advanced and regards



With IP forwarding enabled it should forward traffic from one interface to the other without issue.  I'm assuming that you are basically going to be using this as a wireless brouter (bridging router) given the description you gave.  It would be nice to see your /etc/network/interfaces file and also the output returned by 'ifconfig -a'.  Also, are you running any other services on this machine?  Have you told the machines on the 192.168.2.0 network that this machine will be their default gateway?  Does 192.168.1.1 know that all traffic on the 192.168.2.0 network will need to be routed through 192.168.1.3?  How are the machines on these networks being assigned addresses?  Are they all statically set or do you have a DHCP server for each network? What errors are returned when you try pinging 192.168.1.1 from any machine (besides the brouter) on the 192.168.2.0 network?



Let me know if this was helpful.

---

### Post by deejaylinux on 2007-01-18
Exactly, that is what I want! First I tried setting the box as a bridge, but it didn't work.

I was reading some information about bridging, and there is a lot of problems doing bridging with wireless cards.

Then the next step was to configure my box as a router, so the wireless card will be connected to a network, and the wired card will be connected to another network. Now I write the information you ask for in your post:

/etc/network/interfaces 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The wired network interface
auto eth0
iface eth0 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        network 192.168.2.0

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid proteus
        wireless-key1 <my wep key>
        wireless-ap 00:60:b3:af:6c:74
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 80.58.0.33

and now the ifconfig -a output:

eth0      Link encap:Ethernet  HWaddr 00:40:63:D7:E6:48
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:63ff:fed7:e648/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:55269 (53.9 KiB)  TX bytes:125326 (122.3 KiB)
          Interrupt:11 Base address:0xec00

eth1      Link encap:Ethernet  HWaddr 00:11:50:35:F0:29
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe35:f029/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:587536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:786127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:212970638 (203.1 MiB)  TX bytes:800010059 (762.9 MiB)
          Interrupt:10 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4279 (4.1 KiB)  TX bytes:4279 (4.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[B][I]
Does 192.168.1.1 know that all traffic on the 192.168.2.0 network will need to be routed through 192.168.1.3?[/I][/B]
Really no! Just this is the problem, it's sure!!! I have to insert an entry in my ADSL router to return packets from 192.168.2.0 network... what a newbie fail!!!

Thanks, just now I can't check this but this afternoon I'll try

Regards

---

### Post by technodigifreak on 2007-01-18
Your interfaces file looks good, And your output from ifconfig looks good.  Most dsl routers give you an option of specifying additional routes so therein may be the fix.  Let us know what you find out!

---

