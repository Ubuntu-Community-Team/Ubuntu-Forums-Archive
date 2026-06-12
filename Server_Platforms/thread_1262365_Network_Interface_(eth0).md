---
title: "Network Interface (eth0)"
date: 2009-09-09
forum: Server Platforms
---

### Post by pg.phatman on 2009-09-09
Hi Everyone

I am a newbie to Ubuntu, I recently installed Ubuntu Server 9.04 (32-bit). However every time I reboot the box, the network interface (Eth0) goes down and also looses its static IP Address, here is how my /etc/network/interfaces config file looks like

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 10.1.2.220
        netmask 255.255.255.0
        network 10.1.2.0
        broadcast 10.1.2.255
        gateway 10.1.2.1

My question is why do I have to manually put the ip address every time and bring the interface up, is there a (network) start up script that I can use?

---

### Post by pg.phatman on 2009-09-09
Hi Everyone

I am a newbie to Ubuntu, I recently installed Ubuntu Server 9.04 (32-bit). However every time I reboot the box, the network interface (Eth0) goes down and also looses its static IP Address, here is how my /etc/network/interfaces config file looks like

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 10.1.2.220
        netmask 255.255.255.0
        network 10.1.2.0
        broadcast 10.1.2.255
        gateway 10.1.2.1

My question is why do I have to manually put the ip address every time and bring the interface up, is there a (network) start up script that I can use?

---

### Post by pg.phatman on 2009-09-09
Hi Everyone

I am a newbie to Ubuntu, I recently installed Ubuntu Server 9.04 (32-bit). However every time I reboot the box, the network interface (Eth0) goes down and also looses its static IP Address, here is how my /etc/network/interfaces config file looks like

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 10.1.2.220
        netmask 255.255.255.0
        network 10.1.2.0
        broadcast 10.1.2.255
        gateway 10.1.2.1

My question is why do I have to manually put the ip address every time and bring the interface up, is there a (network) start up script that I can use?

---

### Post by nandemonai on 2009-09-09
> **pg.phatman said:**
> Hi Everyone

I am a newbie to Ubuntu, I recently installed Ubuntu Server 9.04 (32-bit). However every time I reboot the box, the network interface (Eth0) goes down and also looses its static IP Address, here is how my /etc/network/interfaces config file looks like

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 10.1.2.220
        netmask 255.255.255.0
        network 10.1.2.0
        broadcast 10.1.2.255
        gateway 10.1.2.1

My question is why do I have to manually put the ip address every time and bring the interface up, is there a (network) start up script that I can use?

```
**auto eth0**
iface eth0 inet static
        address 10.1.2.220
        netmask 255.255.255.0
        network 10.1.2.0
        broadcast 10.1.2.255
        gateway 10.1.2.1
```

---

### Post by nandemonai on 2009-09-09
*** Double Post ***

Please refer to my answer in the Absolute Beginners Forum.

---

### Post by cariboo on 2009-09-09
If you are running a gui, remove use network-manager to set your static ip address. If you are running from the command line, remove dhcp3-client.

---

