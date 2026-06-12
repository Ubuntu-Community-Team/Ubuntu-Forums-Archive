---
title: "Networking problem"
date: 2017-10-28
forum: Virtualisation
---

### Post by satimis on 2017-10-28
Hi all,

Host - Ubuntu 16.04 desktop
Guest - Ubuntu 16.04 desktop
Virtualizer - KVM


Host
====
&#10219; ifconfig```

enp2s0    Link encap:Ethernet  HWaddr f0:79:59:65:2f:bb  
          inet addr:192.168.8.3  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::6c58:d5fc:124f:c287/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5715 (5.7 KB)  TX bytes:11227 (11.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1518290 (1.5 MB)  TX bytes:1518290 (1.5 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:be:53:09  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:320 (320.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:be:53:09  
          inet6 addr: fe80::fc54:ff:febe:5309/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3935 (3.9 KB)

```

&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```


Guest
=====
$ ifconfig```

ens3      Link encap:Ethernet  HWaddr 52:54:00:be:53:09  
          inet addr:192.168.122.122  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::75fb:5622:6ea2:e393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:28031 txqueuelen:1000
          RX bytes:13125597 (13.1 MB)  TX bytes:906342 (906.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148687 (148.6 KB)  TX bytes:148687 (148.6 KB)

```

$ cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```


Why eth0 missing?  Whether it is renamed to enp2s0 ?

How to get eth0 back?

Please advise.  Thanks

Besides whether br0 is now renamed to ens3?

Regards
satimis

---

### Post by TheFu on 2017-10-29
In 16.04 and later builds, the smart guys at systemd project decided to solve a problem that 1% of the world is having with multiple NICs.  We are lucky to also get that unwanted/unneeded solution which has the effect of making ethernet device names unique.

You are welcome.

There is a grub setting to tell the kernel at boot to use the old style ethernet naming, but it is best just to get used to the new naming strategy, since it is the default.

If you want br0, then you need settings in the interfaces file on the host to create that bridge.  There are lots of examples on the internet.  The bridge-utils package is where I'd start.

And you might want to know that systemd seems to have issues restarting the network subsystem for non-trivial network setups on Ubuntu. That is what I've seen when using any sort of linux bridges, but I'm just 1 data point.  Most of our VM systems still run 14.04 due to the systemd issues we are still seeing here.

---

### Post by satimis on 2017-10-29
> **TheFu said:**
> In 16.04 and later builds, the smart guys at systemd project decided to solve a problem that 1% of the world is having with multiple NICs.  We are lucky to also get that unwanted/unneeded solution which has the effect of making ethernet device names unique.

You are welcome.

There is a grub setting to tell the kernel at boot to use the old style ethernet naming, but it is best just to get used to the new naming strategy, since it is the default.

If you want br0, then you need settings in the interfaces file on the host to create that bridge.  There are lots of examples on the internet.  The bridge-utils package is where I'd start.

And you might want to know that systemd seems to have issues restarting the network subsystem for non-trivial network setups on Ubuntu. That is what I've seen when using any sort of linux bridges, but I'm just 1 data point.  Most of our VM systems still run 14.04 due to the systemd issues we are still seeing here.
Hi

With following setting on /etc/network/interfaces, now host can access Internet.

&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dns-nameservers xx8.1xx.xx8.xx2 xx9.x7x.xx8.9xx

# The primary network interface
auto enp2s0
iface enp2s0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.3
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    enp2s0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

&#10219; ifconfig```

br0       Link encap:Ethernet  HWaddr f0:79:59:65:2f:bb  
          inet addr:192.168.8.3  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::f279:59ff:fe65:2fbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1390824 (1.3 MB)  TX bytes:571481 (571.4 KB)

enp2s0    Link encap:Ethernet  HWaddr f0:79:59:65:2f:bb  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1460108 (1.4 MB)  TX bytes:571481 (571.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12158 (12.1 KB)  TX bytes:12158 (12.1 KB)

```

I have performed following steps:```


$ virsh net-destroy default
$ virsh net-undefine default

```
to remove virbr0 which is NAT

Now I couldn't start the previously installed guests with following warning popup:```

Error starting domain: Network not found: no network with matching name
'default'

```

I have reinstalled following packages```

qemu-kvm libvirt-bin bridge-utils virt-manager

```
but it didn't help.

Newly installed guest doesn't have this problem.  I just installed Debian 9.1 Gnome desktop.  I can start it to set static IP

$ sudo ifconfig
[sudo] password for satimis:```

ens3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.2  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::5054:ff:fec7:170a  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:c7:17:0a  txqueuelen 1000  (Ethernet)
        RX packets 50  bytes 3958 (3.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 85  bytes 8500 (8.3 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 198

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 180  bytes 14076 (13.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 180  bytes 14076 (13.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

It is quite strange to me that I must run sudo to start ifconfig on Debian.

I have posted my problem on the mailing list of KVM, waiting for some help there how to restore "default".  In the worst case I just delete the previous installed guests and reinstall them.  There are ONLY four of them;```

antergos 17.10
centos7
fedora workstation ostree
ubuntu 16.04 desktop

```

satimis

---

### Post by KillerKelvUK on 2017-10-29
Hey satimis, any guests that you create before you made these networking changes will need their guest configurations updating to incorporate the new bridge you've created.  The reason for the error message is because the virtual network adapters in the guests are attempting to connect to the NAT bridge which you've now removed.  I suggest (using virt-manager) you remove the network adapters from the affected guests, then add new network adapters and make sure it is configured to connect to your new bridge, in the drop down menu you *might* see your bridge listed but if not choose "shared device" and in the text entry box type "br0".

---

### Post by TheFu on 2017-10-30
No need to reinstall the guests.  Just check/ recreate the XML files that describe the virtual machine that each VM storage is tied into. virsh edit can do that if you don't/can't fix the issues through virt-manager.  virt-manager provides access to about 20% of the libvirt-supported settings. That is the nature of GUIs.  virsh edit - 100% access.

---

### Post by satimis on 2017-10-30
> **TheFu said:**
> No need to reinstall the guests.  Just check/ recreate the XML files that describe the virtual machine that each VM storage is tied into. virsh edit can do that if you don't/can't fix the issues through virt-manager.  virt-manager provides access to about 20% of the libvirt-supported settings. That is the nature of GUIs.  virsh edit - 100% access.
Hi,

Thanks for your advice.

I have been playing around on Virt-Manager but unfortunately I couldn't find a solution.

I found following document:
2.57. net-create
[https://libvirt.org/sources/virshcmdref/html/sect-net-create.html](https://libvirt.org/sources/virshcmdref/html/sect-net-create.html)

But I couldn't resolve the Examples there;```

virsh # net-create /root/examplenetwork.xml

```

The file deleted by me was "default".

Do you have any suggestion?

Regards
satimis

---

### Post by TheFu on 2017-10-30
> **satimis said:**
> 
Do you have any suggestion?

Nope. Never used that.
I do all network modification stuff outside the virtualization tools and only point at a bridge or PCI passthru NIC for specific VMs.  

If I had 10Gbps or 40Gbps networks, then I'd use openswitch instead of normal bridge-utils for performance reasons.  You can use openswitch for any type of network, but normal Linux bridges perform really well at GigE speeds already, so the added complexity of openswitch isn't necessary.

---

