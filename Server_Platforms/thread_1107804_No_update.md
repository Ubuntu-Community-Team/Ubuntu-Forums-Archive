---
title: "No update"
date: 2009-03-27
forum: Server Platforms
---

### Post by Spikerok on 2009-03-27
after upating network settings, setting static ip address im unable to download any updates using apt-get update/upgrade or any other program updates

/etc/apt/sources.list looks ok..

i want ip to be static, and I want to know what to change in the configuration to make ip static and to be able to download updates

im getting error - SIOCDELRT: No such process

---

### Post by Spikerok on 2009-03-27
> **Spikerok said:**
> after upating network settings, setting static ip address im unable to download any updates using apt-get update/upgrade or any other program updates

/etc/apt/sources.list looks ok..

/etc/network/interfaces - when i had error with update
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/PHP]
then i have changed iface eth0 inet 
now i have next settings in sources.list and im able to download updates
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dncp
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/PHP]

---

### Post by namaku0 on 2009-03-27
> **Spikerok said:**
> sources.list - when i had error with update
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/PHP]
then i have changed iface eth0 inet 
now i have next settings in sources.list and im able to download updates
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dncp <-- THIS AND BELOW!
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/PHP]

Not only very close on the keyboard, 'n' and 'h' also
looks alike.

If you are planning to use DHCP it should be like this:

> [PHP]
# The primary network interface
auto eth0
iface eth0 inet dhcp
[/PHP]

No address, netmask, network, broadcast, and gateway part.

---

### Post by Spikerok on 2009-03-27
i want it to be static, and I want to know what to change in the configuration to make it static

im getting error - SIOCDELRT: No such process

---

### Post by Spikerok on 2009-03-27
...

---

### Post by cariboo on 2009-03-27
This solution is not very elegant, but if you don't need dhcp, get rid of the dhcp client:

```
sudo apt-get purge dhcp3-client
```

Jim

---

### Post by Spikerok on 2009-03-27
well i have change config, i have
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1  
[/PHP]

i still unable to connect to download updates, or to connect to computer

---

### Post by Spikerok on 2009-03-27
i can't even use dhcp now..

well i got it working now, i tihnk i got it what to do to fix it!

---

### Post by Spikerok on 2009-03-27
double post

---

### Post by Spikerok on 2009-03-27
can't download any thing, managed to make it static.

---

