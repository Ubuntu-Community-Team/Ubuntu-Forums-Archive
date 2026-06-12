---
title: "Problems with assigning an IP address"
date: 2010-01-14
forum: Server Platforms
---

### Post by jongudm on 2010-01-14
I was trying to assign the static IP address of my internet connection to my home server and managed to make a mess of it.  I've configured the router to assign it the address every time but when I rebooted everything the server is cut off from the network completely (rather unfortunate with a headless server...).  The only file I've edited on the server when trying to do this is /etc/network/interfaces, everything else network related is default.  My intention in editing the file was to make the server accept the IP address assigned by the router since the router was already configured to assign the right one.

I put in

```
inet dhcp
```in the /etc/network/interfaces file, is that wrong?  What is that line supposed to be?

---

### Post by boudies on 2010-01-14
I guess you'd have to include the ethernet interface this definition applies to, e.g.
```
ïface eth0 inet dhcp
```

---

### Post by Iowan on 2010-01-14
FWIW, I also like to let the DHCP server manage static leases as well as dynamic leases. **boudies** seems to have the proper format - I assume you added the "auto eth0" line...

---

### Post by jongudm on 2010-01-14
That's what's in there, I just forgot the

```
iface eth0
```

part since I was writing this from memory.

---

### Post by jongudm on 2010-01-14
Is the loopback interface supposed to be active too?

---

### Post by jongudm on 2010-01-14
This gets increasingly bizarre.  Now I tried booting it again, it got a generic LAN ip and I could connect to it without any problems.  Then, without changing anything on the server I shut everything down again (including the router) and restarted.  Now the server was assigned the external IP by DHCP and again it just sits there invisible to the network.  I'm confused...

---

### Post by confusedstingray on 2010-01-14
could you post your /etc/network/interfaces file this could help on trouble shooting 
also is your router doing DHCP?

---

### Post by jongudm on 2010-01-15
> **confusedstingray said:**
> could you post your /etc/network/interfaces file this could help on trouble shooting 
also is your router doing DHCP?

I will post the entire file the moment I get home from work.

The router is doing DHCP.

---

### Post by jongudm on 2010-01-16
Here comes the file at last:

```
# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#      address 192.168.1.2
#      netmask 255.255.255.0
#      network 192.168.1.2
#      broadcast 192.168.1.255
#      gateway 192.168.1.254
```As you can see it contains remnants of a static address this server had before I decided to use DHCP.  I am completely out of ideas by now...

---

### Post by pirateghost on 2010-01-16
> **jongudm said:**
> Here comes the file at last:

```
# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#      address 192.168.1.2
#      netmask 255.255.255.0
#      network 192.168.1.2
#      broadcast 192.168.1.255
#      gateway 192.168.1.254
```As you can see it contains remnants of a static address this server had before I decided to use DHCP.  I am completely out of ideas by now...
the line marked NETWORK is optional, but it should NOT be the same as the IP address that the machine has.  it should end in a 0

---

### Post by jongudm on 2010-01-17
> **pirateghost said:**
> the line marked NETWORK is optional, but it should NOT be the same as the IP address that the machine has.  it should end in a 0

OK, but that line is commented out now.  It was part of the setup for static IP but now I'm trying to use DHCP.

---

### Post by confusedstingray on 2010-01-17
if your setup goes like this 
which is most

your internet connection goes to a router and you machine connects to 
the router ( wired or wireless) 
and from your file it looks like your router ip is 192.168.1.254

so your /etc/network/interfaces file should look like this 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
# address is the ip of the machine 
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
#gateway should be the ip of your router
gateway 192.168.1.254


also make sure you haven't gave 2 machines the same ip 
it happens

---

### Post by jongudm on 2010-01-18
It worked, finally, but it took a rescue mode start with the install disk to repair the /etc/network/interfaces file so I could download updates.  There were some very strange errors that started turning up when I connected a monitor and keyboard to fix this manually but after this rescue mode session and the following updates all seems to work now, with the right address.

Many thanks to everyone who helped and/or read!

---

