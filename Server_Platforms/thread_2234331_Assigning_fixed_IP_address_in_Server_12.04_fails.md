---
title: "Assigning fixed IP address in Server 12.04 fails"
date: 2014-07-14
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-07-14
Hi all

In [http://ubuntuforums.org/showthread.php?t=1869754]("http://ubuntuforums.org/showthread.php?t=1869754") a solution was to>  Rightly or wrongly decided to disable the Network Manager with

```
sudo apt-get purge network-manager network-manager-gnome
```This fails in Server 12.04 LTS.

Normally the IP address for this server is assigned in the router, but the power supply is subject to surges and the settings can be lost.

Any workarounds, please?

TIA

---

### Post by nerdtron on 2014-07-14
Post number 4 on your links provides the correct way to setup a static ip address on a server.

Enter the correct IP details on the /etc/network/interfaces file on your server. Be careful not to have any typos.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.49
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```

Then restart the interfaces:
```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by ChrisRChamberlain on 2014-07-15
nerdtron 

Many thanks for posting your reply with corrected code.

Would this also apply to server 14.04 LTS, please?

---

### Post by nerdtron on 2014-07-15
Yes, the same file should be edited. Just change the required entries on the IP address block.
And "eth0" will most likely be "em0" on your server so be sure to change that also. To be sure what network interface is currently in use, try the command "ifconfig" and you'll see the correct interface.
If it is "em0", change the interface name in the ifdown and ifup commands to apply the static address.

---

### Post by ChrisRChamberlain on 2014-07-15
nerdtron

Many thanks for posting the code for both Server 12.04 and Server 14.04.

---

