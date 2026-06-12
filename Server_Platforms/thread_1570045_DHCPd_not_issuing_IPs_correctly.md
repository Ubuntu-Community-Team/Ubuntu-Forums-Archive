---
title: "DHCPd not issuing IPs correctly"
date: 2010-09-07
forum: Server Platforms
---

### Post by frillip on 2010-09-07
My set up is as follows.

The client computer requests an IP, if the MAC address is known, the client is issued a 10.0.2.x address, if unknown, it's issued a 192.168.1.x address.

This was working fine when I first set it up, nothing has changed since then (apart from updating via aptitude), yet now when a host is unknown, the DHCP server refuses to give it any IP [-X

I've been at it now for hours and I'm no closer to understanding why it's just given up on me...

Any help is gratefully received,

Phil

My defined network interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# LAN                          
auto eth0
iface eth0 inet static
        address 10.0.2.1
        netmask 255.255.255.0
        network 10.0.2.0
        broadcast 10.0.2.255

# Virtual interface for 192.168.1.0 network
auto eth0:0
iface eth0:0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

# The internet                 
auto eth1
iface eth1 inet dhcp
```

My dhcpd.conf:
```
log-facility local7;
ddns-updates off;
ddns-update-style interim;
option time-offset -0;
default-lease-time 6000;
max-lease-time 72000;
authoritative;

shared-network local {

        subnet 10.0.2.0 netmask 255.255.255.0 {
                range 10.0.2.1 10.0.2.50;
                option subnet-mask 255.255.255.0;
                option ntp-servers 10.0.2.1;
                option broadcast-address 10.0.2.255;
                option netbios-name-servers 10.0.2.1;
                option routers 10.0.2.1;
                option domain-name "SkyNet";
                option domain-name-servers 8.8.8.8, 8.8.4.4;
                deny unknown-clients;

                include "/etc/dhcp3/hosts.conf"
        }

        subnet 192.168.1.0 netmask 255.255.255.0 {
                range 192.168.1.2 192.168.1.50;
                option routers 192.168.1.1;
                option subnet-mask 255.255.255.0;
                option domain-name-servers 8.8.8.8, 8.8.4.4;
                option broadcast-address 192.168.1.255;
                allow unknown-clients;
        }
}

```

The syslog file when restarting the service and requesting IPs with both known and unknown clients:
```
Sep  7 20:36:14 Paprika dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Sep  7 20:36:14 Paprika dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Sep  7 20:36:14 Paprika dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Sep  7 20:36:14 Paprika dhcpd: All rights reserved.
Sep  7 20:36:14 Paprika dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Sep  7 20:36:16 Paprika dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Sep  7 20:36:16 Paprika dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Sep  7 20:36:16 Paprika dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Sep  7 20:36:16 Paprika dhcpd: All rights reserved.
Sep  7 20:36:16 Paprika dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Sep  7 20:36:16 Paprika dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Sep  7 20:36:16 Paprika dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Sep  7 20:36:16 Paprika dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Sep  7 20:36:16 Paprika dhcpd: All rights reserved.
Sep  7 20:36:16 Paprika dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Sep  7 20:36:17 Paprika dhcpd: Wrote 0 deleted host decls to leases file.
Sep  7 20:36:17 Paprika dhcpd: Wrote 0 new dynamic host decls to leases file.
Sep  7 20:36:17 Paprika dhcpd: Wrote 28 leases to leases file.
Sep  7 20:36:17 Paprika dhcpd: 
Sep  7 20:36:17 Paprika dhcpd: No subnet declaration for eth0:0 (0.0.0.0).
Sep  7 20:36:17 Paprika dhcpd: ** Ignoring requests on eth0:0.  If this is not what
Sep  7 20:36:17 Paprika dhcpd:    you want, please write a subnet declaration
Sep  7 20:36:17 Paprika dhcpd:    in your dhcpd.conf file for the network segment
Sep  7 20:36:17 Paprika dhcpd:    to which interface eth0:0 is attached. **
Sep  7 20:36:17 Paprika dhcpd: 
Sep  7 20:42:38 Paprika dhcpd: DHCPDISCOVER from 00:11:09:xx:xx:xx via eth0
Sep  7 20:42:38 Paprika dhcpd: DHCPOFFER on 10.0.2.4 to 00:11:09:xx:xx:xx via eth0
Sep  7 20:43:24 Paprika dhcpd: DHCPDISCOVER from 00:11:22:33:44:55 via eth0: unknown client

```

---

### Post by frillip on 2010-09-14
Not even a nibble? :(

Phil

---

### Post by BkkBonanza on 2010-09-14
Only thing I can see is maybe your virtual interface eth0:0 isn't brought up correctly. You have a message there that appears to indicate it's mapped as 0.0.0.0/0 where I think you intend it to be 192.168.1.1. I would check why dhcp is posting this message:

> Sep  7 20:36:17 Paprika dhcpd: No subnet declaration for eth0:0 (0.0.0.0).
Sep  7 20:36:17 Paprika dhcpd: ** **Ignoring requests on eth0:0**.  If this is not what
Sep  7 20:36:17 Paprika dhcpd:    you want, please write a subnet declaration
Sep  7 20:36:17 Paprika dhcpd:    in your dhcpd.conf file for the network segment
Sep  7 20:36:17 Paprika dhcpd:    to which interface eth0:0 is attached. **


as it would seem to be why it won't assign an IP.

Another thing to check is if you still have valid routes in the routing table.

---

### Post by frillip on 2010-09-21
Output of the 'route' command is as follows:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
10.0.2.0        *               255.255.255.0   U     0      0        0 eth0
80.x.x.0      *               255.255.252.0   U     0      0        0 eth1
default         xxxxxxx 0.0.0.0         UG    100    0        0 eth1
```

As far as I can tell it looks fine... (Please correct me if I'm wrong)

Also by removing the virtual interface from /etc/default/dhcp3-server, I've eliminated the error messages. Apparently as it's the same physical interface, it doesn't need to be included. However the problem is still that DHCPd receives the DHCPREQUEST on eth0 but then doesn't offer a 192.168.1.x IP, even though I've set that subnet to 'allow unknown-hosts' :(

Phil

---

### Post by frillip on 2010-09-23
Ok, so I've fixed my problem. The 'include' line was causing the dhcp server to deny all unknown clients. By removing that and including all the hosts within the subnet declaration in dhcpd.conf, it magically started working again :D

I'm fairly sure that's a bug. How would I go about reporting it?

Phil

---

### Post by CharlesA on 2010-09-23
File a bug report from within ubuntu.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by SeijiSensei on 2010-09-23
> **frillip said:**
> I'm fairly sure that's a bug. How would I go about reporting it?

Before you do that, how about adding a semicolon to the end of the include line?

---

### Post by BkkBonanza on 2010-09-23
Ha, that's why it was ignoring requests on eth0 - missing semi-colon. Such simple things...

---

