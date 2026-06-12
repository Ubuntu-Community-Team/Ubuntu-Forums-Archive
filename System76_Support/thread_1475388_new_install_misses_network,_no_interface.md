---
title: "new install misses network, no interface"
date: 2010-05-06
forum: System76 Support
---

### Post by idella on 2010-05-06
I have a new install and I am quite surprised it just misses networking**.**  That is, **NO** networking.

ifconfig comes up with inly lo.  Nothing else, most primal.

It should use dhcp to connect, bit it fails to create the eth0 interface.
Such a fundamental flaw is one I can't work on. Forget looking in network manager in the desktop, that's still being installed, but it's no help.
I've checked the basic files in etc against karmic.


idella@squeeze:~$ cat /mnt/lucid/etc/network/interfaces 
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp
iface wlan0 inet dhcp

This one had me puzzled.  I was attempting to bring it up as a vm, and it just rejected the line

allow-hotplug eth0.

It accepted hotplug eth0, then didn't do it.


idella@squeeze:~$ cat /mnt/lucid/etc/networks
# symbolic names for networks, see networks(5) for more information
loopback        127.0.0.0
link-local 169.254.0.0

idella@squeeze:~$ cat /mnt/lucid/etc/resolv.conf
nameserver 61.9.242.33
nameserver 61.9.226.33

Any help appreciated.

---

### Post by thomasaaron on 2010-05-07
Run...

sudo gedit /etc/network/interfaces

In the resulting text editor, put a comment (#) in front of each of these lines...

allow-hotplug eth0
iface eth0 inet dhcp
iface wlan0 inet dhcp

...so that they look like this...

#allow-hotplug eth0
#iface eth0 inet dhcp
#iface wlan0 inet dhcp

Leave these lines...

auto lo
iface lo inet loopback

...alone.



Save it. Reboot.

Did that fix it?

---

