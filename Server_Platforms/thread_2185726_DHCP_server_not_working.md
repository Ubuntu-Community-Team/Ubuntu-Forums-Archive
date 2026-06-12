---
title: "DHCP server not working"
date: 2013-11-03
forum: Server Platforms
---

### Post by jcarson99 on 2013-11-03
Hello,

I have just completed a fresh install of Ubuntu 12.04.3 on my home server. The installation and configuration of isc-dhcp-server is the same as when I ran 12.04.2 but when I try to get an IP for my clients (Both windows and Ubuntu desktop) no IP is given to those clients. The logs only say "Wrote 0 leases to leases file". Anyone know how to get this working.

Here is my dhcpd.conf

```
ddns-update-style none;
authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.75 192.168.0.100;
option domain-name-servers 192.168.0.1;
option domain-name "hostname.domain.com";
option routers 192.168.0.1;
option broadcast-address 192.168.0.255;
default-lease-time 10000;
max-lease-time 20000;
}
```

Here is my /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
```

and finally my /etc/default/isc-dhcp-server

```
INTERFACES="eth1"
```

Windows client says "Unable to connect to your DHCP server. Timed out".

I have a NIC (eth0) that connects to my ISP and that works fine. I can browse the internet, update the server, etc...

Any help is appreciated.

---

### Post by jcarson99 on 2013-11-04
Turns out my NIC died. Replaced it and everything works now.

---

