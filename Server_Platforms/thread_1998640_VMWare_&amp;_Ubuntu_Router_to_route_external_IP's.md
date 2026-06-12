---
title: "VMWare &amp; Ubuntu Router to route external IP's"
date: 2012-06-07
forum: Server Platforms
---

### Post by mYzk on 2012-06-07
Hello! I have a problem. I am trying to install Ubuntu as a router on my VMWare esxi to route the external ip's I have ordered from dedicated server hoster.

My router is connected to external (vmnic0 external) and internal (no nic) vSwitches. I have setup the router like this: 

**These are my setting for /etc/network/interfaces:**

```
auto eth0
iface eth0 inet static
address 37.xxx.xxx.9
netmask 255.255.255.0
network 37.xxx.xxx.0
broadcast 37.xxx.xxx.255
gateway 37.xxx.xxx.1

auto eth1
iface eth1 inet static
address 37.xxx.xxx.119
netmask 255.xxx.xxx.0
```

**My routers ifconfig:**

```
root@Router:~# ifconfig
eth0 Link encap:Ethernet HWaddr 00:0c:29:5b:d1:58
inet addr:37.xxx.xxx.9 Bcast:37.xxx.xxx.255 Mask:255.255.255.0
inet6 addr: fe80::20c:29ff:fe5b:d158/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:816540 errors:0 dropped:24849 overruns:0 frame:0
TX packets:32840 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:127643014 (127.6 MB) TX bytes:2002859 (2.0 MB)

eth1 Link encap:Ethernet HWaddr 00:0c:29:5b:d1:62
inet addr:37.xxx.xxx.119 Bcast:37.xxx.xxx.255 Mask:255.255.255.
inet6 addr: fe80::20c:29ff:fe5b:d162/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2 errors:0 dropped:81 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:120 (120.0 B) TX bytes:468 (468.0 B)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:980 errors:0 dropped:0 overruns:0 frame:0
TX packets:980 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:74400 (74.4 KB) TX bytes:74400 (74.4 KB)
```

**/etc/sysctl.conf**

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
```

After that I did *sysctl.conf -p*.

This is what I got when I did *route -n*

```
root@Router:~# route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 37.xxx.xxx.1 0.0.0.0 UG 100 0 0 eth0
37.xxx.xxx.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
37.xxx.xxx.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
```

I am trying to add another virtual machine (Ubuntu Server 12.04) and when I come up to where I need to configure the network manually I insert:

```

IP: 37.xxx.xxx.120
Netmask: 255.255.255.0
Gateway: 37.xxx.xxx.119 (eth1 address on the router)

```

After that it says it can not connect to gateway. 

I am out of ideas. I have scanned around the internet and I still can't find a solution. 

I hope you guys can help me some how.

Thank you.

---

### Post by mYzk on 2012-06-07
No need for help anymore. Got it working.

---

### Post by rubylaser on 2012-06-07
It is nice to post your solution so that others can benefit from your experience.  Also, you can mark the thread as solved under the thread tools at the top of the page.  Thanks :)

---

