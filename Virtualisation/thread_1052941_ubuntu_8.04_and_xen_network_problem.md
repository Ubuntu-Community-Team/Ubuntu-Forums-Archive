---
title: "ubuntu 8.04 and xen network problem"
date: 2009-01-28
forum: Virtualisation
---

### Post by aloa on 2009-01-28
Regards from Sofia, Bulgaria  :)

I have successfully installed xen server and start one test dom1. When i use static IP on eth0 (192.168.2.95) and create dom1 with :
--------------
xen-create-image --hostname=sendit.newpromo.xxx --size=2Gb --swap=256Mb --ide --ip=192.168.2.96 --netmask=255.255.252.0 --gateway=192.168.3.254 --force --dir=/backup/xen --memory=64Mb --arch=i386 --kernel=/boot/vmlinuz-2.6.24-21-xen --initrd=/boot/initrd.img-2.6.24-21-xen --install-method=debootstrap --dist=hardy --mirror=http://archive.ubuntu.com/ubuntu/ --passwd
--------------

Evereting work fine both dom0 and dom1 can see each others.
But to set server online i need to use vlan on eth0 .. so i set it:
------------
auto eth0.164
iface eth0.164 inet static
address 212.72.194.xxx
netmask 255.255.255.224
vlan_raw_device eth0
gateway 212.72.194.xxx
------------

now om0 have internet .. i set dom1 network in the same way .. to next IP from my ISP ..

In xend-config.sxp i use standard (network-script network-bridge) and (vif-script vif-bridge). When i start dom1 i dom0 in ifconfig i have:
-------------
eth0.164  Link encap:Ethernet  HWaddr 00:30:48:d1:c0:4a
         inet addr:212.72.194.xxx  Bcast:212.72.194.159  Mask:255.255.255.224
         inet6 addr: fe80::230:48ff:fed1:c04a/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:63174 errors:0 dropped:0 overruns:0 frame:0
         TX packets:3385 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:2802219 (2.6 MB)  TX bytes:507272 (495.3 KB)

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:477 errors:0 dropped:0 overruns:0 frame:0
         TX packets:477 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:29773 (29.0 KB)  TX bytes:29773 (29.0 KB)

vif2.0    Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff
         inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
         UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
         RX packets:24 errors:0 dropped:0 overruns:0 frame:0
         TX packets:4 errors:0 dropped:2 overruns:0 carrier:0
         collisions:0 txqueuelen:32
         RX bytes:1176 (1.1 KB)  TX bytes:300 (300.0 B)
-------------------------------------------

In dom1 i have :

---------------------
eth0      Link encap:Ethernet  HWaddr 00:16:3e:18:e5:0e
         inet6 addr: fe80::216:3eff:fe18:e50e/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:5 errors:0 dropped:0 overruns:0 frame:0
         TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:378 (378.0 B)  TX bytes:1374 (1.3 KB)

eth0.164  Link encap:Ethernet  HWaddr 00:16:3e:18:e5:0e
         inet addr:212.72.194.xxx  Bcast:212.72.194.159  Mask:255.255.255.224
         inet6 addr: fe80::216:3eff:fe18:e50e/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 B)  TX bytes:906 (906.0 B)

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:2 errors:0 dropped:0 overruns:0 frame:0
         TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:176 (176.0 B)  TX bytes:176 (176.0 B)
-------------------------------

But dom1 have no internet .. no ping to dom0 .. dom0 also can't ping dom1 IP's ..
My question is: is this configuration is possible ? Can i have vlan on dom0 and on dom1 pointing to eht0 ??

Thank in advance,
ALoa

---

