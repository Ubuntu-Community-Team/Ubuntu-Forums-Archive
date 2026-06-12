---
title: "Ubuntu 9.04 KVM networking interfaces question"
date: 2009-06-21
forum: Virtualisation
---

### Post by Mogga on 2009-06-21
I'm working on a home mirror of what will hopefully be an eventual physical server deployment. I'm not well versed in network interface setup, bridging, tup,tun,etc. and need some help or prods in the right direction.

I have the server on my home network (192.168.1.0) for eth0 and on it's own network (10.1.0.0) for eth0:1 (one nic)

Here's the /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0 eth0:1

iface eth0 inet static
	address 192.168.1.50
	network 192.168.1.0
	netmask 255.255.255.0
	gateway 192.168.1.254

iface eth0:1 inet static
	address 10.1.0.1
	network 10.1.0.0
	netmask 255.255.0.0
```

So obviously nothing there for the kvm machines yet. That's why I'm here!

What's my next step? Here's my vmbuilder .cfg file for one of the servers (db)

```
[DEFAULT]
arch = amd64
ip = 10.1.0.3
hostname = db
domain = dshng.net
dest = /var/lib/libvirt/images
part = db.partition
user = user
name = user
pass = default
tmpfs = -
firstboot = db_boot.sh
firstlogin = db_login.sh
bridge = br0
mac = 00:11:22:33:44:33

[ubuntu]
suite = jaunty
flavour = virtual
addpkg = mysql-server, mysql-client, dbconfig-common, unattended-upgrades, acpid

[kvm]
libvirt = qemu:///system
```

Now it will be very easy to linkslap me... [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)
but I've read and re-read that and I need some help with my setup that has two networks involved. I know it's easy but I'm not well versed in the networking side of things.

Thanks for any help.

---

