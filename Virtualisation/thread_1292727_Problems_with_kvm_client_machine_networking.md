---
title: "Problems with kvm client machine networking"
date: 2009-10-16
forum: Virtualisation
---

### Post by tenmillionmilesaway on 2009-10-16
Hi,

I have a host machine, with a static ip, and I have set up a network bridge (br0), which all seems to be working fine.
I have a virtual machine running with with qemu/kvm/libvert, connected to br0 and I need to give this a static ip address too.

Host network conf:

```

# Loopback device:
auto lo
iface lo inet loopback

# device: eth0
auto eth0
iface eth0 inet manual

# bridge br0
auto br0
iface br0 inet static
  address   xxx.xxx.xxx.149
  broadcast xxx.xxx.xxx.191
  netmask   yyy.yyy.yyy.192
  gateway   xxx.xxx.xxx.129
  bridge_ports eth0
  bridge_stp off
  bridge_maxwait 5

# default route to access subnet
up route add -net xxx.xxx.xxx.128 netmask yyy.yyy.yyy.192 gw xxx.xxx.xxx.129 eth0

```

VM network conf:

```

auto lo
iface lo inet loopback

# device: eth0
auto  eth0
iface eth0 inet static
  address   xxx.xxx.xxx.186
  broadcast xxx.xxx.xxx.191
  netmask   yyy.yyy.yyy.192
  gateway   xxx.xxx.xxx.129


```


Host can ping vm and vm can ping host just fine.

However I am having less success both accessing the external world from the vm and accessing the vm from the external world.

I have managed to successfully ping the vm from the outside world, and I have manged to ping the gateway from the vm, but this seems to work intermittently.  I haven't managed to do any domain name resolution from the vm (cannot ping [www.google.com](www.google.com) for example)

I dont know what I am missing or doing wrong, any ideas anyone?

---

### Post by tenmillionmilesaway on 2009-10-16
After playing about some more, it seems that if I do this
```

sudo route add default gw xxx.xxx.xxx.149

```
ie the ip address of my host machine, then everything works fine, except I cannot ping the actual gateway machine which is xxx.xxx.xxx.129.

This isn't really an issue for me, however I do think that it is an indication that something still isnt 100%

btw, id added the route add command into my /etc/network/interfaces like this:
```

  up route add default gw xxx.xxx.xxx.149

```

---

