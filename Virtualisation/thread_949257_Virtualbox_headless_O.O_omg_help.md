---
title: "Virtualbox headless O.O omg help"
date: 2008-10-16
forum: Virtualisation
---

### Post by thefatmoop on 2008-10-16
ok so i'm running virtualbox headless from terminal only to virtualize, and i want to run a windows 2003 server with active directory. I need the virtual to have access to the network and have it's own real ip address (not a NAT from the virtual machine host)

read on virtualbox user manual and i was told i need to make an HIF virtual card and bridge the ports..

what i originally had:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.170
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

#Vbox0
auto br0
iface br0 inet static
address 192.168.1.180
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
bridge_ports eth0 
```

and the error with that
```

"br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature." 
```

what i tried later:

```

auto brdg
iface brdg inet static
        bridge_maxwait 0
        bridge_ports eth0 vbox0
        address 192.168.1.170
        netmask 255.255.255.0

#auto eth0
iface eth0 inet manual

#auto vbox0
iface vbox0 inet manual 
```

i haven't seen the error for that cause i was doing it over ssh... and whenever it messes up it drops the server connection lol 



anyone know what to do? it's ubuntu server 8.04

---

### Post by thefatmoop on 2008-10-16
Lol someone halp meh!

---

### Post by eppo on 2008-10-17
are you also editing the /etc/vbox/interfaces file?
that fill will spawn bridged interfaces for your virtualbox guests to bind to.
then you go and edit your virtual machine to use those interfaces.

---

