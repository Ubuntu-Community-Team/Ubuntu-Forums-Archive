---
title: "Server has static IP, picks up DHCP anyway"
date: 2011-01-31
forum: Server Platforms
---

### Post by kchakrak on 2011-01-31
Right so I have an Ubuntu 10.04 server running DHCP, Bind9 and Kerio with a static IP of 10.0.0.1. 

The problem I'm experiencing is that 3 times in 20 minutes it has picked up a DHCP address from it's own DHCP server. I have never seen this and no idea how to tackle a problem, help please!

Thanks in advance

---

### Post by turbine2 on 2011-01-31
Take a look in /etc/networks for a file called interfaces. It should look something like this:-
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo eth0
iface lo inet loopback
# The primary network interface
iface eth0 inet **static**
        address [B]10.0.0.1
[/B]        netmask 255.0.0.0
        broadcast 10.0.0.255
        network 10.0.0.0

The items in bold are the ones you're looking for.

---

### Post by kchakrak on 2011-01-31
Yep, thats how I've configured it, every other time that's been enough but for some reason it's assigning itself 10.0.0.103.

I've got round it for now by putting DHCP somewhere else but it's far from ideal, it has however meant the users can get on with their work while I find the sure.

The eth0 extract from my server:

# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0
gateway 10.0.0.254
network 10.0.0.0
broadcast 10.0.0.255

---

### Post by sh1ny on 2011-01-31
See if there's a dhclient process running. If it is - KILL IT ! :D

---

### Post by kchakrak on 2011-01-31
I found this after doing a ps aux

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

Is that what you mean? If so why would it not have stopped when the DHCP server was started? Bit confused. I'm LPI level 1 qualified but haven't dealt with 10.04 in a production environment all that much.

---

### Post by turbine2 on 2011-01-31
ignore, error

---

### Post by sh1ny on 2011-02-04
> **kchakrak said:**
> I found this after doing a ps aux

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

Is that what you mean? If so why would it not have stopped when the DHCP server was started? Bit confused. I'm LPI level 1 qualified but haven't dealt with 10.04 in a production environment all that much.

I haven't even read the books that describe what's in LPI level 1. It does not matter :P

Things behave like this :

1. You install a server and set it up ( initially ) to get IP over dhcp
2. You decide what the static ip for that server would be and change /etc/network/interface to have a definition of the interface required, stating "static" and all that jazz.
3. You restart networking with /etc/init.d/networking restart or service networking restart
4. Some time later your static IP is gone and you again get ip from dhcp.

As you saw , there's still a dhclient running in the background, and he does not care if it says "static" in your interfaces file.
2 things you can do to fix it :

a. Kill the dhclient
b. Reboot the machine after you're done setting up the static ip.

Regards,

---

### Post by cmcbeth on 2011-02-16
kchakrak, did the solutions sh1ny suggested resolve your issue?  I am having an identical issue and was curious if your issue has been resolved.
 
Thanks

---

### Post by kchakrak on 2011-02-24
Well I ended up looking for the dhclient config and commenting it all out if I remember rightly, though I'll double check my notes. I think sh1ny's post hit the spot. Hope this helps.

---

