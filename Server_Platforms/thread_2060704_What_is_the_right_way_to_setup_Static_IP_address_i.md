---
title: "What is the right way to setup Static IP address in Ubuntu 12.04?"
date: 2012-09-20
forum: Server Platforms
---

### Post by donniezazen on 2012-09-20
Hi,

I am unable to setup static IP in my new Ubuntu 12.04 server setup. Here is my basic configuration /etc/network/interfaces.

This breaks internet but sets static IP address.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.86
netmask 255.255.255.0
gateway 192.168.0.1
```

Adding dns-nameserver 8.8.8.8 to same file gives virtual network device failed and waiting 60 seconds for network configuration and network doesn't work at all ssh or internet.

Thanks.

---

### Post by CharlesA on 2012-09-20
```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

```

---

### Post by donniezazen on 2012-09-20
Thanks.

I added network broadcast and dns-nameservers. Initially I had dns-nameserver without s and neiter static IP or dyndns worked. Now both are working. I am just dropping my config here for future reference.

Thanks again.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.86
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 8.8.8.8 8.8.4.4
```

---

