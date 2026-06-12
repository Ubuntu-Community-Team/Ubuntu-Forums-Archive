---
title: "br0 for kvm is not working on Hardy"
date: 2008-08-04
forum: Server Platforms
---

### Post by Brazen on 2008-08-04
I just did a fresh install and update of Ubuntu Server 8.04.  Following the server documentation, I'm changing my network config so I can have a bridge interface.  The network works fine by default, but when I change to the following configuration, I get an error:

--------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto br0
iface br0 inet static
       address 192.168.5.18
       network 192.168.0.0
       netmask 255.255.248.0
       broadcast 192.168.7.255
       gateway 192.168.3.1
       bridge_ports eth0
       bridge_fd 9
       bridge_hello 2
       bridge_maxage 12
       bridge_stp off
--------------------------------

The error I get is a bunch of lines saying:
"br0:  ERROR while getting interface flags:  No such device"
and then one final line saying:
"Failed to bring up br0."

Any ideas?

---

### Post by santran.cedric on 2008-10-02
sudo apt-get install bridge-utils && sudo /etc/init.d/networking restart

---

