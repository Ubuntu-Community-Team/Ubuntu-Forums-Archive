---
title: "Ubuntu Server Setting two nic"
date: 2006-01-06
forum: Server Platforms
---

### Post by wcliao on 2006-01-06
How to setting two nic on ubuntu server ?

---

### Post by adwait on 2006-01-06
Put the NICs in the computer, start up Ubuntu, it will detect them. In the network configuration (Application>system>) give static IPs to each of the nics and you are done. Then bring them up woth
```
sudo ifup eth0
sudo ifup eth1
```

---

### Post by bluefrog on 2006-01-07
you can also use one card and assign a virtual IP to eth0.


sudo vi /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth0:0
iface eth0:0 inet static
        address 192.168.0.101
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1


restart your network afterwards.

james

---

