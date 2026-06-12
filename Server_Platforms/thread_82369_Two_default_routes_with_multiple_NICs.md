---
title: "Two default routes with multiple NICs"
date: 2005-10-26
forum: Server Platforms
---

### Post by gfarrow on 2005-10-26
I have two NICs.  One (external) is configured with a static IP and one (internal) is configured via DHCP on our internal network.  When I reboot the machine I end up with two default routes, one pointing to each NIC.  In order to make the networking function correctly I have to delete the default route pointing to the internal NIC manually after each reboot.  How can I automatically configure things to have a default route added for only the static interface on startup?  

Interfaces file below with IP addresses modified for privacy.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth2
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 11.22.177.236
        netmask 255.255.255.248
        network 11.22.177.232
        broadcast 11.22.177.239
        gateway 11.22.177.233
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 11.180.96.12 11.238.96.12

E45: 'readonly' option is set (add ! to override)             10,1          Top

---

### Post by mlomker on 2005-10-26
The obvious answer is to not use DHCP and assign a static address.  The other option would be to call a script when that interface comes up and have your delete command in that script.

```

iface eth2 inet dhcp
   post-up /pathto/yourscript

```

---

