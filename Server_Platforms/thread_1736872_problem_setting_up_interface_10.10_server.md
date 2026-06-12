---
title: "problem setting up interface 10.10 server"
date: 2011-04-22
forum: Server Platforms
---

### Post by gopher2x on 2011-04-22
im trying to setup eth0 with subdevice eth0.0 and eth0.99 to come up at boot

eth0 is dhcp clint
eth0:0 is static ip
eth0.99 is 802.1q vlan interface


/etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
 metric 0

iface eth0.0 inet static
 address 172.20.26.239
 netmask 255.255.255.0
 broadcast 172.20.26.255
 network 172.20.26.0

iface eth0.99 inet static
 address 192.168.50.2 
 netmask 255.255.255.0
 network 192.168.50.0
 broadcast 192.168.50.255
 vlan_raw_device eth0

```


after boot only eth0 is up
```

david@ubuntu-server1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:c1:6e:c0  
          inet addr:172.20.26.101  Bcast:172.20.26.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fec1:6ec0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76892 (76.8 KB)  TX bytes:69828 (69.8 KB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:584553 (584.5 KB)  TX bytes:584553 (584.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

but if i issue ifup for each interface they come up

```

david@ubuntu-server1:~$ sudo ifup eth0:0
ssh stop/waiting
ssh start/running, process 2615
david@ubuntu-server1:~$ sudo ifup eth0.99
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 99 to IF -:eth0:-
ssh stop/waiting
ssh start/running, process 2777
david@ubuntu-server1:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:c1:6e:c0  
          inet addr:172.20.26.101  Bcast:172.20.26.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fec1:6ec0/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:2086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:295596 (295.5 KB)  TX bytes:290556 (290.5 KB)
          Interrupt:46 

eth0:0    Link encap:Ethernet  HWaddr 00:24:1d:c1:6e:c0  
          inet addr:172.20.26.239  Bcast:172.20.26.255  Mask:255.255.255.0
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          Interrupt:46 

eth0.99   Link encap:Ethernet  HWaddr 00:24:1d:c1:6e:c0  
          inet addr:192.168.50.2  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fec1:6ec0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46 (46.0 B)  TX bytes:9431 (9.4 KB)


```

so what am i doing wrong? whay are the not booting up?

---

### Post by bmathis on 2011-04-22
its been awhile and Im probably wrong, but I believe you need to add auto to your interface file

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
 metric 0

**auto eth0.0**
iface eth0.0 inet static
 address 172.20.26.239
 netmask 255.255.255.0
 broadcast 172.20.26.255
 network 172.20.26.0

**auto eth0.99**
iface eth0.99 inet static
 address 192.168.50.2 
 netmask 255.255.255.0
 network 192.168.50.0
 broadcast 192.168.50.255
 vlan_raw_device eth0

---

