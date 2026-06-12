---
title: "Configuring Network with Multiple NICs"
date: 2011-11-10
forum: Server Platforms
---

### Post by Major7up on 2011-11-10
I'm sure that the question that I am about to ask has been covered somewhere but I am not certain what to search for exactly so please forgive my rookie question:

I have installed Ubuntu 11.10 Server 64-bit and I am trying to figure out how to configure my network properly. My server has two integrated nics and I have 5 Static IP's which I want to assign to one of those and the other I want to connect to the local network. I have been successful in either getting one external static IP configured on one nic and the other with a static IP on the local network, or, getting all 5 external static ips configured on one nic and nothing on the other. I am uncertain what I doing incorrectly or what to search goolge/forums for to learn the answer. If anyone understands what I am trying to explain, can you kindly enlighten me or please direct me to what (or what terms) it is that I should search for to find out?

My current /etc/network/interfaces file: (xx = external IP, yy = local ip)

auto lo eth0 eth0:0
iface lo inet loopback

iface eth0 inet static
  address xx.xx.xx.xx
  netmask 255.255.255.248
  gateway xx.xx.xx.xx

iface eth0:0 inet static
   address xx.xx.xx.xx
   netmask 255.255.255.248
   gateway xx.xx.xx.xx
 
iface eth0:1 inet static
   address xx.xx.xx.xx
   netmask 255.255.255.248
   gateway xx.xx.xx.xx
 
iface eth0:2 inet static
   address xx.xx.xx.xx
   netmask 255.255.255.248
   gateway xx.xx.xx.xx
 
iface eth0:4 inet static
   address xx.xx.xx.xx
   netmask 255.255.255.248
   gateway xx.xx.xx.xx
 


Why can't I add:
iface eth1 inet static
   address yy.yy.yy.yy
   netmask 255.255.255.0
   gateway yy.yy.yy.yy
   for the local network?


It works if I remove all of the virtual interfaces and only have eth0 and eth1...

Does this make sense?

---

### Post by Major7up on 2011-11-10
I was able to discover the solution with more trial and error using this:

auto lo eth0 eth0:0 eth0:1 eth0:2 eth0:3 eth0:4 eth1
iface lo inet loopback

iface eth0 inet static
        address xx.xx.xx.xx
        netmask 255.255.255.248
        gateway xx.xx.xx.xx

iface eth0:0 inet static
        address xx.xx.xx.xx
        netmask 255.255.255.248
        gateway xx.xx.xx.xx

iface eth0:1 inet static
        address xx.xx.xx.xx
        netmask 255.255.255.248
        gateway xx.xx.xx.xx

iface eth0:2 inet static
        address xx.xx.xx.xx
        netmask 255.255.255.248
        gateway xx.xx.xx.xx

iface eth0:3 inet static
         address xx.xx.xx.xx
         netmask 255.255.255.248
         gateway xx.xx.xx.xx
 
 iface eth0:4 inet static
         address xx.xx.xx.xx
         netmask 255.255.255.248
         gateway xx.xx.xx.xx
 
 iface eth1 inet static
        address yy.yy.yy.yy
        netmask 255.255.255.0
        broadcast yy.yy.yy.1
        network yy.yy.yy.yy.0


Seems like I needed to add that network and broadcast element.

---

### Post by Jonathan L on 2011-11-11
Hi Major7

The configuration of different interfaces only interferes with each other when the addresses overlap in some way.  To me it looks like you were doing it exactly the right way, but I wonder what the addresses were.  My guess is there was a different problem such as a typo or simillar: sadly so easily done.

Your sample is a little strange.
```
iface eth1 inet static
        address yy.yy.yy.yy
        netmask 255.255.255.0
        broadcast [COLOR=Red]yy.yy.yy.1[/COLOR]
        network [COLOR=Red]yy.yy.yy.yy.0[/COLOR]
```The broadcast address is almost certain to cause problems (other computers not hearing the broadcasts) and the network address appears to be invalid (5 octets).

My suggestion would be to try ifconfig manually until you get a configuration that works, then copy its details to /etc/network/interfaces.

Hope that's helpful

Kind regards,
Jonathan.

---

### Post by Major7up on 2011-11-12
You are correct about the 5 octets, that was a typo on my part when I entered the reply here. It seems to work correctly as I have it setup now as shown above except for the 5 octets bit. It's definitely a learning experience and I plan to expand my knowledge of networking in general as it is presently at only a novice level. Thanks for the reply though, I appreciate it :)

---

### Post by spynappels on 2011-11-14
It looks like you configured a Gateway on the LAN interface, which was not required. I'll bet the gateway was the same on all your logical interfaces, so essentially you have only one gateway, but when you added another on the LAN interface, that would have messed up the settings.

Ideally, you would set one of your logical interfaces with a gateway and leave the gateway line out of all others. If a specific source IP (one of your logical interfaces) for a specific reason, you'd normally add a static route for that.

Glad you got it working anyway.

---

