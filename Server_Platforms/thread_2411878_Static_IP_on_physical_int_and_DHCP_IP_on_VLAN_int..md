---
title: "Static IP on physical int and DHCP IP on VLAN int."
date: 2019-02-05
forum: Server Platforms
---

### Post by am.steen on 2019-02-05
I am using ubuntu 18.04 bionic 
Is it possible to have physical interface  eth0 to work with static IP while 
A VLAN interface linked to eth0 work with automatic DHCP ??


[COLOR=#ff0000]**I try this in netplan file :-**[/COLOR]


[COLOR=#0000ff]network:[/COLOR]
[COLOR=#0000ff]  version: 2[/COLOR]
[COLOR=#0000ff]  renderer: NetworkManager[/COLOR]
[COLOR=#0000ff]  ethernets:[/COLOR]
[COLOR=#0000ff]    eth0:[/COLOR]
[COLOR=#0000ff]     dhcp4: no[/COLOR]
[COLOR=#0000ff]     addresses: [192.168.100.60/24][/COLOR]
[COLOR=#0000ff]     gateway4: 192.168.100.1[/COLOR]
[COLOR=#0000ff]     nameservers:[/COLOR]
[COLOR=#0000ff]       addresses: [8.8.8.8,8.8.4.4][/COLOR]
[COLOR=#0000ff]  vlans:[/COLOR]
[COLOR=#0000ff]      veth0:[/COLOR]
[COLOR=#0000ff]          id: 0[/COLOR]
[COLOR=#0000ff]          link: eth0[/COLOR]
[COLOR=#0000ff]          dhcp4: yes

[/COLOR]
**but it did not work as eth0 works with 192.168.100.60 and vlan0 do take any ip address**


eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.100.60  netmask 255.255.255.0  broadcast 192.168.100.255
        inet6 fd0a:428f:6aa3:0:42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x20<link>
        ether 02:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 5071  bytes 937488 (937.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3647  bytes 584681 (584.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 39


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 80  bytes 5920 (5.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 80  bytes 5920 (5.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 12:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



[COLOR=#ff0000]**please help**[/COLOR]

---

### Post by darkod on 2019-02-05
1. Always post the output inside CODE tags. That allows to keep formatting and spacing, which is very important for netplan. From what you posted no one can tell if the config is correct.

2. You seem to be using VLAN ID 0. Is that right? That is a very strange choice. Have you tried using another VLAN ID?

Here you have examples for netplan VLANs among other things: [https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan](https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan)

---

### Post by SeijiSensei on 2019-02-05
Are they going to have addresses in different subnets?  If not, I don't see the advantage.

---

### Post by am.steen on 2019-02-06
Very sorry I was not know how to add code tags
now I try it as 
[https://blog.ubuntu.com/2017/12/01/u...bionic-netplan]("https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan")

like this 

```
network:  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
     dhcp4: no
     addresses: [192.168.100.60/24]
     gateway4: 192.168.100.1
     nameservers:
       addresses: [8.8.8.8,8.8.4.4]
  vlans:
      vdev:
          id: 101
          link: eth0
          dhcp4: true   

```[COLOR=#000000]

But the same result 

[/COLOR]```
 eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.100.60  netmask 255.255.255.0  broadcast 192.168.100.255
        inet6 fd0a:428f:6aa3:0:42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x20<link>
        ether 02:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 3184  bytes 576650 (576.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2554  bytes 437956 (437.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 39


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 80  bytes 5920 (5.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 80  bytes 5920 (5.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vdev: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x20<link>
        ether 02:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 2616 (2.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


veth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x20<link>
        ether 02:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 17  bytes 2706 (2.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 12:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
And After two minutes it becomes like this
```
 eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500        inet 192.168.100.60  netmask 255.255.255.0  broadcast 192.168.100.255
        inet6 fd0a:428f:6aa3:0:42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::42:82ff:fea6:f0d0  prefixlen 64  scopeid 0x20<link>
        ether 02:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 1386  bytes 247739 (247.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1148  bytes 204746 (204.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 39


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 80  bytes 5920 (5.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 80  bytes 5920 (5.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 12:42:82:a6:f0:d0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

I am not using [COLOR=#000000]VLAN ID 0 here but it takes it anyway

What I want to do is that when I move my device to different network 
with different subnet it will be on line anyway.
and it is the same if we can run main interface with auto IP 
and vlan with static IP no problem

Please help

[/COLOR]

---

### Post by darkod on 2019-02-06
I don't think you understand how vlans work. You can't simply invent them. Is the computer connected to a switch that can do vlan tagging at all?

Vlans are not used so that you can have static IP connected to one network and then dhcp when connected to another place. You will have to change settings manually in such case.

Maybe you could add multiple IPs to the NIC so that they correspond to both networks.

---

### Post by volkswagner on 2019-02-06
You likely don't need static IP, unless you plan to create a bridge interface or something.

Set your server to DHCP, and setup a reservation in your router/DHCP server. If your router can't do DHCP reservations... get a new router :)

---

### Post by am.steen on 2019-02-07
OK 

I think I was misunderstanding 
I have only one network card and can not add another one 
As I work on orange-pi zero that is a small board computer

So how to do to let the Ubuntu have two interfaces ( for example one physical 
and one virtual ) one auto IP And other one is static IP

Is there are some solution ??

---

