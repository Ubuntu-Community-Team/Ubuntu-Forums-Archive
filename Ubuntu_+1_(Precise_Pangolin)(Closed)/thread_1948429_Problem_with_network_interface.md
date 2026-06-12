---
title: "Problem with network interface"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by socka on 2012-03-28
Hey, dont know if this is and bugg, or if it is something else.

But when im trying to install Ubuntu 12.04 from a preseed, my networkconfigurations looks wierd.

this is the only things that is defined in my preseed config regarding network.

```
d-i netcfg/choose_interface select auto

d-i netcfg/dhcp_timeout string 60

d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

```
And when the installation is complete, and i boot up the system. my /etc/network/interface looks likte this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp
# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto
```

One thing is that the 'iface eth0 inet dhcp' looks missplaced, and i have to put a # infront of 'iface eth0 inet6 auto' for it to work.

as i said. this might not be a bug in ubuntu 12.04, maybe it has something to do with the preseed config.

what is your thoughts?

---

