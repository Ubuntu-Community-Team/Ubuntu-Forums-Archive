---
title: "LXD containers not getting IP addresses"
date: 2017-01-21
forum: Virtualisation
---

### Post by Plecebo on 2017-01-21
This was working earlier today, had been working for months, then I switched out my router and things are all goofed. No matter what I do I can't get the lxd containers to grab an IP address from the new dhcp server. 

Here is some context to help out, not sure what info is most needed, so appologies if this is too much info: 

First my networking configuration: 
```

br0       Link encap:Ethernet  HWaddr 08:60:6e:10:f6:07  
          inet addr:192.168.86.50  Bcast:192.168.86.255  Mask:255.255.255.0
          inet6 addr: fe80::a60:6eff:fe10:f607/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:485927 (485.9 KB)  TX bytes:44974 (44.9 KB)

vethSEROPP Link encap:Ethernet  HWaddr fe:20:fe:62:cf:b7  
          inet6 addr: fe80::fc20:feff:fe62:cfb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1192 (1.1 KB)  TX bytes:868 (868.0 B)

```

now my /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet manual

auto br0
iface br0 inet dhcp
	bridge-ports enp3s0

```

Now some lxd info:
```
lxc --version
2.7

``` 

Here is one containers config: 
```
lxc info proxy
Name: proxy
Remote: unix:/var/lib/lxd/unix.socket
Architecture: x86_64
Created: 2016/04/28 17:43 UTC
Status: Running
Type: persistent
Profiles: default
Pid: 17406
Ips:
  eth0:	inet6	fe80::216:3eff:fe05:aab4	vethVRJU1E
  lo:	inet	127.0.0.1
  lo:	inet6	::1
Resources:
  Processes: 6
  Disk usage:
    root: 496.02MB
  CPU usage:
    CPU usage (in seconds): 1
  Memory usage:
    Memory (current): 11.77MB
    Memory (peak): 32.62MB
  Network usage:
    eth0:
      Bytes received: 568 bytes
      Bytes sent: 600 bytes
      Packets received: 7
      Packets sent: 4
    lo:
      Bytes received: 0 bytes
      Bytes sent: 0 bytes
      Packets received: 0
      Packets sent: 0

```

and the defult profile:
```
lxc profile show default
name: default
config: {}
description: Default LXD profile
devices:
  eth0:
    nictype: bridged
    parent: br0
    type: nic
usedby:
- /1.0/containers/proxy

```

Here is the list output:
```
lxc list proxy
+-------+---------+------+------+------------+-----------+
| NAME  |  STATE  | IPV4 | IPV6 |    TYPE    | SNAPSHOTS |
+-------+---------+------+------+------------+-----------+
| proxy | RUNNING |      |      | PERSISTENT | 0         |
+-------+---------+------+------+------------+-----------+

```

no matter what I do i can't seem to get it an ip address. 

Anyone have any suggestions on how to figure this out? Any other info needed I can get. 

Thanks in advance for any help you can provide.

---

### Post by Plecebo on 2017-01-22
I figured out a solution to this, not my optimal solution I think, but it is mostly working ok now. 

What I ended up doing was changing from using the bridged nic to the macvlan

So my default profile for lxd now looks like this:
```
lxc profile show default
name: default
config: {}
description: Default LXD profile
devices:
  eth0:
    nictype: macvlan
    parent: br0
    type: nic

```

I then had to change each container to specify that it should get an IP address via DHCP, not sure why it was working previously and has since stopped working, but making this change made the containers get an IP at boot from the new router: 

Changed from this: 
```
cat /etc/network/interfaces.d/eth0.cfg
# The primary network interface
auto eth0
iface eth0 inet manual

```

To this: 
```
cat /etc/network/interfaces.d/eth0.cfg
# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Reboot the container and magic!

The downside to this is that my container host can not communicate with my containers. Apparently this is a limitation of the macvlan interface type. 

I'm putting this solution here in case anyone else runs into this.

---

