---
title: "unable to ping on eth2"
date: 2009-05-14
forum: Server Platforms
---

### Post by theref on 2009-05-14
Hi

I have two NICs in my Ubuntu 8.10 server but can only ping out on eth0, not eth2.  I have static IPs assigned to the two NICs which are outside of my router DHCP range (which is attached to a cable modem).

I can ping out on eth0 by doing ```
ping -I eth0 google.com
``` however when I do ```
ping -I eth2 google.com
``` all I get is lost packets.

My current network set up is as follows:

Cable Modem>Cable Router(192.168.0.79 - DHCP range 80-85)>router (192.168.0.150, netmask 255.255.255.0, DHCP off)>Ubuntu Server(eth0 192.168.0.200, eth2 192.168.0.201).  The server is not connected directly to the first router due to it being in a different room.  I have connected the two routers via LAN ports.

ifconfig -a gives:
```
eth0      Link encap:Ethernet  HWaddr 00:30:1b:b1:c0:0e  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb1:c00e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:232686 (232.6 KB)  TX bytes:445718 (445.7 KB)
          Interrupt:22 Base address:0xc000 

eth2      Link encap:Ethernet  HWaddr 00:0f:3d:ee:8a:60  
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:feee:8a60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3972 (3.9 KB)  TX bytes:3468 (3.4 KB)
          Interrupt:18
```

/etc/network/interfaces gives:
```
# The primary network interface
#auto eth0
#iface eth0 inet dhcp
auto eth0
iface eth0 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.79

#Secondary NIC
#auto eth2
#iface eth2 inet dhcp
auto eth2
iface eth2 inet static
        address 192.168.0.201
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.79

```

netstat -rn gives:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0      0.0.0.0         255.255.255.0   U         0 0          0 eth2
0.0.0.0         192.168.0.79     0.0.0.0         UG        0 0          0 eth2
0.0.0.0         192.168.0.79     0.0.0.0         UG        0 0          0 eth0

```

route gives:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0      0.0.0.0         255.255.255.0   U         0 0          0 eth2
0.0.0.0         192.168.0.79     0.0.0.0         UG        0 0          0 eth2
0.0.0.0         192.168.0.79     0.0.0.0         UG        0 0          0 eth0

```

/etc/resolv.conf gives:
```
nameserver 192.168.0.79
```

/etc/hosts gives:
```
127.0.0.1       localhost
127.0.1.1       server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Please help. Many thanks in advance.

---

### Post by a9k3d on 2009-05-14
Try running three terminals (I'd use screen) then run
1) **tcpdump -n -i eth0 icmp**
2) **tcpdump -n -i eth2 icmp**
3) **ping -c 1 -I eth2 192.168.0.79**
The screens 1 and 2 should show what happened. You probably don't need to ping google.com to fail.

I suspect your ping request goes out eth2 but comes back on eth0 but the above technique gives you the real answer.

I've never put two physical interfaces on the same net, instead I'd use aliases on the first interface. I'm a huge fan of using an IP for each function - that way if you decide to move port 80 to another local box, just move the IP from one box to another.

What are you trying to accomplish with the two IP's?

---

### Post by theref on 2009-05-15
Thanks for that.  You are right, the ping request from eth2 comes back to eth0.  Why is that?

I am wanting to split services per IP, e.g. smtp on 192.168.0.200 and http on 192.168.0.201.

Is there a way in which I can make it work? What changes should I make to my /etc/network/interfaces file to split the NICs on to two separate nets?

Thanks in advance.

---

