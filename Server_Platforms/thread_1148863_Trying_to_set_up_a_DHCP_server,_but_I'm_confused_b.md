---
title: "Trying to set up a DHCP server, but I'm confused by it"
date: 2009-05-04
forum: Server Platforms
---

### Post by SFauconnier on 2009-05-04
I'm trying to set up a DHCP server for the first time, but it's harder than I thought..

I've installed DHCP3-server and BIND9.
The DHCP and BIND servers both work. My server sends out IP adresses to other clients in the network (from a range starting at 192.168.1.10).
Also, when I ping (for example) google.com, it shows google's IP but has a 100% packet loss. Why is that? It's like everything works, but it's just not sharing the internet.

This is my dhcpd.conf file:
```
# Sample /etc/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1;
option netbios-name-servers 192.168.1.1;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
}

```

This is my interfaces config
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

#auto eth0
#iface eth0 inet static
#	address 192.168.1.1
#	network 192.168.1.0
#	netmask 255.255.255.0
#	broadcast 192.168.1.255
#

```

Hope someone out there can help. Thanks in advance!

---

### Post by Iowan on 2009-05-04
Depending on the size of your network, it might be worth checking into dnsmasq - which integrates DHCP and DNS server.  It's still on my to-do list, but it seemed to work on the Freesco router I had.

---

### Post by koenn on 2009-05-05
> **SFauconnier said:**
> I'm trying to set up a DHCP server for the first time, but it's harder than I thought..

I've installed DHCP3-server and BIND9.
The DHCP and BIND servers both work. My server sends out IP adresses to other clients in the network (from a range starting at 192.168.1.10).
Also, when I ping (for example) google.com, it shows google's IP but has a 100% packet loss. Why is that? It's like everything works, but it's just not sharing the internet.

If a dhcp server hands out address leases, it works. It is not supposed to do anything else. 
If you ping a hostname and it returns an address, you have a functioning DNS on your network.

your lack of connectivity is most likely not related to DNS or DHCP
Neither DNS or DHCP have anything to do with internet connection sharing

You'll have to redefine what it is you are trying to do and provide more, and more accurate, information about what you are trying to accomplisch, what you have set up so far and how, how your network is laid out, etc.

---

### Post by koenn on 2009-05-05
> **Iowan said:**
> Depending on the size of your network, it might be worth checking into dnsmasq - which integrates DHCP and DNS server.  It's still on my to-do list, but it seemed to work on the Freesco router I had.
It works, and it's an excellent solution for small and medium sized networks

---

