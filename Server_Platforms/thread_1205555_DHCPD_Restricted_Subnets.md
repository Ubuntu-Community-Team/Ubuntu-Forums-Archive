---
title: "DHCPD Restricted Subnets"
date: 2009-07-06
forum: Server Platforms
---

### Post by Keithamus on 2009-07-06
I'm trying to use DHCPD to set up two subnets. One is wired (which currently works), the other is a "wireless" connection, which I want to restrict access to just the internet. Here is my DHCPD.conf:

```

option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 3600;
max-lease-time 604800;

# Our wired network sits between 192.168.1.100 and 192.168.1.200
subnet 192.168.1.0 netmask 255.255.255.0 {
        authoritative;
        range 192.168.1.100 192.168.1.200;
        option routers 192.168.1.252;
        option broadcast-address 192.168.1.255;
        filename "pxelinux.0";
        }

# Our wireless network sits between 192.168.2.100 and 192.168.2.200
subnet 192.168.2.0 netmask 255.255.255.0 {
        authoritative;
        range 192.168.2.100 192.168.2.200;
        option routers 192.168.2.253;
        option broadcast-address 192.168.2.255;
        filename "pxelinux.0";
        }

```

So I want the Wireless network (192.168.2.*) to see the internet (sitting on 192.168.1.252) but no other machines in the 192.168.1.* subnet.

---

