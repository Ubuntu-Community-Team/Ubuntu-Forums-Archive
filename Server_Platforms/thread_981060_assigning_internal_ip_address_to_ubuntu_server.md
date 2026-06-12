---
title: "assigning internal ip address to ubuntu server"
date: 2008-11-13
forum: Server Platforms
---

### Post by wardolb on 2008-11-13
does anyone know how cant seem to find anything about it on the net, just how to convert dhcp to static is all i able to find..i would just like to use 192.168.2.2 for the computer that my printer and samba shares are on...

---

### Post by Philio on 2008-11-13
lol completely misread this post!

---

### Post by oneloveamaru on 2008-11-13
> **wardolb said:**
> does anyone know how cant seem to find anything about it on the net, just how to convert dhcp to static is all i able to find..i would just like to use 192.168.2.2 for the computer that my printer and samba shares are on...

Here is a sample for you. This will make your eth0 have a static IP of 192.168.2.2, assuming your gateway is 192.168.2.1

You also will need to adjust your /etc/resolv.conf to your DNS server, as it was creating it automatically via DHCP. The settings may stay on a reboot though.

Example of /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

---

### Post by Philio on 2008-11-13
> **oneloveamaru said:**
> allow-hotplug eth0

This doesn't always work, may need to use this instead:

auto eth0

---

### Post by cariboo on 2008-11-13
@oneloveamaru

Is this something new?

> allow-hotplug eth0

I usually use:

```
auto eth0
```

I was having problems with dhcp overriding my static settings, so I uninstalled dhcp3-client, and things are now working as expected. Would the hotplug option prevented the problem?

Jim

---

### Post by oneloveamaru on 2008-11-13
allow-hotplug is a lot like auto. man interfaces

And yes, some systems do not like it but I haven't encountered a system that didn't like it in quite a while.

---

### Post by wardolb on 2008-11-13
> **oneloveamaru said:**
> Here is a sample for you. This will make your eth0 have a static IP of 192.168.2.2, assuming your gateway is 192.168.2.1

You also will need to adjust your /etc/resolv.conf to your DNS server, as it was creating it automatically via DHCP. The settings may stay on a reboot though.

Example of /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

i added this but changed the info to my network info (ie. netmask, gateway),but i have a question about the network line is that the address for my router cause i believe ive set it up right but it still doesnt work. i loose my internet connection which by the way is wireless via dhcp(if that matters) and i get this error ->Ignoring unknown interface eth1=eth1.

---

### Post by oneloveamaru on 2008-11-13
You need to find out what your wireless connection is called. wlan0? eth1? You need to edit the interfaces file accordingly. Do an ifconfig -a and that will show you all connections.

---

### Post by Philio on 2008-11-13
> **wardolb said:**
> i added this but changed the info to my network info (ie. netmask, gateway),but i have a question about the network line is that the address for my router cause i believe ive set it up right but it still doesnt work. i loose my internet connection which by the way is wireless via dhcp(if that matters) and i get this error ->Ignoring unknown interface eth1=eth1.

The gateway value is the IP address of your router.

Can you copy over your /etc/network/interfaces file.

Also output from ifconfig might be useful.

---

### Post by wardolb on 2008-11-13
im good to go, thanks for the help

---

