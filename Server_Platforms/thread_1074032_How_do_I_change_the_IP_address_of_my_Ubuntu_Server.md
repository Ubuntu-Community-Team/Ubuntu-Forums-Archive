---
title: "How do I change the IP address of my Ubuntu Server"
date: 2009-02-18
forum: Server Platforms
---

### Post by JimTDI on 2009-02-18
I setup the server a few years ago (think it's 6.06 LTS) and it's sitting on a DMZ port on my firewall.  I want to move it to the internal network, and port forward to it from my firewall.

I forget how the original install asked me about the IP address - but I want to change the IP address from an external to an internal (192.168.xxx.xxx range) Ip address.

Can someone tell me how I would do that?  Thanks very much!

---

### Post by rhcm123 on 2009-02-18
> **JimTDI said:**
> I setup the server a few years ago (think it's 6.06 LTS) and it's sitting on a DMZ port on my firewall.  I want to move it to the internal network, and port forward to it from my firewall.

I forget how the original install asked me about the IP address - but I want to change the IP address from an external to an internal (192.168.xxx.xxx range) Ip address.

Can someone tell me how I would do that?  Thanks very much!

The simplest way is to do the following

```
sudo nano /etc/network/interfaces
```

and set as such (this is from my own server file):
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.2.193
	netmask 255.255.255.0
	gateway 192.168.2.1

```

EDIT: in case i forgot to mention
address = assigned ip of the server
netmask = subnet mask
gateway = default gateway

there are other options (e.g. broadcast) that can be used, but this is what i use and it works just fine.

---

### Post by JimTDI on 2009-02-18
> **rhcm123 said:**
> The simplest way is to do the following

```
sudo nano /etc/network/interfaces
```

and set as such (this is from my own server file):
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.2.193
	netmask 255.255.255.0
	gateway 192.168.2.1

```


Thanks very much!  That's EXACTLY what I was looking for!!

---

### Post by rhcm123 on 2009-02-18
> **JimTDI said:**
> Thanks very much!  That's EXACTLY what I was looking for!!

no probs
just be sure to use the right interfaces (you saw on mine i only have a loopback and eth0 interface) be sure to modify your file accordingly! I ususally just change the "dhcp" to "static" and then add the arguments below.

good hunting :)

---

### Post by JimTDI on 2009-02-18
> **rhcm123 said:**
> no probs
just be sure to use the right interfaces (you saw on mine i only have a loopback and eth0 interface) be sure to modify your file accordingly! I ususally just change the "dhcp" to "static" and then add the arguments below.

good hunting :)


Cool!  In my case it's already assigned a static (I have an 8 block) so should be minimal editing.  Maybe I'll try VI again!  ;-)

Thanks again!

---

### Post by rhcm123 on 2009-02-18
> **JimTDI said:**
> Cool!  In my case it's already assigned a static (I have an 8 block) so should be minimal editing.  Maybe I'll try VI again!  ;-)

Thanks again!

vi (shivers) good luck with that :) Nano all the way.

---

