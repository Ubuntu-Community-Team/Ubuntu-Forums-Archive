---
title: "Host and guest Ubuntu Lucid for LXC"
date: 2010-10-13
forum: Virtualisation
---

### Post by narcisgarcia on 2010-10-13
Hello, I'm trying to write a sample procedure for me, but I get an error when trying to run a Linux Container.
I've installed a fresh Ubuntu 10.04 server and then made the following steps to start a LXC container:

```

sudo -i
apt-get update
apt-get install lxc vlan bridge-utils python-software-properties screen debootstrap language-pack-ca
mkdir /var/containers
mkdir /var/cache/debootstrap
apt-get upgrade

```
Created /etc/init.d/lxc with the content recommended at [https://help.ubuntu.com/community/var/containers](https://help.ubuntu.com/community/var/containers) and installed for startup:
```

update-rc.d lxc defaults
invoke-rc.d lxc restart

```

Created a package to cache debootstrap (Known architectures for --arch: i386 amd64)
```

Architecture="i386"
TemplateName="$(lsb_release -is | tr "[:upper:]" "[:lower:]")-$(lsb_release -rs)-$Architecture"
debootstrap --variant=minbase --arch $Architecture $(lsb_release -cs) /tmp/${TemplateName}.tmp
tar -cjf "/var/cache/debootstrap/$TemplateName.tar.bz2" /tmp/${TemplateName}.tmp/
rm -R /tmp/${TemplateName}.tmp

```

Creating a container:
```

ContainerName="myguest"
ContainerIP="192.168.1.1"
mkdir -p /var/containers/$ContainerName/rootfs
cd /var/containers/$ContainerName/rootfs
tar xf /var/cache/debootstrap/ubuntu-10.04-i386.tar.bz2
cd /var/containers
echo "$ContainerName" > /var/containers/$ContainerName/rootfs/etc/hostname
echo "127.0.0.1 localhost $ContainerName" > /var/containers/$ContainerName/rootfs/etc/hosts
echo "$ContainerIP $ContainerName" >> /var/containers/$ContainerName/rootfs/etc/hosts

```

Configurations inside:
```

chroot /var/containers/$ContainerName/rootfs
apt-get install --force-yes -y gpgv
apt-get update
apt-get install -y language-pack-ca
locale-gen ca_ES.UTF-8
update-locale LANG="ca_ES.UTF-8" LANGUAGE="ca_ES.UTF-8" LC_ALL="ca_ES.UTF-8"
apt-get install -y adduser apt-utils console-setup iproute nano netbase openssh-blacklist openssh-blacklist-extra openssh-server iputils-ping sudo
rm /etc/mtab
ln -s /proc/mounts /etc/mtab
exit

```

Creating a file "/var/containers/myguest/fstab" with this content:
```

none /var/containers/myguest/rootfs/dev/pts devpts defaults 0 0
none /var/containers/myguest/rootfs/proc proc defaults 0 0
none /var/containers/myguest/rootfs/sys sysfs defaults 0 0
none /var/containers/myguest/rootfs/var/lock tmpfs defaults 0 0
none /var/containers/myguest/rootfs/var/run tmpfs defaults 0 0
/etc/resolv.conf /var/containers/myguest/rootfs/etc/resolv.conf none bind 0 0

```

Creating a config file "/var/containers/myguest/lxc.conf" with this content:
```

lxc.utsname = myguest
lxc.tty = 4
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.name = eth0
lxc.network.mtu = 1500
lxc.network.ipv4 = 192.168.1.1/24
lxc.rootfs = /var/containers/myguest/rootfs
lxc.mount = /var/containers/myguest/fstab
lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 4:0 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
# /dev/pts/* - pts namespaces are "coming soon"
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm

```

Replacing all the content in /var/containers/myguest/rootfs/etc/init/rc-sysinit.conf by:
```

#!/bin/bash
# Whatever is needed to clear out old daemon/service pids from your container
rm -f $(find /var/run -name '*pid')
rm -f /var/lock/apache/*
route add default gw 192.168.1.254
exit 0

```
Execution permissions:
```

chmod a+x /var/containers/$ContainerName/rootfs/etc/init/rc-sysinit.conf

```

Cleaning hardware-related scripts:
```

cd /var/containers/$ContainerName/rootfs/etc/init
rm -f console* control* hwclock* module* mount* network-interface* plymouth* procps* tty{4,5,6}.conf udev* upstart*
cd /var/containers

```

Registering the container:
```

lxc-create -f /var/containers/$ContainerName/lxc.conf -n $ContainerName

```

And the first throuble comes when trying to startup:
```

lxc-start -n $ContainerName

```

This is the result:
```

lxc-start: failed to attach 'vethZgwEGv' to the bridge 'br0'
lxc-start: failed to create netdev
lxc-start: failed to create the network
lxc-start: failed to spawn '/sbin/init'
lxc-start: cgroup is not mounted

```

Forum threads to see also:
[http://ubuntuforums.org/showthread.php?t=1382823](http://ubuntuforums.org/showthread.php?t=1382823)

---

### Post by cpldave on 2011-06-16
Just so anyone else stumbling across this doesn't go round in circles for hours like I did, this is a regression in the Lucid kernel documented here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/790863](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/790863)

I agree with the other comments on that bug; changing the kernel functionality on an LTS release was a massive mistake and the kernel team should be jumping to fix the issue ASAP. Unfortunately it looks like the regression was caused when trying to fix another bug and the team think the LXC affecting bug is less important than the "fixed" bug. I quote "fixed" because disabling functionality to avoid a bug is not fixing it.

I fixed this by rolling back to the previous kernel release.

---

