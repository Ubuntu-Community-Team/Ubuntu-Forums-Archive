---
title: "LXD : how to set USB device to a container"
date: 2016-08-11
forum: Virtualisation
---

### Post by jean-pierre2 on 2016-08-11
Hello,

I had to upgrade from ubuntu 14.04 32bits with lxc to ubuntu 16.04 64bits with lxd.

With LXD, I do not know how to give a USB device to a container.

Previously, I just had to add in config file of the container:
```
lxc.cgroup.devices.allow = c 188:* rwm
lxc.mount.entry = /dev/ttyUSB0  dev/ttyUSB0  none  bind,optional
```

Now, I have no idea of the proper command : lxc config device add <[remote:]container> <name> <type> [key=value]... 

Not found any examples nor doc for this case.

TIA

JP

---

### Post by jean-pierre2 on 2016-08-14
Hi,

First, I read too quickly [https://github.com/lxc/lxd/blob/master/doc/configuration.md](https://github.com/lxc/lxd/blob/master/doc/configuration.md) ...
Secondly, there is no type usb for my lxd version (0.20).

So proper commands are simply (now) :
```
lxc config device add jeedom  rfxcom unix-char path=/dev/ttyUSB0
lxc config device set jeedom  rfxcom  mode 666
```
  
JP

---

### Post by MAFoElffen on 2016-08-14
Follow the Logic: 
LXD is containers, so is removed/abstracted from the hardware. 

There are exceptions. For instance, you can access a shared host directory. Now if that directory just happened to be a Host mounted USB device... Then you would have access to that USB. At least by that Logic.

Now if it an on-going kind of thing, then setup a host directory that the container will use as a host resource. You mount your drives to the directory. That way if a drive is not mapped nor mounted to that directory, the container can still stop... but then would just see and "empty" shared host directory.

The biggest challenge on that is setting the permission on that shared directory so that is can be written to by users of the container. You could set to world, but I lean towards trying to find the "least" permissive to do what is needed.

---

