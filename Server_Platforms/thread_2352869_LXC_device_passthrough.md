---
title: "LXC device passthrough"
date: 2017-02-16
forum: Server Platforms
---

### Post by tessiof on 2017-02-16
**On Ubuntu Server 16.04**

I'm trying to pass this device to a LXC container:
```
tessio@lxc-03:~$ ls -l /dev/sg3
crw-rw---- 1 root tape 21, 3 Feb 16 09:50 /dev/sg3
```

Container config file:

```
# Distribution configuration
lxc.include = /usr/share/lxc/config/ubuntu.common.conf
lxc.arch = x86_64

# Container specific configuration
lxc.rootfs = /var/lib/lxc/bar/rootfs
lxc.rootfs.backend = dir
lxc.utsname = bar

# Network configuration
lxc.network.type = veth
lxc.network.link = lxcbr0
lxc.network.flags = up
lxc.network.hwaddr = 00:16:3e:a5:6f:33

# Allow devices
lxc.cgroup.devices.allow = c 21:3 rwm
```

Inside the container I mknod the device, but it's not fully passed through:

```
root@bar:~# mknod -m 660 /dev/sg3 c 21 3
root@bar:~# udevadm info -n /dev/sg3 -q all
P: /devices/pci0000:00/0000:00:07.0/0000:06:00.0/host2/rport-2:0-2/target2:0:0/2:0:0:1/scsi_generic/sg3
N: sg3
E: DEVNAME=/dev/sg3
E: DEVPATH=/devices/pci0000:00/0000:00:07.0/0000:06:00.0/host2/rport-2:0-2/target2:0:0/2:0:0:1/scsi_generic/sg3
E: MAJOR=21
E: MINOR=3
E: SUBSYSTEM=scsi_generic

```

What's wrong with my config file?

---

