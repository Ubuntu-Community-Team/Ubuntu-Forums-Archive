---
title: "Network setup / bridging / UEC and OpenStack"
date: 2011-02-19
forum: Server Platforms
---

### Post by MarkusThielmann on 2011-02-19
I'm currently experimenting with Ubuntu UEC and OpenStack. With both setups, I seem to be unable to get the network setup. To make it easier, I'll focus on OpenStack:

I installed OpenStack from the stable PPA-archive. It works great, as long as I let OpenStack figure out how to configure its br100 device on his own. But then I don't have any network connectivity at all for the instances.

So I'd need a way to:
- create instances with local IPs (192.168.0.x), which are able to communicate with each other via IP.
- It would be great, if the instances would be able to communicate via the hosts IP. But it's not absolutly neccessary.
- Use euca-associate-address to associate one out of four public IPs my hoster provides for me.

What I have:
- One server which hosts the whole OpenStack installation
- Four public IPs

Here's what my /etc/interfaces file looks after a few tests (far from all tests I made). But since I tend to loose connectivity (using SSH), it's rather unpleasant to just test setups without really knowing what to do.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Public IPs: XXX.XXX.XXX.11 - XXX.XXX.XXX.14

#auto eth0
#iface eth0 inet manual
#       up ifconfig eth0 up

# The primary network interface
#auto br100
#iface br100 inet static
#     bridge_ports    eth0
#     bridge_stp      off
#     bridge_maxwait  0
#     bridge_fd       0
#     address XXX.XXX.XXX.11
#     netmask 255.255.255.0
#     network XXX.XXX.XXX.0
#     broadcast XXX.XXX.XXX.255
#     gateway XXX.XXX.XXX.1
     # dns-* options are implemented by the resolvconf package, if installed
#     dns-nameservers 217.11.48.200 217.11.49.200


# The primary network interface
auto eth0
iface eth0 inet static
        address XXX.XXX.XXX.11
        netmask 255.255.255.0
        network XXX.XXX.XXX.0
        broadcast XXX.XXX.XXX.255
        gateway XXX.XXX.XXX.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers XXX.XXX.XXX.XXX XXX.XXX.XXX.XXX

# Networking for OpenStack Compute 
#auto br100 

#iface br100 inet static 
#    bridge_ports        eth0 
#    bridge_stp           off 
#    bridge_maxwait   0 
#    bridge_fd            0 


```

Any help is appreciated!

---

