---
title: "Getting confused with Interfaces file"
date: 2009-01-06
forum: Server Platforms
---

### Post by happyhacker on 2009-01-06
This is my file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
#gateway 192.168.0.1
#network 192.168.1.0
#broadcast 192.168.1.255
gateway 192.168.1.254

At the moment my server is connected to 192.168.1.x (my home)network. With the arrangement shown I can access my server from XP browser (webmin, etc.) on my home network. My work network is 192.168.0.x. I often bring the server home to learn more about ubuntu and configuration. So I swap the gateway over as appropriate. If I change network or broadcast access fails.

Is there a way of configuring this file (or something else) so it will work at both locations without changing it?

PS, how do I restart the interfaces file without restarting the server?

---

### Post by iponeverything on 2009-01-06
> **cantthinkofanickname said:**
> This is my file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
#gateway 192.168.0.1
#network 192.168.1.0
#broadcast 192.168.1.255
gateway 192.168.1.254

At the moment my server is connected to 192.168.1.x (my home)network. With the arrangement shown I can access my server from XP browser (webmin, etc.) on my home network. My work network is 192.168.0.x. I often bring the server home to learn more about ubuntu and configuration. So I swap the gateway over as appropriate. If I change network or broadcast access fails.

Is there a way of configuring this file (or something else) so it will work at both locations without changing it?

PS, how do I restart the interfaces file without restarting the server?


Just change your netmask 255.255.252.0 and your broadcast to 192.168.3.255

your interfaces file should look like this:


```
iface lo inet loopback

# The primary network interface
auto eth0

iface eth0 inet static
address 192.168.0.2
netmask 255.255.252.0
network 192.168.0.0
broadcast 192.168.3.255
gateway 192.168.0.1

```

Then just change your gateway depending on if you are at work or at home.
```

route del default
route add default gw <gateway>

```

Restart the interfaces file with:
```

/etc/init.d/network restart

```

---

### Post by koenn on 2009-01-06
> **iponeverything said:**
> Just change your netmask 255.255.252.0 and your broadcast to 192.168.3.

I'm not so sure this is a good idea. It might work, but it will cause network trouble sooner or later.
Assuming there's more than one host on the home network and these need to connect to this server, the home network hosts will still be in a 192.168.1.0/255.255.255.0 network, so to them, a host with 192.168.0.x will be in an other network, and they'll try to connect to it through their default router. 
A similar but oposite problem may oocur when the server is on the work LAN and needs to reply to a host on an other network. If the host address falls within the 192.168.0.0/255.255.252.0 range, the server won't know this has to be routed.

It's probably better to maintain 2 interfaces files, one for each network - say /etc/network/interfaces.home and /etc/network/interfaces.work
then you could have a script, say /usr/local/bin/setnetwork, that copies the desired file to /etc/network/interfaces.
something like 
```

#!/bin/bash
cp -pv /etc/network/interfaces.$1 /etc/network/interfaces
/etc/init.d/networking restart

```
usage:
setnetwork home
or
setnetwork work

If you can think of a way to let the server discover where it is, you could probably automate this. Eg: try interfaces.work, ping a local address (the default router ?), if it doesn't work, assume we're on the wrong network and try the other one. Just thinking out loud. 

That said, it strikes me as an odd idea to be moving servers around and use a 'work' server "to learn more about ubuntu and configuration." Maybe you should consider setting up a separate server at home, or even a few (eg with vmware or so). Or leave that server where it is and connect to it remotely (vpn, ssh, ...)

---

### Post by happyhacker on 2009-01-06
Thanks for your detailed replies. I have taken it home for the holidays as I volunteer at work for 1 day a week and need more time.

I am able to see the server from windows and have samba shares. The problem at the moment is that backuppc using either smb or rsync fails. Rsync times out. I can ping my XP 192.168.1.66 from the server but not it's name "lt7" (not found) and I wonder if this is the problem. My router shows the server on 192.168.0.2.

Is ther another way of checking access to XP from the server.

---

