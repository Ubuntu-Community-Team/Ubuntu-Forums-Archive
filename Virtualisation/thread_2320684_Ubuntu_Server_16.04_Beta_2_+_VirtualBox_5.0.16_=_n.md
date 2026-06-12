---
title: "Ubuntu Server 16.04 Beta 2 + VirtualBox 5.0.16 = no bridged network settings"
date: 2016-04-16
forum: Virtualisation
---

### Post by speedojoe2 on 2016-04-16
I'm trying to run VirtualBox on a headless whitebox running Ubuntu Server, but there's one thing which has stumped me - the lack of bridged network settings under Preferences/Network. The only tabs available are 'NAT Networks' and 'Host-only Networks'.
[IMG]http://i.imgur.com/JALtUmU.png[/IMG]

Have I missed some configuration?

---

### Post by MAFoElffen on 2016-04-16
It would be okay for you to post your 192.168.xxx.xxx address here, without having to edit it, as that NID range is a private network NID range and could not be accessed from outside your network...

Did you configure a bridge? 
Because, via what output you did provide, I do not see that you did. an "ifconfig -a" would give more detaill. But the only bridge I see is for LXC, which 16.04 uses LXD, and asks you if you further want to convert that bridge to an (LXD bridge naming convention in the install...) That LXC bridge is not accessible by VirtualBox.

If you switch the Guest to NAT, do you have outside network connectivity from your guest? (just to ensure that your guests can connect if and when you do install and configure a bridge...)

EDIT--
For my own curiosity: I see a recent interest in headless servers running VirtualBox... VirtualBox is a Type type 2 hypervisor, which is also GUI based. If you are going thorugh the trouble of installing a headless server, which is most likelt vt-x capable, what was your decision to do VirtualBox? No judgement omn that at all. I'm just curious.

---

### Post by speedojoe2 on 2016-04-16
> It would be okay for you to post your 192.168.xxx.xxx address here, without having to edit it, as that NID range is a private network NID range and could not be accessed from outside your network...
I know. That's what I've done.

> Did you configure a bridge? 
Because, via what output you did provide, I do not see that you did. an "ifconfig -a" would give more detaill. But the only bridge I see is for LXC, which 16.04 uses LXD, and asks you if you further want to convert that bridge to an (LXD bridge naming convention in the install...) That LXC bridge is not accessible by VirtualBox.
The section of VirtualBox in my screenshot is where you'd usually configure a bridge.

I was asked during installation of Ubuntu Server if I wanted to convert the bridge. Do you think that's it?

ifconfig -a
```
 ifconfig -aenp2s0    Link encap:Ethernet  HWaddr 94:de:80:cb:d8:e6
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:fecb:d8e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29800948 (29.8 MB)  TX bytes:363253807 (363.2 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:31223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:349590712 (349.5 MB)  TX bytes:349590712 (349.5 MB)


lxcbr0    Link encap:Ethernet  HWaddr ce:4f:63:f7:ff:0c
          inet addr:10.0.3.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::cc4f:63ff:fef7:ff0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:570 (570.0 B)
```
> If you switch the Guest to NAT, do you have outside network connectivity from your guest?
I don't have any guest VMs yet due to not having bridged networking working.

---

### Post by MAFoElffen on 2016-04-17
Let me switch over to my older desktop development machine. Besides also being my server management station, with connections to all my virtual servers, it also just happens to be locally running VirtualBox, VMware Player and VMware Workstation.

Then I can post the config from there. That way it will be easier to explain...
This is the output from that box'es ifconfig. Note 'virbr0'. Ignore the blank stats, as I haven't started any VM's yet...
```

mafoelffen@maferr-ubuntu-1:~$ ifconfig -a
eth5      Link encap:Ethernet  HWaddr bc:ae:c5:78:4d:41  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe78:4d41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173 errors:0 dropped:1 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34731 (34.7 KB)  TX bytes:14670 (14.6 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25597 (25.5 KB)  TX bytes:25597 (25.5 KB)


virbr0    Link encap:Ethernet  HWaddr e6:03:1a:05:72:38  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 00:0d:88:8b:b5:e3  
          inet addr:192.168.1.88  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe8b:b5e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73618 (73.6 KB)  TX bytes:28553 (28.5 KB)

```
This is it's /etc/network/interfaces:
```

mafoelffen@maferr-ubuntu-1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


## This is the second physical port
## But shows up as eth3
auto eth5 
#  iface eth5 inet dhcp
  # Alternate Manual Config
  iface eth5 inet static
  address 192.168.1.6
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.1
  dns-search ferreiraent.com
  dns 192.168.2.15 192.168.2.16 8.8.8.8
##  First 2 above are my local dns primary and secondary servers, which are also the dhcp servers for that NID


## This is the First physical port, which has intermittent problems, so remove my bridge from this box, and just use the NAT on virbr0
#auto eth4 
#  iface eth4 inet dhcp


auto wlan0 
  iface eth0 inet dhcp

```

I installed a bridge to bridge my vm's to my host network... Note 'bridge-utils' in the following output
```

mafoelffen@maferr-ubuntu-1:~$ dpkg -l | grep -i bridge
ii  bridge-utils                                          1.5-6ubuntu2                                           amd64        Utilities for configuring the Linux Ethernet bridge
ii  ebtables                                              2.0.10.4-3ubuntu1                                      amd64        Ethernet bridge frame table administration
ii  libatk-adaptor:amd64                                  2.10.2-2ubuntu1                                        amd64        AT-SPI 2 toolkit bridge
ii  libatk-bridge2.0-0:amd64                              2.10.2-2ubuntu1                                        amd64        AT-SPI 2 toolkit bridge - shared library
ii  python3-uno                                           1:4.2.8-0ubuntu4                                       amd64        Python-UNO bridge

```
If you do a formal 'bridge', you have to bind it to a dedicated host NIC. NAT is default for both VMware and VirtualBox (because installing a bridge requires additional installation and configuration). If virbr0 is not in your host's output, then something went wrong with your install of VirtualBox and maybe you should try reinstalling it.

If you have another network card in your host and you want to bridge your VM's to your host network;s NID, then I can lead you through that. But I would suggest you get your NAT net working first, as that is broke at the moment for you...

---

### Post by speedojoe2 on 2016-04-18
Hi MAFoElffen

I may have been wrong with where I was expecting to see the bridged network settings.

I'll confirm tonight.

---

### Post by MAFoElffen on 2016-04-18
Okay...

---

### Post by Morbius1 on 2016-04-19
More of an FYI but VBox released 5.0.18 last night with a package specifically for Xenial this time: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by MAFoElffen on 2016-04-19
Good to know, especially with it's release this week. :D

---

