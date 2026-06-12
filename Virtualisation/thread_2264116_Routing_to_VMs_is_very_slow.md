---
title: "Routing to VMs is very slow"
date: 2015-02-05
forum: Virtualisation
---

### Post by topler on 2015-02-05
**Problem:**

The connection to guest VMs from the host network, apart form the KVM host itself, is painfully slow.
It's only 65 KBits and it also appears to jam the network, as it seems to drop lots of packages.

[B]Details:

[/B][IMG]https://s3-eu-west-1.amazonaws.com/quickupload/KVMNetwork.jpg[/IMG]



[LIST]
[*]Ubuntu 14.04.1
[*]KVM/ QEMU
[*]The pysical network is a Gigabit Ethernet
[*]The guest VMs are connected to virtual networks with the modus "Route".
[*]My home office intranet (10.100.200.0/24) has the DD-WRT router as gateway configured. Within this intranet I have got a Linux machine which runs KVM/ QEMU. This machine has a virtual network (10.11.12.0/24) to which all its guest VMs are connected to.
[*]The KVM host machine has the IP 10.100.200.10.
[*]To make the VM guests discoverable, I added a static route to the dd-wrt router (Setup > Advanced Routing) with the settings below.
[/LIST]

```
Destination LAN NET: 10.11.12.0 
Subnet Mask: 255.255.255.0 
Gateway: 10.100.200.10 
Interface: LAN & WLAN

```

The routing table on the 10.100.200.10 machine (KVM host) is below. 

```
$ ip route show 
default via 10.100.200.1 dev em1 
10.11.12.0/24 dev virbr1  proto kernel  scope link  src 10.11.12.1 
10.100.200.0/21 dev em1  proto kernel  scope link  src 10.100.200.10

```

Machines from within 10.100.200.0/24 network can now discover and connect to the VMs in the 10.11.12.0/24 network. 

However the connection speed is very slow (about 65 KBits), when a machine from within the 10.100.200.10/24 network initiates the connection and sends data to the VM (10.11.12.20). The problem might also be of existence for the opposite direction but haven't been able to test this yet. 
When I do a ping from within the 10.100.200.0/24 network to the NIC 10.11.12.20, I get the "Redirect Host(New nexthop: 10.100.200.10)" message. 

```
$ ping 10.11.12.20 
PING 10.11.12.20 (10.11.12.20) 56(84) bytes of data. 
64 bytes from 10.11.12.20: icmp_seq=1 ttl=63 time=13.5 ms 
From 10.145.24.1: icmp_seq=2 Redirect Host(New nexthop: 10.100.200.10) 
64 bytes from 10.11.12.20: icmp_seq=2 ttl=63 time=13.5 ms 
From 10.145.24.1: icmp_seq=3 Redirect Host(New nexthop: 10.100.200.10) 
64 bytes from 10.11.12.20: icmp_seq=3 ttl=63 time=13.6 ms 
From 10.145.24.1: icmp_seq=4 Redirect Host(New nexthop: 10.100.200.10) 
64 bytes from 10.11.12.20: icmp_seq=4 ttl=63 time=13.5 ms 
From 10.145.24.1: icmp_seq=5 Redirect Host(New nexthop: 10.100.200.10) 
64 bytes from 10.11.12.20: icmp_seq=5 ttl=63 time=13.5 ms

```

I run traceroute from my laptop and it appears that it routes to the expected IPs but shows where the deplays are introduced. 
Sometimes it also times out (it displays a * rather than the timings). 

Traceroute when it didn't time out: 

```
$ traceroute 10.11.12.20 
traceroute to 10.11.12.20 (10.11.12.20), 30 hops max, 60 byte packets 
 1  10.100.200.1 (10.100.200.1)  0.387 ms  0.706 ms  0.796 ms 
 2  10.100.200.10 (10.100.200.10)  13.411 ms  25.857 ms  38.277 ms 
 3  10.11.12.20 (10.11.12.20)  50.970 ms  63.466 ms  75.893 ms

```

Traceroute when it timed out: 

```
$ traceroute 10.11.12.20 
traceroute to 10.11.12.20 (10.11.12.20), 30 hops max, 60 byte packets 
1 10.100.200.1 (10.100.200.1) 0.359 ms 0.640 ms 0.799 ms 
2 10.100.200.10 (10.100.200.10) 13.656 ms 26.051 ms 38.410 ms 
3 10.11.12.20 (10.11.12.20) 51.140 ms 63.482 ms * 

```

**Question: **
As far as I can see, I guess that the dd-wrt router is configured correctly but the KVM host (IP 10.100.200.10) requires some tweaking. 
Is there a way of making iptables and route changes on the KVM host (IP 10.100.200.10) to address this problem?

**Note:**
I am aware of the approach of bridging the NIC and then use the bridge directly with KVM but then I would be bound to use the network within which the KVM host resides in. Network separation is required!

Thanks for your help!

---

### Post by topler on 2015-02-05
I made a drawing to make it easier for you to picture the infrastructure. Hopefully it will get someone of you looking into it. :)

---

### Post by TheFu on 2015-02-05
I discovered years ago that the built-in networking created by virsh/libvirt sucks.  Don't know why, just that it does.

Manually setup any bridges you need through the /etc/network/interfaces file on the host and everything will run at 90%+ of native bandwidth.

Of course, if you are running a 10Gig network, then you'll want to use openvswitch to get that extra 10% performance.

I generally assign a different physical interface to each bridge, don't give the hostOS any networking on that interface, but you can do whatever you like.

[http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM) has more details on why you want to use normal Linux bridges for networking.

---

