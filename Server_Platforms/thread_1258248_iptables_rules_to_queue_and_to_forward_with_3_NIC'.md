---
title: "iptables rules to queue and to forward with 3 NIC's"
date: 2009-09-04
forum: Server Platforms
---

### Post by Gen2ly on 2009-09-04
Hello everyone.  I'm still pretty new to iptables and need some help in setting up my router.  My setup is that I need snort to queue to two NIC's from the Internet and then I need to forward to the internal NIC.  Here's how I have my interfaces set up:

```
# /etc/network/interfaces

# Loopback interface
auto lo
iface lo inet loopback

# Bridge for snort
auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1
bridge_maxwait 0

# LAN NIC
auto eth2
iface eth2 inet static
  address 192.168.89.100
  netmask 255.255.255.0
```

From the documentation I've read, queuing is done as:

```
iptables -A INPUT -j QUEUE
```

Why question is how do I forward traffic from the internet then to the LAN NIC?  Would I have to use nat in a rule like?:

```
iptables -t nat -A POSTROUTING <device>
```

I think this is pretty close but not sure what device I should use.

---

### Post by Gen2ly on 2009-09-06
Anybody had any experience in this?  I am going in the right direction, right?

---

