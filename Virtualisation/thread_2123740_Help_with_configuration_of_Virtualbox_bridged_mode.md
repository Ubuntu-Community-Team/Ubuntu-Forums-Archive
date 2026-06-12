---
title: "Help with configuration of Virtualbox bridged mode"
date: 2013-03-08
forum: Virtualisation
---

### Post by ATW72 on 2013-03-08
Hi,

I currently am running Ubuntu 12.10 server and I have install Virtualbox Headless.  Within Virtualbox, I am running Centos as a guest OS.  I'm finding that if I run in Nat mode, I am able to connect out to the internet, but I actually need to run in bridged mode as I need my internal network to be able to access the guest.  I am able to ping the guest from the host and ping the host from the guest in bridged mode, but I am not able to ping anything beyond the host.  I am wondering if I am missing something and some help would be very much appreciated.

Anthony

---

### Post by TheFu on 2013-03-08
Try network troubleshooting 101.
Use IP addresses for everything - including pinging internet locations.
Could it be that DNS isn't setup on the client?

---

### Post by ATW72 on 2013-03-08
Thanks for the reply.  When troubleshooting, I am pinging other devices  by ip address.  Like I said, I'm able to ping my host ip address, but  nothing else in my network.

Anthony

---

### Post by SeijiSensei on 2013-03-08
In bridged mode both the host and guest should have addresses in the same subnet as the rest of your network.  If you have a DHCP server somewhere to handle address assignments, that should have been set up correctly to begin with.

What is the IP address and subnet mask for the host and guest?  Can you show us the guest's routing table with "route -n"?

One alternative to bridged mode is to use NAT, then run iptables on the host and have it forward specific ports back to the guest.

---

### Post by ATW72 on 2013-03-08
Both the host and the guest are on the same network (192.168.2.0).  They are also both configured with static ip's.

Here is the output of the route -n on the guest:

root@pbx:~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1002   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0



Here is the output of the Host ifconfig -a:

atwillia@cits-server:/etc/network$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 8c:89:a5:32:e1:6f  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fe32:e16f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5287045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8164303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1512845294 (1.5 GB)  TX bytes:8909747827 (8.9 GB)
          Interrupt:42 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:11:0a:57:bc:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:11:0a:57:bc:33  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:377717 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1719781209 (1.7 GB)  TX bytes:1719781209 (1.7 GB)


I have 3 NIC cards but I'm only using one.


Also here is the output of my guest ifconfig -a:

root@pbx:~ $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:5A:64:9A  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe5a:649a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225299 (220.0 KiB)  TX bytes:84285 (82.3 KiB)
          Interrupt:10 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:221385 (216.1 KiB)  TX bytes:221385 (216.1 KiB)



Anthony

---

### Post by TheFu on 2013-03-09
What is the routing table on the client?

Are you positive that the VM is connected to the correct NIC on the hostOS settings? I had to ask. I've accidentally selected the wrong NIC in the VM settings myself.

---

### Post by ATW72 on 2013-03-09
> **TheFu said:**
> What is the routing table on the client?

Are you positive that the VM is connected to the correct NIC on the hostOS settings? I had to ask. I've accidentally selected the wrong NIC in the VM settings myself.

Yes I am positive I'm bridged to eth0.

---

### Post by TheFu on 2013-03-09
> **ATW72 said:**
> Yes I am positive I'm bridged to eth0.

What is the routing table on the client?

---

### Post by ATW72 on 2013-03-09
> **TheFu said:**
> What is the routing table on the client?


root@pbx:~ $ route -n
Kernel IP routing table
Destination        Gateway              Genmask          Flags      Metric   Ref      Use   Iface
192.168.2.0        0.0.0.0       255.255.255.0         U                 0              0              0       eth0
169.254.0.0        0.0.0.0               255.255.0.0          U               1002        0       0       eth0
0.0.0.0                 192.168.2.1      0.0.0.0                        UG              0               0              0       eth0

---

### Post by SeijiSensei on 2013-03-09
And yet you cannot ping 192.168.2.1 from the guest but you can from the host?  Just want to make sure.  You don't have any iptables rules on either the host or guest, too, yes?

---

### Post by TheFu on 2013-03-09
> **ATW72 said:**
> root@pbx:~ $ route -n
Kernel IP routing table
Destination        Gateway              Genmask          Flags      Metric   Ref      Use   Iface
192.168.2.0        0.0.0.0       255.255.255.0         U                 0              0              0       eth0
169.254.0.0        0.0.0.0               255.255.0.0          U               1002        0       0       eth0
0.0.0.0                 192.168.2.1      0.0.0.0                        UG              0               0              0       eth0

The only thing that I see different from my setups is that the metric for the gateway is not higher than the metric for the LANs.

Also, it would be helpful if you wrapped column data in a code-not-code so we can more easily read the results.
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         rt1             0.0.0.0         UG    100    0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

```
See how much easier this is to read?
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 virbr1
172.20.1.0      0.0.0.0         255.255.255.0   U     0      0        0 bus0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 or0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         192.168.1.1     0.0.0.0         UG    1      0        0 or0
0.0.0.0         172.20.1.1      0.0.0.0         UG    100    0        0 bus0

```
And this?

---

### Post by ATW72 on 2013-03-09
> **SeijiSensei said:**
> And yet you cannot ping 192.168.2.1 from the guest but you can from the host?  Just want to make sure.  You don't have any iptables rules on either the host or guest, too, yes?

Yes, I'm unable to ping the gateway from the guest.  I can ping the gateway from the host though.

Anthony

---

