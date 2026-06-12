---
title: "Ubuntu Server 12.04LTS 64bit Networking + Openstack Configuration"
date: 2013-02-21
forum: Server Platforms
---

### Post by rgranados80 on 2013-02-21
Greetings Forum Members

I am in the process of learning about Cloud Computing and Openstack as the platform. The documentation I'm following is available from Openstack at the link below.
[http://docs.openstack.org/folsom/basic-install/content/](http://docs.openstack.org/folsom/basic-install/content/)

The document has been very helpful in the initial setup and configuration of the servers I'm deploying (this is being done with virtual machines hosted on ESXi servers).

I believe I've come across either an issue with my limited experience of networking in linux or the documentation not providing more information on Openstack.


Issue:

[HTML]

3 Systems configured to communicate with each other

		controller-host		network-host	compute-host

Names		folsom-controller	folsom-network	folsom-compute

External	10.54.36.26/23		10.54.36.27/23	10.54.36.28/23
+ API Network

Management	192.168.0.1/24		192.168.0.2/24	192.168.0.3/24
 Network

Data					10.10.10.1/24	10.10.10.2/24
 Network

Number of		2			3		2
 NIC's



[/HTML]

I'm not familiar with routing or iptables but I'm having some issues in having the management network communicate and I believe that is because of the directions that exist for the openstack documentation. The public network I'm utilizing for the "external + API" network is a routed network that has a gateway and DNS server,  but my private network is connected to a dumb switch with no other infrastructure at all.

I've provided an excerpt of the configuration of the networks on both systems below.

[HTML]

root@folsom-controller:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.54.36.1      0.0.0.0         UG    100    0        0 eth1
10.54.36.0      *               255.255.254.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
root@folsom-controller:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
nova-api-INPUT  all  --  anywhere             anywhere
ACCEPT     gre  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
nova-filter-top  all  --  anywhere             anywhere
nova-api-FORWARD  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
nova-filter-top  all  --  anywhere             anywhere
nova-api-OUTPUT  all  --  anywhere             anywhere

Chain nova-api-FORWARD (1 references)
target     prot opt source               destination

Chain nova-api-INPUT (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             folsom-controller.openstack  tcp dpt:8775

Chain nova-api-OUTPUT (1 references)
target     prot opt source               destination

Chain nova-api-local (1 references)
target     prot opt source               destination

Chain nova-filter-top (2 references)
target     prot opt source               destination
nova-api-local  all  --  anywhere             anywhere
root@folsom-controller:~# ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable


[/HTML]


[HTML]

root@folsom-network:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.54.36.1      0.0.0.0         UG    100    0        0 eth2
10.10.10.0      *               255.255.255.0   U     0      0        0 eth1
10.54.36.0      *               255.255.254.0   U     0      0        0 eth2
localnet        *               255.255.255.0   U     0      0        0 eth0
root@folsom-network:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@folsom-network:~#
root@folsom-network:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable


[/HTML]



I'm wondering if there is no gateway device or DNS server -- does there need to be some manual configuration on the hosts to allow for them to communicate? I think there is because any attempt to ping 192.168.0.0/24 is going to go through my "external + API" network gateway fails because that isn't a known network to my DNS servers.

What am I doing wrong? Or is the documentation on openstack a little skimpy because they assume you should have the infrastructure or the knowledge?

Any help would be greatly appreciated! :D

---

### Post by TheFu on 2013-02-21
Probably not any help, but .... 

I'm not an openstack expert and haven't ever tried to install it, but I have been to a few meetups and talked with some large scale O-S deployments.  I was under the impression that openstack had to be loaded onto the real hardware, not inside VMs.  It provides the VM environment using KVM.  KVM is not compatible with ESX or ESXi.  Only 1 hypervisor can be loaded at a time on the physical hardware.  That means your "compute" nodes cannot be inside a VM of any sort.

That doesn't mean you can't create a KVM VM, then an LXC containter or 20 inside a VM under KVM, just that only 1 main hypervisor can run on the hardware.

I think the management workstation can run inside an O-S VM, after everything is configured.

O-S is really complex and intended for locations with hundreds to tens of thousands of physical machines.  For locations with less than 50 physical machines, there are better, easier alternatives, IMHO.  

The complexity of O-S is just too great.  Each peice - and there are a bunch of moving parts - are really separate and difficult all alone to get working.

Did you start out by using the all-in-one development O-S install? I've been told that this should get you up and familiar with the ideas and how things interact.

Sorry that I'm not any help.

---

### Post by rgranados80 on 2013-02-22
Hello all.

I have gone and done some due diligence and started reading more about networking to help myself out.

I started on a website that had some very blunt statements about what to do and what not do when networking. The points I took from it is to be very careful when configuring multiple NIC's on a system so that troubleshooting of routing isn't a nightmare later on.

[http://www.ni.com/white-paper/12558/en#toc2](http://www.ni.com/white-paper/12558/en#toc2)


Then I did the rest of my surfing on wikipidea on the subject of subnetting and subnet masks. When I was in school the concept was complicated and I can say that is still as daunting as it was back then! ;)

I luckily did take something away from it yesterday that I didn't back in school, so at least some of the advice my professor was giving me finally sank in.

The documentation that was provided on the openstack "How-To" didn't really give lay down the best configuration recommendations as there was a possibility of routing issues like the ones I experienced. After following the principles laid down in the links below - everything worked the way I wanted.

[http://en.wikipedia.org/wiki/Subnetwork#IPv4_subnetting](http://en.wikipedia.org/wiki/Subnetwork#IPv4_subnetting)
[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)


I'll be making a recommendation to the folks that wrote the "How-To" at openstack, and maybe they'll take it, maybe they won't. At least I hope to be able to help others with networking issues. :)


[HTML]
rfiorenzano@folsom-controller:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:56:85:58:05
          inet addr:192.168.0.1  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:56ff:fe85:5805/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15073 (15.0 KB)  TX bytes:14489 (14.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:56:85:58:06
          inet addr:10.54.37.26  Bcast:10.54.37.255  Mask:255.255.254.0
          inet6 addr: fe80::250:56ff:fe85:5806/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4259650 (4.2 MB)  TX bytes:40327 (40.3 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26349680 (26.3 MB)  TX bytes:26349680 (26.3 MB)

rfiorenzano@folsom-controller:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.54.36.1      0.0.0.0         UG    100    0        0 eth1
10.54.36.0      *               255.255.254.0   U     0      0        0 eth1
192.168.0.0     *               255.255.0.0     U     0      0        0 eth0
rfiorenzano@folsom-controller:~$ ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_req=1 ttl=64 time=0.283 ms
64 bytes from 192.168.0.2: icmp_req=2 ttl=64 time=0.174 ms
64 bytes from 192.168.0.2: icmp_req=3 ttl=64 time=0.206 ms
^C
--- 192.168.0.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.174/0.221/0.283/0.045 ms
rfiorenzano@folsom-controller:~$
[/HTML]


[HTML]
root@folsom-network:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:56:85:58:15
          inet addr:192.168.0.2  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:56ff:fe85:5815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15563 (15.5 KB)  TX bytes:14689 (14.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:50:56:85:58:16
          inet addr:172.16.0.1  Bcast:172.31.255.255  Mask:255.240.0.0
          inet6 addr: fe80::250:56ff:fe85:5816/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:180 (180.0 B)  TX bytes:468 (468.0 B)

eth2      Link encap:Ethernet  HWaddr 00:50:56:85:58:17
          inet addr:10.54.37.27  Bcast:10.54.37.255  Mask:255.255.254.0
          inet6 addr: fe80::250:56ff:fe85:5817/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:75830292 (75.8 MB)  TX bytes:2437883 (2.4 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

root@folsom-network:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.54.36.1      0.0.0.0         UG    100    0        0 eth2
10.54.36.0      *               255.255.254.0   U     0      0        0 eth2
172.16.0.0      *               255.240.0.0     U     0      0        0 eth1
localnet        *               255.255.0.0     U     0      0        0 eth0
root@folsom-network:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=0.205 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.56 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=0.164 ms
^C
--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.164/0.643/1.560/0.648 ms
root@folsom-network:~#
[/HTML]

---

