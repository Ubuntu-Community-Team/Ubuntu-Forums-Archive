---
title: "Help with dual network adapter setup - routes and gateways"
date: 2013-01-29
forum: Server Platforms
---

### Post by sradhakrishna on 2013-01-29
Hi,

I have Ubuntu Server 12.04 running on a VM (Virtual Box) with two network adapters. The first adapter (eth0) is a bridged adapter connected to my LAN. The second adapter (eth1) is connected to Host only adapter.

The /etc/network/interfaces is as follows:

```

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.1.9
    netmask 255.255.0.0

```
The Host-only adapter settings are as follows:

```

Host-only adapter address: 192.168.1.11
Netmask: 255.255.0.0

DHCP Server Address: 192.168.1.10
DHCP Server Netmask: 255.255.0.0
Lower Address Bound: 192.168.1.11
Upper Address Bound: 192.168.1.254

```
When I boot the above VM, the public and private network addresses come up as follows:

Public network IP address: 10.3.0.237
Private network IP address: 192.168.1.9

I have another VM, with Host only adapter as n/w configuration, set to network address 192.168.1.20.

Now, from my machine with two network addresses:

1. I can ping 192.168.1.20.
2. However, when I do an arping 192.168.1.20, I don't see a response.

route -n shows this:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.3.0.2        0.0.0.0         UG    100    0        0 eth0
10.3.0.0        0.0.0.0         255.255.0.0     U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1

```

What am I missing here? Why am I not able to ping 192.168.1.20?

---

### Post by darkod on 2013-01-29
What is the purpose of this exactly, just testing?

Since you are using different subnets on both adapters, you can set both as bridged to your physical LAN card. I am not sure how Host Only works exactly.

Set it to bridged on both VMs, and run any subnets you want on the same network. Just make sure you configure everything correctly.

---

### Post by TheFu on 2013-01-29
Seems you'd need to manually specify the **gateway** for each interface.  
The complete output from **ifconfig** might help.

---

### Post by darkod on 2013-01-29
You don't need more than one gateway just to ping a machine on the same subnet. In fact, you rarely need two gateways, especially if the point of this exercise is to have ubuntu server acting as a router. In that case it has only one gateway towards the internet.

I think the Host Only option is messing with how you expect it to work. You said ping works, but arping doesn't. The Host Only might be blocking the ARP replies.

---

### Post by sradhakrishna on 2013-01-29
I am trying to emulate a private n/w, public n/w setup that we use. All devices are a part of a private n/w, while there's one machine which talks to each of these devices for some data, and provides a webserver for users in the public n/w to view this data.

The ifconfig output is as follows:

```

eth0      Link encap:Ethernet  HWaddr 08:00:27:92:a7:f0  
          inet addr:10.3.0.237  Bcast:10.3.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a00:27ff:fe92:a7f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26064 (26.0 KB)  TX bytes:2353 (2.3 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:ed:ef:cb  
          inet addr:192.168.1.9  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a00:27ff:feed:efcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:316 (316.0 B)  TX bytes:748 (748.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1036 (1.0 KB)  TX bytes:1036 (1.0 KB)


```

---

### Post by SeijiSensei on 2013-01-29
> ```
auto eth1
iface eth1 inet static
    address 192.168.1.9
    netmask 255.255.0.0
```

Your routing table specifies the "class-B" address space 192.168.0.0/16.  What you really want is 192.168.1.0/24, or 192.168.1.0 with a 255.255.255.0 netmask.  Change the netmask in /etc/network/interfaces.

---

### Post by sradhakrishna on 2013-01-29
Thanks for the reply SeijiSensei,

Tried changing the netmask - but didn't seem to help. The default gateway is still set to the network of eth0.

Also, am able to ping the machines on the eth1 network. Its just that arping doesn't work. 

Any help will be greatly appreciated.

Radha.

---

### Post by darkod on 2013-01-30
> **sradhakrishna said:**
> Thanks for the reply SeijiSensei,

Tried changing the netmask - but didn't seem to help. The default gateway is still set to the network of eth0.

Also, am able to ping the machines on the eth1 network. Its just that arping doesn't work. 

Any help will be greatly appreciated.

Radha.

Did you try changing the Host Only to Bridged?

Of course you will receive default gateway on eth0 since it's set up for dhcp. It receives the gateway from the dhcp server.

If you want the gateway to be eth1, change eth0 to static settings with only IP and netmask, and set correct gateway on eth1.

But I still think the Host Only is messing with you and arping. That's why ping works.

And why do you need arping anyway? Is it only a test, or you really need ARP packages?

---

