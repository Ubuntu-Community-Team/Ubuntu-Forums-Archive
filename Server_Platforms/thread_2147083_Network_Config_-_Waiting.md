---
title: "Network Config - Waiting"
date: 2013-05-20
forum: Server Platforms
---

### Post by chrisguk on 2013-05-20
I have a strange problem. My network has been up and running for some time and all of a sudden when I goto reboot the DNS and NAS Servers they boot up with:

Waiting for network configuration
blah blah blah still waiting for another 60 seconds

These servers along with 2 others both have static IPs and they have been added to the DHCP server as static IPs.  Here is the code in my /etc/network/interfaces:

```


auto eth0
iface eth0 inet static
    address 172.22.22.100
    netmask 255.255.255.0
    network 172.22.22.0
    broadcast 172.22.22.255
    gateway 172.22.22.1

auto eth1
iface eth1 inet static
    address 172.22.22.101
    netmask 255.255.255.0
    network 172.22.22.0
    broadcast 172.22.22.255
    gateway 172.22.22.1
    dns-nameservers 172.22.22.100 172.22.22.101
    dns-domain simpson.home.

# The loopback network interface
auto lo
iface lo inet loopback

```

Any ideas?

---

### Post by DJ_Max on 2013-05-21
These are two separate servers? Or a single server? Which do you reboot first?

---

### Post by chrisguk on 2013-05-21
They are the same server, 2 IPs as its the DNS server.  I actually resolved the issue by removing the "wondershaper" line in /etc/network/interfaces

---

