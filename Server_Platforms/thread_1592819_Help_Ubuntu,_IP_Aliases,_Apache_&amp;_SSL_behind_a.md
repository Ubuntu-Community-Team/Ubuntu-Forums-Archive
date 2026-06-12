---
title: "Help: Ubuntu, IP Aliases, Apache &amp; SSL behind a NAT"
date: 2010-10-11
forum: Server Platforms
---

### Post by sean123 on 2010-10-11
Hi,

I'm having issues with what seemed like a fairly simple thing to do, but has turned into a major headache.

**Requirements**
I have a need to add a second SSL certificate to a dedicated Ubuntu box running Apache2.

**What's happened so far?**
Knowing that I need a second public-facing IP address, I asked the  hosting company to set up a second public IP as a 1-to-1 NAT with a new  LAN IP. I set up an IP-alias on the ubuntu NIC card with the new LAN IP  they gave me, and changed Apache's config to listen on the new IP and  changed everything to IP-based virtual hosts.

**The result**
The existing websites continue to operate as normal, however the new one  does not respond to the outside world at all (ping, https, http, ssh,  etc). I have logged into the Ubuntu box and can ping both LAN addresses,  and have used w3m to confirm that both virtual hosts respond correctly  on the LAN. The new public IP just won't respond. The hosting company  are not very experienced with Linux, and so can't offer much advice.  They think that there might be a problem with having two IPs on the one  NIC, that perhaps it's responding on the primary IP instead of the  secondary?

Here's a short explanation of how the network is set up (IPs changed from real-life for privacy):

**LAN IPs**
eth0 - 192.168.0.15
eth0:0 - 192.168.0.16

subnet - 255.255.255.0
broadcast - 192.168.0.255
network - 192.168.0.0
gateway - 192.168.0.1

**Public IPs**
200.100.200.71
200.100.200.87

Can anyone help me out with some possible "gotchas" that I've missed?

**Config Info**

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:20:32:28:a1
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe32:28a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:359393 (350.9 KB)  TX bytes:202896 (198.1 KB)
          Interrupt:16

eth0:0    Link encap:Ethernet  HWaddr 00:0f:20:32:28:a1
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26355502 (25.1 MB)  TX bytes:26355502 (25.1 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                                  -00
          inet addr:172.23.112.58  P-t-P:172.23.112.57  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:281529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:487003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:20771272 (19.8 MB)  TX bytes:661383012 (630.7 MB)
``````

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.23.112.1    172.23.112.57   255.255.255.255 UGH   0      0        0 tun0
192.168.0.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1    0.0.0.0         UG    100    0        0 eth0
default         192.168.0.1    0.0.0.0         UG    100    0        0 eth0
``````

# The loopback network interface
auto lo eth0 eth0:0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
    address 192.168.0.15
    netmask 255.255.255.0
    broadcast 192.168.0.255
    network 192.168.0.0
    gateway 192.168.0.1
    dns-nameservers 61.88.88.88
    post-up iptables-restore < /etc/iptables.up.rules

iface eth0:0 inet static
    address 192.168.0.16
    netmask 255.255.255.0
    broadcast 192.168.0.255
    network 192.168.0.0
    gateway 192.168.0.1
    dns-nameservers 61.88.88.88

```

---

### Post by sean123 on 2010-10-11
Nevermind - turns out it was a typo in the NAT settings. The above settings were correct.

---

