---
title: "Openvpn Lan cannot ping vpn clients"
date: 2018-07-23
forum: Ubuntu Cloud and Juju
---

### Post by yukaputz on 2018-07-23
Hello all, 

I would first like to say if I am posting this in the wrong place please let me know, I landed here researching my issue and found a thread that was similar but not exactly my issue, so I'm hoping this forum can help.  This is my last hurdle to complete unicorns and nirvana.  :-)

I am running a Ubuntu based Open Vpn Access Server in Azure.  ](*,)

Static clients get a 172.28.224.0/20 address
Dynamic clients get a 172.27.224.0/20 address
One dynamic client acts as a gateway for a 192.168.10.0/24
Another dynamic client acts as a gateway for a 192.168.1.0/24
 The Open VPN server also has a nic 10.1.0.6/24
There is a windows server 10.1.0.4 with 10.1.0.6 set as its default gateway on the Azure Vnet

Static and dynamic clients can ping each other.  Groovy!
Static and dynamic clients can ping the 192 networks.  Groovy!
The 192 networks can ping the static and dynamic clients.  Groovy
Static and dynamic and 192 clients can ping 10.1.0.6.  Groovy!
Static and dynamic and 192 clients can ping 10.1.0.4 Groovy!

wait for it....

The windows server with all windows firewalls turned off cant ping any of the vpn clients or the networks they are the gateways for.  ERMAHGERD RLY?!  

Ip forwarding is enable on the Open Vpn Server.  
The windows server is using the open vpn server as its default gateway as well. 

I'm at a loss as to what to do next.  Static routes on the windows server?  But it has the vpn server as the dg so that won't do anything. 

Some sort of routing that I'm not aware of how to do on the vpn server?


HALP?

---

### Post by yukaputz on 2018-07-23
Also, here is the routing table from the OVPN server.  The answer is probably staring right in the face but I"m too tired to see it.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.0.1        0.0.0.0         UG    0      0        0 eth0
10.1.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
168.63.129.16   10.1.0.1        255.255.255.255 UGH   0      0        0 eth0
169.254.169.254 10.1.0.1        255.255.255.255 UGH   0      0        0 eth0
172.27.224.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t0
172.27.228.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t1
172.27.232.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t2
172.27.236.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t3
172.28.232.10   0.0.0.0         255.255.255.255 UH    0      0        0 as0t3
172.28.232.12   0.0.0.0         255.255.255.255 UH    0      0        0 as0t2
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 as0t3

And the routing table from the windows server.
===========================================================================
Interface List
  5...00 0d 3a 4d 61 7d ......Microsoft Hyper-V Network Adapter #2
  1...........................Software Loopback Interface 1
  3...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
  6...00 00 00 00 00 00 00 e0 Microsoft Teredo Tunneling Adapter
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0         10.1.0.6         10.1.0.4    266
         10.1.0.0    255.255.255.0         On-link          10.1.0.4    266
         10.1.0.4  255.255.255.255         On-link          10.1.0.4    266
       10.1.0.255  255.255.255.255         On-link          10.1.0.4    266
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    331
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    331
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link          10.1.0.4    266
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    331
  255.255.255.255  255.255.255.255         On-link          10.1.0.4    266
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
          0.0.0.0          0.0.0.0         10.1.0.6  Default
===========================================================================

Persistent Routes:
  None

---

