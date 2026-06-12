---
title: "DHCP in dom0"
date: 2008-10-27
forum: Virtualisation
---

### Post by shoaibi on 2008-10-27
[SIZE="5"]Part One[/SIZE]
My current setup:
```

DSL Router -----------> nextcube
> DHCP
> DNS
> FW
> 10.0.0.138            10.0.0.1

```

As you see that there is only one machine. DHCP,DNS and FW are running in DSL Router, i have NAPT on router so all connection made to my live ip say liv.eip.liv.eip will get to 10.0.0.1 which is my system.

I read about Xen, and i want to implement it at home.

I have got 4 more machines and a 8 port D-Link Switch. What i want is:
1. Run my DHCP server and etc in Xen, as shown on dom1, this should be responsible for ip assignment to clients connected to switch and rest of domUs.
2. if i run DHCP server in dom1, the one on DSL router will be disabled, previously i could access internet by setting my default gw to 10.0.0.138, what about now? What if i assign a static ip to DSL router say 172.30.10.108 by DHCP in dom1?


My future set up:
```

                                                                                    /-----> desk103[DHCP Client]
                                                                                    /-----> desk102[DHCP Client]
DSL Router ----> nextcube ------------------------------------------------------->Switch  ----> boombastic[DHCP Client]
172.30.10.108    > dom0: Iptables for NAT and etc, 172.30.10.1                      \- - -> abacus[DHCP Client]                            
                 > dom1 :fox (DHCP, DNS, Squid, Mail, etc) 172.30.10.101            \-----> desk101 [DHCP Client]
                 > dom2: walter (LAMP) 172.30.10.102


```



Is it possible? if yes, how?


[SIZE="5"]Part two:[/SIZE]

Goal: I want to create a DHCP and DNS server in fox(domU, 172.30.10.101). my dom0 (ip:192.168.10.107) is a part of another network 192.168.10.xxx with gateway as 192.168.10.1.
I want to create a internal and independent LAN of domU's everyone getting IP from fox. fox will be DHCP, DNS, gateway, squid and etc. There will be other machines in physical LAN which would get ip and etc from fox

echo = dom0, 192.168.10.107, 172.30.10.1
fox = domU, 172.30.10.101


```

root@echo:/etc/xen# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:1d:d0:0a  
          inet addr:192.168.10.107  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe1d:d00a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:181997 (177.7 KB)  TX bytes:146760 (143.3 KB)

eth0:0    Link encap:Ethernet  HWaddr 00:1c:c0:1d:d0:0a  
          inet addr:172.30.10.1  Bcast:172.30.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

peth0     Link encap:Ethernet  HWaddr 00:1c:c0:1d:d0:0a  
          inet6 addr: fe80::21c:c0ff:fe1d:d00a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1492  Metric:1
          RX packets:1911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:208968 (204.0 KB)  TX bytes:150396 (146.8 KB)
          Interrupt:17 Base address:0x4000 

vif1.0    Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:39 overruns:0 carrier:0
          collisions:0 txqueuelen:32 
          RX bytes:2304 (2.2 KB)  TX bytes:73927 (72.1 KB)

root@echo:/etc/xen# cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
mtu 1492

auto eth0:0
iface eth0:0 inet static
name Ethernet alias LAN card
    address 172.30.10.1
    netmask 255.255.255.0
    broadcast 172.30.10.255
    network 172.30.10.0
    gateway 192.168.10.1
root@echo:/etc/xen# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.10.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

root@echo:ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=241 time=331 ms

64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=241 time=333 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=241 time=333 ms

root@echo:~$ ping 192.168.10.1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_seq=1 ttl=64 time=0.466 ms
64 bytes from 192.168.10.1: icmp_seq=2 ttl=64 time=0.411 ms
64 bytes from 192.168.10.1: icmp_seq=3 ttl=64 time=0.493 ms

root@echo:~$ ping fox
PING fox (172.30.10.101) 56(84) bytes of data.
64 bytes from fox (172.30.10.101): icmp_seq=1 ttl=64 time=0.107 ms
64 bytes from fox (172.30.10.101): icmp_seq=2 ttl=64 time=0.063 ms
64 bytes from fox (172.30.10.101): icmp_seq=3 ttl=64 time=0.056 ms

--- fox ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.056/0.075/0.107/0.023 ms


################# Going to the domU

root@echo:/etc/xen# xm console fox
root@fox:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:3e:e8:fe:ae  
          inet addr:172.30.10.101  Bcast:172.30.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fee8:feae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77041 (75.2 KB)  TX bytes:2850 (2.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@fox:~# cat /etc/network/interfaces 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 172.30.10.101
 network 172.30.10.0
 gateway 172.30.10.1   ### the alias ip...
 netmask 255.255.255.0
 mtu 1492

root@fox:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.10.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         172.30.10.1     0.0.0.0         UG    100    0        0 eth0

root@fox:~# ping google.com
ping: unknown host google.com

root@fox:~# ping 192.168.10.107
PING 192.168.10.107 (192.168.10.107) 56(84) bytes of data.
64 bytes from 192.168.10.107: icmp_seq=1 ttl=64 time=3.70 ms
64 bytes from 192.168.10.107: icmp_seq=2 ttl=64 time=0.069 ms

--- 192.168.10.107 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 0.069/1.886/3.704/1.818 ms

root@fox:~# ping 192.168.10.1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.

--- 192.168.10.1 ping statistics ---
640 packets transmitted, 0 received, 100% packet loss, time 639046ms

root@fox:~# ping 192.168.10.50
PING 192.168.10.50 (192.168.10.50) 56(84) bytes of data.

--- 192.168.10.50 ping statistics ---
640 packets transmitted, 0 received, 100% packet loss, time 639046ms


```


So as you see, from domU/fox i can ping local machine, my dom0/host one... 
but can't ping any other machine in LAN with my dom0 or google. Problem with gateway? of domU? of dom0?
I might not be able to ping google out any web coz my the gateway at 192.168.10.1 has firewall and only allows traffic from 192.168.10.xxx whereas my domU is on 172.30.10.xxx. But still i should be able to ping domU from other hosts in my LAN...

---

