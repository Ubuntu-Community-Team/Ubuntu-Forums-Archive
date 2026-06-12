---
title: "Assign IP to virtual instance"
date: 2016-06-24
forum: Virtualisation
---

### Post by Victor_Huertero on 2016-06-24
Im running ubuntu (host) and am trying to assinged an ip to a virtualbox ubuntu instance.

**My host ifconfig and interface files**

```
eth0      Link encap:Ethernet  HWaddr 04:7d:7b:90:09:88          inet6 addr: fe80::67d:7bff:fe90:988/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1077991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:126289093 (126.2 MB)  TX bytes:1012 (1.0 KB)
          Interrupt:18 Memory:dfd00000-dfd20000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:997577 (997.5 KB)  TX bytes:997577 (997.5 KB)


p6p1      Link encap:Ethernet  HWaddr 00:02:c9:c1:2d:ba
          inet addr:x.x.244.34  Bcast:x.x.244.39  Mask:255.255.255.248
          inet6 addr: fe80::202:c9ff:fec1:2dba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95018605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56058476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:136551212095 (136.5 GB)  TX bytes:13768833540 (13.7 GB)


p6p1:0    Link encap:Ethernet  HWaddr 00:02:c9:c1:2d:ba
          inet addr:x.x.244.35  Bcast:x.x.244.39  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


p6p1:1    Link encap:Ethernet  HWaddr 00:02:c9:c1:2d:ba
          inet addr:x.x.244.36  Bcast:x.x.244.39  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```
```
auto lo
iface lo inet loopback
auto p6p1
iface p6p1 inet static
        address x.x.244.34
        netmask 255.255.255.248
        gateway x.x.244.33


auto p6p1:0
iface p6p1:0 inet static
        address x.x..244.35
        netmask 255.255.255.248

auto p6p1:1
iface p6p1:1 inet static
        address x.x..244.36
        netmask 255.255.255.248



```

My main NIC is p6p1 which works and has outside internet.

p6p1:0 is for my first instance and p6p1:1 is for my second instance. this setup worked before before i formatted and started again. (Both guest us ubuntu too)

My guest and virtualbox configurations 

[http://i.imgur.com/ghyEaqX.png](http://i.imgur.com/ghyEaqX.png)

[http://i.imgur.com/fN8b9Z0.png](http://i.imgur.com/fN8b9Z0.png)

[http://i.imgur.com/sDUUqL1.png](http://i.imgur.com/sDUUqL1.png)

thanks.

to recap

x.x.244.34 is host
x.x.244.35 and x.x.244.36 is my virtualbox instances

[ATTACH=CONFIG]269764[/ATTACH][ATTACH=CONFIG]269765[/ATTACH][ATTACH=CONFIG]269766[/ATTACH][ATTACH=CONFIG]269767[/ATTACH]

---

### Post by MAFoElffen on 2016-06-26
Move to the Virtualization Forum.

First, please post the results of:
```

sudo dpkg -l | grep vlan
sudo dpkg -l | grep bridge-utils

```
If you could also post what is in the advanced section of each guest virtual NIC, please?

I can see that you are trying to create a vlan trunk. The first thin I see that jumps out at me, is that there is a recursion. DeviceName.0 is the same as saying DeviceName without the dot zero. So DeviceName is the original device that is being sectioned and split out. vlan.1 (or vlan.000001) might be the first device section, then something with a different identifier, such as vlan.2. But "zero", or something resulting in the same, is reserved as the original.

Does that make sense? It's sort of like a netwrok ID (NID). An NID is the whole, and ID's te whole, you cannot use it also as a slice of the whole. That would be a conflict from recursion (calling itself, and expecting it to be diffrent).

Where is the config of your bridge (the bridge from virt net to host) and what is the device name? Is there anyway you could post your host ifconfig in text format (addy's edited, if needed) within code tags?

---

