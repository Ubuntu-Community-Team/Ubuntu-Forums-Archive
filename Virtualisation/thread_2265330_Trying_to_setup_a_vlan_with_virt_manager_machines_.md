---
title: "Trying to setup a vlan with virt manager machines can't get to the internet."
date: 2015-02-14
forum: Virtualisation
---

### Post by pepsifx357 on 2015-02-14
I don't know if this post should be in the cloud section or virtualization section, but I'm trying to setup a MAAS server and a bunch of nodes with Virt-Manager and I want to put this "cloud" on a seperate network, because of the need for MAAS to control dhcp.  

I've tried to put them on a vlan called cloud, with the network 10.0.0.0/24, but I don't think I know enough about kvm networking, or networking for that matter to figure out how to get the vlan machines to access the internet.  My physical network is on 192.168.1.0/24 network, with a seperate dhcp/dns server at 192.168.1.80, and the gateway is at 192.168.1.254. Can anyone kinda walk me through the steps, via virt-manager, on how to create a vlan, with no dhcp server, where the machines will be able to connect to the internet?  I could probably figure out how to get MAAS working from there.  OR maybe I'm going about it the wrong way.  I'm really not too sure.

Thanks

---

### Post by TheFu on 2015-02-14
I found the networking in virt-manager (i.e. libvirt) to be terrible (slow, prone to disconnects).  Just use the normal Linux networking facilities on the hostOS to create whatever you need, then hook that up to the VMs.  Inside libvirt, the only thing I do network-wise is to specify the bridge I created elsewhere.  

I don't use vlans - most people seem to think that vlans help security - that is not true.  physical separation is necessary. vlan tags are just "suggestions", which can easily be ignored.

---

### Post by pepsifx357 on 2015-02-14
Yeah, vlans was something I was used to in virtualbox.  I didn't know if it worked the same way in libvirt.  What kind of settings would I need in /etc/network/interfaces? I have a bridge setup right now.

I tried this with no luck:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.72
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
	dns-namesevers 192.168.1.80 8.8.8.8
auto br0
iface br0 inet static
        address 192.168.1.73
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

auto eth0:1
iface eth0:1 inet static
	address 10.1.1.1
	netmask 255.255.255.0
	gateway 10.1.1.1

auto br1
iface br1 inet static
        address 10.1.1.2
        network 10.1.1.0
        netmask 255.255.255.0
        broadcast 10.1.1.255
        gateway 10.1.1.1
        bridge_ports eth0:1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

I ended up with this:

```
ben@KVM-Host:~$ sudo ifup br1
device eth0:1 is already a member of a bridge; can't enslave it to bridge br1.
RTNETLINK answers: File exists

```

Actually I think I have a mess of a network right now.  Here's my network info:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
    link/ether 60:a4:4c:62:f0:15 brd ff:ff:ff:ff:ff:ff
    inet 10.1.1.1/24 brd 10.1.1.255 scope global eth0:1
       valid_lft forever preferred_lft forever
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 60:a4:4c:62:f0:15 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.73/24 brd 192.168.1.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::62a4:4cff:fe62:f015/64 scope link 
       valid_lft forever preferred_lft forever
4: lxcbr0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default 
    link/ether 6e:c6:ce:1b:6d:b1 brd ff:ff:ff:ff:ff:ff
    inet 10.0.3.1/24 brd 10.0.3.255 scope global lxcbr0
       valid_lft forever preferred_lft forever
    inet6 fe80::6cc6:ceff:fe1b:6db1/64 scope link 
       valid_lft forever preferred_lft forever
5: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:d7:a4:ab brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fed7:a4ab/64 scope link 
       valid_lft forever preferred_lft forever
6: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:a9:05:7d brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fea9:57d/64 scope link 
       valid_lft forever preferred_lft forever
7: vnet2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:2f:bf:85 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe2f:bf85/64 scope link 
       valid_lft forever preferred_lft forever
8: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default 
    link/ether da:36:94:2d:42:d5 brd ff:ff:ff:ff:ff:ff
    inet 10.1.1.2/24 brd 10.1.1.255 scope global br1
       valid_lft forever preferred_lft forever
    inet6 fe80::d836:94ff:fe2d:42d5/64 scope link 
       valid_lft forever preferred_lft forever
```

br0 works like a champ though.  I have no idea where all the vnets came from.  I can only account for lxcbr0 because I was playing with linux containers.

---

