---
title: "can't start lxc container in oneiric"
date: 2011-10-20
forum: Server Platforms
---

### Post by xlyz on 2011-10-20
setting up a virtualbox server with oneiric.

minimal server install + openssh

loggin in

install lxc following this guide:
[https://dev.launchpad.net/Running/LXC](https://dev.launchpad.net/Running/LXC)

when I lxc-start my test lxc container I get:

```
lxc-start: No such file or directory - failed to mount '/var/lib/lxc/test/rootfs/' on '/usr/lib/lxc/root/none'
lxc-start: failed to setup the mounts for 'test'
lxc-start: failed to setup the container
lxc-start: invalid sequence number 1. expected 2
lxc-start: failed to spawn 'test'
lxc-start: Device or resource busy - failed to remove cgroup 'sys/fs/cgroup/cpuset/test'
```any idea what's wrong?

EDIT:

cat /var/lib/lxc/test/config ```

lxc.network.type=veth
lxc.network.link=virbr0
lxc.network.flags=up
lxc.arch=i686
lxc.utsname = test

lxc.tty = 4
lxc.pts = 1024
lxc.rootfs = /var/lib/lxc/test/rootfs
lxc.mount  = /var/lib/lxc/test/fstab
lxc.arch = i686

lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
#lxc.cgroup.devices.allow = c 4:0 rwm
#lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm
#fuse
lxc.cgroup.devices.allow = c 10:229 rwm

```cat /etc/fstab

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9f625d3f-d4c5-4ba6-b53f-69f585015aa8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=85542c7d-2342-4e80-a0af-4a831bb2c039 none            swap    sw              0       0
tryin creating /usr/lib/lxc/root/none

> $ sudo mkdir -p /usr/lib/lxc/root/none
$ lxc-start -n test
lxc-start: failed to cap_get_flag: Invalid argument
lxc-start: failed to create vethhn27TC-vethtu4xs6 : Operation not permitted
lxc-start: failed to create netdev
lxc-start: failed to create the network
lxc-start: failed to spawn 'test'
lxc-start: Permission denied - failed to remove cgroup '/sys/fs/cgroup/cpuset/test'


cat /var/lib/lxc/test/fstab
> proc            /var/lib/lxc/test/rootfs/proc         proc    nodev,noexec,nosuid 0 0
sysfs           /var/lib/lxc/test/rootfs/sys          sysfs defaults  0 0
 /var/lib/lxc/test/rootfs/ none bind 0 0


---

### Post by xlyz on 2011-10-20
fixed
posting the solution for others to see:

step 6 of the howto:
sudo lxc-create -t ubuntu -n lucid-test-lp -f /etc/lxc/local.conf -- -r lucid -a i386 -b robertc

you should change robertoc at the end with a valid user on your machine.
that's it.

---

