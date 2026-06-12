---
title: "Unknown primary network interface"
date: 2016-05-20
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2016-05-20
Hi all

Have installed Ubuntu server 16.04 on a test server and would like to allocate a LAN ip address on startup through /etc/network/interfaces.

Current code is ```

# The primary network interface
auto enp17s0
iface enp17s0 inet dchp
```

On Ubuntu server 14.04 the code was changed to either
```
# The primary network interface
auto p3p1
iface p3p1 inet static
address 192.168.0.49
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4

```

or 

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.49
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4

```

depending on the interface.

What should it be now, please?

TIA

---

### Post by darkod on 2016-05-20
The config parameters are the same, only in 16.04 it is little changed how it names the interfaces. You already have the name of the primary interface, it's enp17s0. If that is the one you want to set up, use that.

If you have multiple interfaces and want to see the name of another one, you can use something like:
```
sudo lshw -short | grep network
```

That should show you all interfaces.

---

### Post by ChrisRChamberlain on 2016-05-20
darkod

Many thanks for resolving the issue and explaining how to show all interfaces.

Chris

---

