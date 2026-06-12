---
title: "server kvm routing for internal network"
date: 2012-12-14
forum: Virtualisation
---

### Post by nwalkey on 2012-12-14
I'm trying to set up a server so that we have all our actual server  functions operating from within KVM virtual machines. The physical  machine we have is a 2 processor AMD opteron box with 2 ethernet  interfaces. I've installed ubuntu server 12.04, kvm, libvirt,  virt-machine manager and all that I needed to to get the virtual  machines running. Everything is good we've got our virtual machine  running with SMEserver and it connects to the internet via a nat  interface. Our problems start when we try to set it up so that SMEserver  acts as a gateway and dhcp server for the private network. Currently  all I want is to get the computers to connect to the internet through  SMEserver. With an ubuntu desktop VM setup to use the same adapter as  SMEserver, the desktop gets supplied with an IP from SMEserver and can  connect to google.ca. Our configuration is a s follows:

My /etc/network/interfaces file looks like this:

auto eth0
iface eth0 inet static
        address 184.70.141.82
        netmask 255.255.255.252
        gateway 184.70.141.81

auto eth1
iface eth1 inet static
        address 10.10.10.3
        netmask 255.255.255.0
        gateway 10.10.10.1

and virtual interfaces (from ifconfig):

virbr2    Link encap:Ethernet  HWaddr 52:54:00:1e:a0:4b  
          inet addr:10.10.12.1  Bcast:10.10.12.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1787316 (1.7 MB)  TX bytes:2168953 (2.1 MB)

virbr3    Link encap:Ethernet  HWaddr 52:54:00:bd:0c:b1  
          inet addr:10.10.10.1  Bcast:10.10.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:ef:46:a5  
          inet6 addr: fe80::fc54:ff:feef:46a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1852301 (1.8 MB)  TX bytes:1975491 (1.9 MB)

vnet1     Link encap:Ethernet  HWaddr fe:54:00:1b:b0:59  
          inet6 addr: fe80::fc54:ff:fe1b:b059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:20125 (20.1 KB)  TX bytes:108114 (108.1 KB)

SMEserver  uses virbr2/vnet1 to connect to the external network via NAT with dhcp  and virbr3/vnet0 to as the network adapter that would hopefully be  bridged to eth1. 
As I said already, SMEserver will supply internet  to the ubuntu VM using the same adapter but I cannot get it to bridge to  eth1. I've tried setting up a bridged adapter but that didn't work  either, I will try it again later.

My iptables and route on the host look like this:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         184.70.141.81   0.0.0.0         UG    100    0        0 eth0
10.10.10.0      0.0.0.0         255.255.255.0   U     0      0        0 virbr3
10.10.10.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.10.12.0      0.0.0.0         255.255.255.0   U     0      0        0 virbr2
184.70.141.80   0.0.0.0         255.255.255.252 U     0      0        0 eth0

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:67

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            10.10.12.0/24        state RELATED,ESTABLISHED
ACCEPT     all  --  10.10.12.0/24        0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable
ACCEPT     all  --  10.10.10.2           10.10.10.0/24       
ACCEPT     all  --  10.10.10.2           10.10.10.0/24       

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

And  iptables for the SMEserver guest are defined by the default SMEserver  install as a gateway and server which should supply dhcp and routing to  allow internet for an internal network.

Sorry for the long post  but I feel it was necessary to include as much detail as possible.  Hopefully there is enough info there and someone can help me solve the  problem!

---

