---
title: "Networking problem on cloned VM"
date: 2016-12-02
forum: Virtualisation
---

### Post by satimis on 2016-12-02
Hi all,

Host - Ubuntu 16.04
Guest - Ubuntu 16.04
Virtualbox

Networking problem on cloned VM.


Orginal VM
=========
$ ifconfig -a
```

br0       Link encap:Ethernet  HWaddr 08:00:27:42:e8:1f  
          inet addr:192.168.8.14  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe42:e81f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3792980 (3.7 MB)  TX bytes:35224 (35.2 KB)

eth0      Link encap:Ethernet  HWaddr 08:00:27:42:e8:1f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3966562 (3.9 MB)  TX bytes:41355 (41.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1505 (1.5 KB)  TX bytes:1505 (1.5 KB)

```


Cloned VM
=========
$ ifconfig -a     
```

br0       Link encap:Ethernet  HWaddr a6:90:2f:e0:0f:0f  
          inet addr:192.168.8.14  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::a490:2fff:fee0:f0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11738 (11.7 KB)

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:a2:ad:e7  
          inet addr:192.168.8.2  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::1677:cb49:5e42:e350/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32369 (32.3 KB)  TX bytes:12688 (12.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:18333 (18.3 KB)  TX bytes:18333 (18.3 KB)

```

cat /etc/udev/rules.d/10-network.rules ```

SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="08:00:27:42:e8:1f", KERNEL=="enp0s3", NAME="eth0"

```

How to change enp0s3 back to eth0?

I encountered this problem before.  Unfortunately I forgot the fix.

Please help.


EDIT
====
I found the problem.  I have 2 network cards on this PC, say network-card-1 and network-card-2.  The former is used and the latter is spare

On cloning a VM if without selecting;
Reinitialize the MAC address of all network cards

there is no problem.  eth0 won't be changed to enp0s3

Is there any solution rather than deleting the VM and re-cloning it?  Thanks


Regards
satimis

---

### Post by satimis on 2016-12-02
Problem solved as follows;

Edit /etc/network/interfaces
Change all "eth0" to "enp0s3"

Reboot VM

---

