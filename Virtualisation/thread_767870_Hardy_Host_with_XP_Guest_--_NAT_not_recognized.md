---
title: "Hardy Host with XP Guest -- NAT not recognized"
date: 2008-04-26
forum: Virtualisation
---

### Post by insert_name_here on 2008-04-26
I just updated to Hardy and figured it would be a nice time to switch from VMware to Virtualbox for running XP.  I really like the Seamless Mode, etc.

However, I can't get the NAT to work in Vbox.  A VMware Accelerated NAT Device or something shows up in my XP Device Manager, but otherwise, I see no traces of the NAT I've set up in Vbox.  (I set the NAT up in Vbox by going to Network, connecting the cable, using the first and second card options and a random MAC address.)

Any ideas on how to make it work?   Is there a module or process I need to have running that might not be running?  Do I have to install something in the host?

(If it's relevant, I tried using the third network card option - the Intel one - but it gave an error when I selected it.  If you think that could be useful, tell me and I'll copy over the error message.)

---

### Post by seamuso on 2008-04-26
You could set up a bridge connection .. [http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/)

Those instructions show how to set up a bridge with a static IP for the host machine. You can add up to 4 taps to the bridge.

from my /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
# address 192.168.1.17
# netmask 255.255.255.0
# gateway 192.168.1.1

auto tap1
iface tap1 inet manual
tunctl_user seamuso
uml_proxy_arp 192.168.1.17
uml_proxy_ether eth0

auto tap2
iface tap2 inet manual
tunctl_user seamuso
uml_proxy_arp 192.168.1.17
uml_proxy_ether eth0


auto br0
iface br0 inet static
        address 192.168.1.17
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge-ports eth0 tap1 tap2
        bridge-maxwait 0

```

all I have to do to add another tap to my /etc/network/interfaces is:
```

auto tap3
iface tap3 inet manual
tunctl_user seamuso
uml_proxy_arp 192.168.1.17
uml_proxy_ether eth0

```

change
```

bridge-ports eth0 tap1 tap2

```  to ```

bridge-ports eth0 tap1 tap2 tap3
```
and restart networking

.. lather rinse repeat up to tap4

---

