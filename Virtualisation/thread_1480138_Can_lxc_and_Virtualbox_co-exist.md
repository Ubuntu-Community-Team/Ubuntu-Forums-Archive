---
title: "Can lxc and Virtualbox co-exist"
date: 2010-05-11
forum: Virtualisation
---

### Post by gtr33m on 2010-05-11
I have a decent server that is a few years old and restricted to 32 bit.  It has plenty of ram and processing power, so I'm very reluctant to upgrade to a newer system.

At the moment I am running Lucid as the host OS and have a few virtualbox guests running Windows 2003, ubuntu hardy, and ubuntu lucid.

I'm getting poor performance with a specific app (Zimbra) on the hardy guest which has led me to look at lxc.

What I'd like to know is whether lxc and Virtualbox can co-exist happily on the same host.  I'll still need Virtualbox for my Windows 2003 guest.

I'll post this is a separate thread, but I'm also interested to know if lxc can run a hardy guest on the lucid host.

Thanks,

Mark

---

### Post by BoneKracker on 2010-05-12
I can't see why they wouldn't.

In fact, you ought to be able to use libvirt to manage both.

---

### Post by gtr33m on 2010-05-12
So far it seems that you can.  The only issue that I am having is using the bridged network adapter.  It's probably a good idea to use 2 separate network adapters, and bridge one for Virtualbox and the other for lxc

---

### Post by BoneKracker on 2010-05-12
Are you using libvirt?  I would think it would handle that for you.

---

### Post by gtr33m on 2010-05-14
It looks like bridge-utils is the networking method used for lxc, and bridge utils does take up the interface it's bridged to, so at least one spare interface is required.

I believe that multiple containers can use the same bridged interface, but I've still to test this.

---

### Post by BoneKracker on 2010-05-14
There are a number methods of networking a container, but connecting the container through a veth pair to a bridge is the most broadly useful.

You don't need to use multiple physical network adapters (although you can if you like).

You can attach multiple virtual ethernet intface pairs to a single bridge (as many as you want, effectively).  In othere words, you can connect multiple containers to a single bridge.

Also, you can assign multiple addresses (and multiple psuedo-interfaces) to a single adapter.  In other words, you can create multiple bridges on a single adapter.

The alternatives are numerous.  You could use a single interface on a single adapter and route traffic to multiple pseudo-interfaces.  You can isolate containers using iptables or ebtables.  You can have the containers on seperate vlans.

But for the simplest most useful approach, just use the host system to create a bridge, and then connect each container to the bridge using unnamed veth pairs.  The system will automatically deconflict veth naming.

To demonstrate, here are two containers running on a single host, connected to the network via container-unique veth pairs plugged into a single bridge.  This is ifconfig from the host (which has only a single physical network adapter enabled):
```
tempest ~ # ifconfig
br0       Link encap:Ethernet  HWaddr 00:04:76:33:80:2e  
          inet addr:192.168.1.27  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22503564 (21.4 MiB)  TX bytes:3216255 (3.0 MiB)

eth0      Link encap:Ethernet  HWaddr 00:04:76:33:80:2e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1119 txqueuelen:1000 
          RX bytes:22922731 (21.8 MiB)  TX bytes:4835217 (4.6 MiB)
          Interrupt:3 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3012 (2.9 KiB)  TX bytes:3012 (2.9 KiB)

vethBiTww Link encap:Ethernet  HWaddr 8e:76:52:e6:39:f0  
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7737 (7.5 KiB)  TX bytes:7851 (7.6 KiB)

vethwxWK5 Link encap:Ethernet  HWaddr 0a:5c:3f:e5:b3:99  
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1066 (1.0 KiB)  TX bytes:716 (716.0 B)

```

This is ifconfig from the first container:
```
alpha / # ifconfig
eth0      Link encap:Ethernet  HWaddr fa:d7:52:ba:41:b2  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:716 (716.0 B)  TX bytes:1066 (1.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

And this is ifconfig from the second container:
```
beta ~ # ifconfig
eth0      Link encap:Ethernet  HWaddr b6:67:82:92:ca:a0  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6545 (6.3 KiB)  TX bytes:6553 (6.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

On the host, the bridge was configured thus:

```
brctl addbr br0
brctl setfd br0 0
brctl addif br0 eth0
ifconfig eth0 0.0.0.0 up
```

a dhcp client was used on the host to assign an ip address to br0
a dhcp client was also used within each of the containers to assign an ip address to their end of their veth pair (which they see as "eth0")

Under this particular configuration, the containers can talk to each other "over the LAN" as part of the same subnet (there is no firewall between the containers):
```
alpha / # ssh beta
root@beta's password: 
beta ~ # 
```

---

### Post by fjgaude on 2010-05-14
Fantastic, thanks for such useful information!

---

### Post by BoneKracker on 2010-05-14
One more thing.

The network portion of these containers' config files is what you'd expect.  Both are identical, with unique MAC addresses for the pseudo-inteface:
```

# network configuration
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = br0
lxc.network.hwaddr = b6:67:82:92:ca:a0
lxc.network.ipv4 = 0.0.0.0
```

What I do is comment out the lxc.network.hwaddr the first time I start the container, then cut and paste (from ifconfig or whatever) the MAC address that's randomly generated.  If you don't have one, the container will receive a new, randomly-generated MAC address each time.

Having a consistent one is good for your network if you're using dhcp or if you are frequently stopping and starting the container.  (Otherwise you cause perturbation in your dhcp lease pool, routing tables, and arp tables.)  Also, it's actually necessary if you are using static routes or DNAT to send connections to the container (ie., if you have firewall rules that refer to the container by MAC or IP address).

The lxc.network.ipv4 = 0.0.0.0 is what is in the "literature" for using dhcp.  I suspect it's not necessary but haven't tried it without.

Don't mean to prognosticate -- just hope this saves somebody some time figuring it out. :)

---

### Post by gtr33m on 2010-05-16
Thanks for the fantastic info, this is exactly what I was after.

LXC seems to work extremely well, very similar to OpenVZ without the custom kernel.  The only real issue is the lack of documentation or real world users.  This will come with time no doubt.

Thanks again,

Mark

---

