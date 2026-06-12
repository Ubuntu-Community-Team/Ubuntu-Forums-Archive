---
title: "Networking Configuration w/ external and internal nics"
date: 2006-10-19
forum: Server Platforms
---

### Post by sud0n1m on 2006-10-19
Im hoping someone can help. I have 2 nics in my server. One is connected to my t1, the other is connected to my internal router.  I have my websites configured so that my main website is configured to go over the public ip and the intranet only goes to the private ip.

The problem I am having is with accessing the internet from the server. If I enable the gateway as the internal gateway, my public site is not accessible...

How do I configure this so it wont mess up and the networking will work properly?

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The private network interface
auto eth0
iface eth0 inet static

        address 192.168.102.25
        netmask 255.255.255.0
#       broadcast 192.168.102.255
        gateway 192.168.102.200

auto eth0:0
iface eth0:0 inet static
address 192.168.102.26
netmask 255.255.255.0
#broadcast 192.168.102.255

auto eth1
iface eth1 inet static
address 72.xxx.xxx.228
netmask 255.255.255.248
#broadcast 72.xxx.xxx.255
gateway 72.xxx.xxx.225

auto eth1:0
iface eth1:0 inet static
address 72.xxx.xxx.229
netmask 255.255.255.248
#broadcast 72.xxx.xxx.255
#gateway 72.xxx.xxx.225
```

---

