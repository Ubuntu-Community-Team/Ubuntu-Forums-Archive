---
title: "networkin help"
date: 2008-09-11
forum: Virtualisation
---

### Post by maerlma on 2008-09-11
hi all. i have LAMP server running on Hardy serving some web based applications. i'd like to setup a guest ftp server on this same box. i managed to get VirtualBox installed and even have a guest (Hardy as well) already installed. My trouble is correctly setting up the bridge for the host-based networking. When I enable the bridge, i'm unable to reach my webpages. 

here's my /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual
        #address 10.0.0.28
        #netmask 255.255.255.0
        #gateway 10.0.0.1

#network bridge for VMs
iface br0 inet static
       address 10.0.0.28
       netmask 255.255.255.0
       gateway 10.0.0.1
       bridge_ports eth0

```

what am i missing?

---

