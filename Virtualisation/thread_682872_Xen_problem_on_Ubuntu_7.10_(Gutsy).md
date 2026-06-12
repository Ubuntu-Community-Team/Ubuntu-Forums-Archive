---
title: "Xen problem on Ubuntu 7.10 (Gutsy)"
date: 2008-01-30
forum: Virtualisation
---

### Post by sudoyang on 2008-01-30
I have been using Xen on CentOS dom0's but now I'm trying to migrate some of these servers to Ubuntu 7.10 Server (Gutsy).  Yesterday, I built one Ubuntu server to run Xen and everything's working fine (all domUs started just fine).  In an attempt to clone the system, I accidentally destroy the file systems.  Anyway, today I tried to create this server with the exact configuration but I can't start any of the domU's.  This is the error I'm getting:

[B]   root@ubuxen:/var/log/xen# xm create -c ac1
   Using config file "/etc/xen/ac1".
   Error: Device 0 (vif) could not be connected. Hotplug scripts not working.

[/B]

xend is running and all the bridges are up:

  root@ubuxen:/var/log/xen# brctl show
  bridge name     bridge id               STP enabled     interfaces
  xenbr0          8000.feffffffffff       no              vif0.0
                                                          peth0
  xenbr1          8000.feffffffffff       no              vif0.1
                                                          peth1

my interfaces:

eth0      Link encap:Ethernet  HWaddr 00:30:48:34:54:BA  
          inet addr:10.1.34.229  Bcast:10.1.34.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe34:54ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:323541 (315.9 KB)  TX bytes:120604 (117.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:30:48:34:54:BB  
          inet addr:192.168.1.1  Bcast:192.168.1.0  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe34:54bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

peth0     Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:5185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:371206 (362.5 KB)  TX bytes:135016 (131.8 KB)
          Base address:0x2000 Memory:da000000-da020000 

peth1     Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          UP BROADCAST NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2020 Mif0.0    Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120604 (117.7 KB)  TX bytes:323611 (316.0 KB)

vif0.1    Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:468 (468.0 b)  TX bytes:510 (510.0 b)

xenbr0    Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182859 (178.5 KB)  TX bytes:468 (468.0 b)

xenbr1    Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:384 (384.0 b)  TX bytes:468 (468.0 b)
emory:da020000-da040000 


this is my domU xen config file:

kernel = "/boot/vmlinuz-xenu-cos44"
ramdisk = "/boot/initrd-xenu-cos44"
memory = 1024
name = 'ac1'
vcpus = 4
vif = [ 'bridge=xenbr1,mac=00:16:3e:14:2f:7f' ]
disk = [  'file:/store/ac1root,sda1,w', 'file:/store/ac1swap,sda2,w' ]
root = '/dev/sda1 ro'
extra = "3"
on_reboot = 'restart'
on_crash = 'restart'


these are the xen packages I have installed;

ii  libxen3.1                              3.1.0-0ubuntu18         library interface for Xen, a Virtual Machine
ii  linux-image-2.6.22-14-xen              2.6.22-14.47            Linux kernel image for version 2.6.22 on Thi
ii  linux-image-xen                        2.6.22.14.21            Linux kernel image on Xen
ii  linux-restricted-modules-2.6.22-14-xen 2.6.22.4-14.10          Non-free Linux 2.6.22 modules on Xen
ii  linux-restricted-modules-xen           2.6.22.14.21            Restricted Linux modules on Xen
ii  linux-ubuntu-modules-2.6.22-14-xen     2.6.22-14.37            Ubuntu supplied Linux modules for version 2.
ii  linux-xen                              2.6.22.14.21            Complete Linux kernel on Xen
ii  python-xen-3.1                         3.1.0-0ubuntu18         python bindings for Xen, a Virtual Machine M
ii  xen-hypervisor-3.1                     3.1.0-0ubuntu18         The Xen Hypervisor for i386, amd64 amd lpia
ii  xen-shell                              1.2-1                   Console based Xen administration utility
ii  xen-tools                              3.5-1ubuntu2            Tools to manage debian XEN virtual servers
ii  xen-utils-3.1                          3.1.0-0ubuntu18         XEN administrative tools

Any idea what can be wrong?  It was working fine yesterday with this exact same config on Ubuntu 7.10 server (this same config still works on CentOS 5.1).

---

### Post by sudoyang on 2008-01-30
I just built another server and it works fine.  As far as I know both systems are identical.  Same packages are installed and same configurations.  Why is the broken system not able to initialize vif hotplug device?  I guess I can always reinstall.  weird.

---

### Post by sudoyang on 2008-01-30
That is so weird.  I rebuilt the server (keeping the partition that housed my VMs) and everything's working fine now.  Don't know what the problem could've been.

Anyway, just want to update everyone.  In case you're experiencing the same problem, sometime it might be worthwhile to simply reinstall.

---

