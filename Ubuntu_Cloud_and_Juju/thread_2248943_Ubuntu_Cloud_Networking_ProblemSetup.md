---
title: "Ubuntu Cloud Networking Problem/Setup"
date: 2014-10-18
forum: Ubuntu Cloud and Juju
---

### Post by ccrypto on 2014-10-18
I am running Ubuntu 14.04.1 and just completed an Ubuntu Cloud install.   The install is on bare metal and I chose an "single machine install" for the Openstack/Cloud installation.   Everything seems to have completed successfully but I am a bit confused on the networking setup.

When I go to "cloud-status" everything is indicated as "started" but it seems to have created a different subnet for all of the Openstack components.  On the bare metal machine I have a single ethernet interface configured on 10.87.9.182/24.   However the Openstack installation created a new subnet on 10.0.3.0/24 with all of the Openstack services on that subnet.   I tried changing a client machine (on eth0) to be on the 10.0.3.0/24 subnet but it can't reach any of the Openstack components.   

I have included the output of ifconfig below.   Can someone advise as to how I can access lxcbr0 from the eth0 subnet?   I am guessing that I have to bridge these two together but if someone can let me know the recommended method it would be appreciated.   Goal is a single node "all in one".    The server does have multiple physical ethernet interfaces so if it is advisable to map lxcbr0 to eth1 for example I could do that as well.

Second question, is there anyway to tell "cloud-install" to use ip addresses on the eth0 subnet prior to Openstack installation?    Thanks.  I appreciate any assistance.

```
[FONT=courier new]eth0      Link encap:Ethernet  HWaddr f8:72:ea:f6:ff:c0[/FONT]
[FONT=courier new]          inet addr:10.87.9.182  Bcast:10.87.9.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::fa72:eaff:fef6:ffc0/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:1173322 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:576490 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000[/FONT]
[FONT=courier new]          RX bytes:1520098962 (1.5 GB)  TX bytes:35619827 (35.6 MB)[/FONT]
[FONT=courier new]          Memory:def00000-df000000[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lo        Link encap:Local Loopback[/FONT]
[FONT=courier new]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=courier new]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=courier new]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=courier new]          RX packets:1064182 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:1064182 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0[/FONT]
[FONT=courier new]          RX bytes:386756658 (386.7 MB)  TX bytes:386756658 (386.7 MB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lxcbr0    Link encap:Ethernet  HWaddr fe:54:00:b1:71:be[/FONT]
[FONT=courier new]          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::e426:4bff:fe95:4fb2/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:578489 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:748672 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0[/FONT]
[FONT=courier new]          RX bytes:39118717 (39.1 MB)  TX bytes:1221970831 (1.2 GB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]virbr0    Link encap:Ethernet  HWaddr 02:54:42:55:24:83[/FONT]
[FONT=courier new]          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0[/FONT]
[FONT=courier new]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]vnet0     Link encap:Ethernet  HWaddr fe:54:00:b6:b6:71[/FONT]
[FONT=courier new]          inet6 addr: fe80::fc54:ff:feb6:b671/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:551131 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:762964 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:500[/FONT]
[FONT=courier new]          RX bytes:45782048 (45.7 MB)  TX bytes:1022833310 (1.0 GB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]vnet1     Link encap:Ethernet  HWaddr fe:54:00:b1:71:be[/FONT]
[FONT=courier new]          inet6 addr: fe80::fc54:ff:feb1:71be/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:84638 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:85411 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:500[/FONT]
[FONT=courier new]          RX bytes:10370435 (10.3 MB)  TX bytes:119730069 (119.7 MB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]vnet2     Link encap:Ethernet  HWaddr fe:54:00:ee:da:b6[/FONT]
[FONT=courier new]          inet6 addr: fe80::fc54:ff:feee:dab6/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:148204 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:115134 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:500[/FONT]
[FONT=courier new]          RX bytes:24307081 (24.3 MB)  TX bytes:113075749 (113.0 MB)  [/FONT]

```

---

### Post by bmullan2 on 2014-10-26
the 10.0.3.x network is for the openstack "services" that are running in LXC containers instead of the usual hw virtualization machines (VMs).. better performance, resource utilization etc.
There are several good blogs on LXC networking.   

If you ignore the references to vagrant (just because its not pertinent to the networking question) this one describes various networking use-cases such as VETH which I think is what you are looking for etc:

[http://containerops.org/2013/11/19/lxc-networking/](http://containerops.org/2013/11/19/lxc-networking/)

---

