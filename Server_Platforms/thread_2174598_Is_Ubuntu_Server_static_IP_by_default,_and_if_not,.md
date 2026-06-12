---
title: "Is Ubuntu Server static IP by default, and if not, how can I make it so?"
date: 2013-09-15
forum: Server Platforms
---

### Post by icebox83 on 2013-09-15
Is Ubuntu Server set up as static IP by default, and if not, how can I change it to static IP? Do I need to do anything else, e.g. change settings on my router? I'm new to this command line stuff, so please be gentle :)

---

### Post by trundlenut on 2013-09-15
You are given the option to choose the networking setup when going through the installation.  I think the default is to use DHCP though.

---

### Post by nerdtron on 2013-09-15
```
cat /etc/network/interfaces
```
If you see a dhcp entry, then your server IP is DHCP.
If you see a static entry, the your server IP is statically configured.

You need to edit /etc/network/interfaces file if you want a static IP.
```
sudo nano /etc/network/interfaces
```
Here's a sample:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.5
    network 192.168.1.0
    netmask 255.255.255.0
    gateway 192.168.1.1
    broadcast 192.168.1.255
    dns-nameservers 192.168.1.1 8.8.8.8
```
Don't erase the "auto lo" entry. It is needed by the system.

After editing, save, and exit nano. Restart your network interface.
```
sudo ifdown eth0 && sudo ifup eth0
```
Then confirm that the changes were applied.
```
ifconfig
```

---

