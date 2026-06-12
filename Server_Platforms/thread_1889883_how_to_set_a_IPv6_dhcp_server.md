---
title: "how to set a IPv6 dhcp server"
date: 2011-12-02
forum: Server Platforms
---

### Post by fantome2025 on 2011-12-02
Hello every one

I' am trying to make a IPv6 dhcp server. For that i looked on Internet for find some information, but I don't arrive.

for make my server, I install Isc-dhcp-server in which one I wrote inside dhcpd.conf
```

default-lease-time 600;
max-lease-time 7200; 
log-facility local7; 
subnet6 2001:db8:0:1::/64 {
        # Range for clients
        range6 2001:db8:0:1::129 2001:db8:0:1::254;
        # Additional options
        option dhcp6.name-servers fec0:0:0:1::1;
        option dhcp6.domain-search "domain.example";
        # Prefix range for delegation to sub-routers
        prefix6 2001:db8:0:100:: 2001:db8:0:f00:: /56;
        # Example for a fixed host address
        host specialclient {
            host-identifier option dhcp6.client-id 00:01:00:01:4a:1f:ba:e3:60:b9:1f:01:23:45;
            fixed-address6 2001:db8:0:1::127;
        } 
} 

``` I changed the dhcp6.client-id

and I installed "radvd" without modification.
I launch the service with ```
[COLOR=#000000]# /usr/sbin/dhcpd -6 -f -cf /etc/dhcp/dhcpd.conf eth1 [/COLOR]
```but when I connect my server (a laptop) to a client (a laptop on w7), nothing is happening

---

### Post by collisionystm on 2011-12-02
[http://www.linuxtopia.org/online_books/network_administration_guides/Linux+IPv6-HOWTO/hints-daemons-dhcpv6..html](http://www.linuxtopia.org/online_books/network_administration_guides/Linux+IPv6-HOWTO/hints-daemons-dhcpv6..html)

[http://tldp.org/HOWTO/html_single/Linux+IPv6-HOWTO/](http://tldp.org/HOWTO/html_single/Linux+IPv6-HOWTO/)

---

### Post by fantome2025 on 2011-12-07
I found the source that you gave me.

Install radvd & isc-dhcp-server

but I don't have a dhcp6s.conf in "etc/"
That my problem for both links. 
I have folders named "dhcp3" and "dhcp", in the one named "dchp" I have one conf files ! but I have the impression that it command nothing

---

