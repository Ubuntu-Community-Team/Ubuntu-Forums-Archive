---
title: "ltsp with dual ethernet card - slow net access"
date: 2012-05-17
forum: Server Platforms
---

### Post by hundred1906 on 2012-05-17
My ltsp host is suffering very slow web page look-ups. After install it seemed OK straight "out of the box" but has recently become unusable though I do not recall changing anything in the set up.

I could use some help in trying to understand what is going wrong because the various config files look OK to me.

The install was from the F4 (ltsp) option on the 12.04 Alternate Distribution. eth0 is the Primary Network, going of to my Linksys router. eth1 is connected to the thin client (which boots OK).

My understanding was that eth0 is not dhcp managed by my host, leaving that up to my router. But that eth1 is dhcpd managed. I wanted it that way so that I do not have to reconfigure other parts of my network and can operate the thin clients in isolation.

ifconfig looks like this:
```
eth0      Link encap:Ethernet  HWaddr 00:11:09:2e:77:13  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe2e:7713/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15992676 (15.9 MB)  TX bytes:1175286 (1.1 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:02:44:3a:8e:aa  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe3a:8eaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26111 (26.1 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95967 (95.9 KB)  TX bytes:95967 (95.9 KB)
```
The ltsp/dhcpd.conf contains this:
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

etc/network.interfaces has this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
```

I also have a Trace Route and an IP Route output available but have not attached these at this point, basically to keep down the size of this initial post.

---

### Post by hundred1906 on 2012-05-18
Solved this myself. Nothing to do with my server. It is due to degradation of the link down to the router.

---

