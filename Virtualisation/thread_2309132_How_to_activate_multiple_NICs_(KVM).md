---
title: "How to activate multiple NICs (KVM)?"
date: 2016-01-07
forum: Virtualisation
---

### Post by philled on 2016-01-07
I have been running KVM on some CentOS 7 servers but have decided instead to get KVM up and running on Ubuntu as that is what all my other servers are based on. The KVM host machine has 3 NICs which are needed because one of its virtual machines is a firewall which needs 3 NICs - 1 for local LAN management interface, 1 for a DMZ and 1 for the WAN internet connection. I had this all working nicely on CentOS but I'm having a problem with the WAN NIC on the Ubuntu KVM host. I think it's because I haven't defined it correctly in /etc/network/interfaces:

[FONT=courier new]auto br0[/FONT]
[FONT=courier new] iface br0 inet static[/FONT]
[FONT=courier new]         address 192.168.0.102[/FONT]
[FONT=courier new]         netmask 255.255.255.0[/FONT]
[FONT=courier new]         network 192.168.0.0[/FONT]
[FONT=courier new]         broadcast 192.168.0.255[/FONT]
[FONT=courier new]         gateway 192.168.0.254[/FONT]
[FONT=courier new]         dns-nameservers 192.168.0.254[/FONT]
[FONT=courier new]         dns-search edwards.local[/FONT]
[FONT=courier new]         bridge_ports em1[/FONT]
[FONT=courier new]         bridge_stp on[/FONT]
[FONT=courier new]         bridge_maxwait 0[/FONT]
[FONT=courier new]
[/FONT][FONT=courier new]# DMZ NIC[/FONT]
[FONT=courier new]auto p255p1[/FONT]
[FONT=courier new]iface p255p1 inet dhcp[/FONT]
[FONT=courier new]
[/FONT][FONT=courier new]# WAN NIC
auto p255p2[/FONT]
[FONT=courier new]iface p255p2 inet dhcp[/FONT]

On the CentOS KVM host the 2 additional NICs don't have IP4 addresses (I'm ignoring the IP6 stuff):

[FONT=courier new]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN[/FONT]
[FONT=courier new]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=courier new]    inet 127.0.0.1/8 scope host lo[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]    inet6 ::1/128 scope host[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP qlen 1000[/FONT]
[FONT=courier new]    link/ether 08:2e:5f:1b:18:02 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::a2e:5fff:fe1b:1802/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new][COLOR=#ff0000]3: enp5s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    link/ether 00:11:0a:55:d9:50 brd ff:ff:ff:ff:ff:ff[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    inet6 fe80::211:aff:fe55:d950/64 scope link[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]       valid_lft forever preferred_lft forever[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]4: enp5s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    link/ether 00:11:0a:55:d9:51 brd ff:ff:ff:ff:ff:ff[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    inet6 fe80::211:aff:fe55:d951/64 scope link[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]       valid_lft forever preferred_lft forever[/COLOR][/FONT]
[FONT=courier new]5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP[/FONT]
[FONT=courier new]    link/ether 08:2e:5f:1b:18:02 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet 192.168.0.103/24 brd 192.168.0.255 scope global br0[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]    inet6 fe80::a2e:5fff:fe1b:1802/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN[/FONT]
[FONT=courier new]    link/ether 52:54:00:04:90:00 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]7: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast master virbr0 state DOWN qlen 500[/FONT]
[FONT=courier new]    link/ether 52:54:00:04:90:00 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]35: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN qlen 500[/FONT]
[FONT=courier new]    link/ether fe:54:00:2e:43:af brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::fc54:ff:fe2e:43af/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]36: macvtap0@enp5s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 500[/FONT]
[FONT=courier new]    link/ether 00:0c:29:79:d4:e5 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::20c:29ff:fe79:d4e5/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]37: macvtap1@enp5s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 500[/FONT]
[FONT=courier new]    link/ether 00:0c:29:79:d4:f2 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::20c:29ff:fe79:d4f2/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]


But on the Ubuntu KVM host the 2 additional NICs do have IP4 addresses, which results in the host's physical NIC getting an IP address from my cable modem, whereas the virtual NIC on the firewall VM should be getting that IP address:

[FONT=courier new]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default[/FONT]
[FONT=courier new]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/FONT]
[FONT=courier new]    inet 127.0.0.1/8 scope host lo[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]    inet6 ::1/128 scope host[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]2: em1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000[/FONT]
[FONT=courier new]    link/ether 08:2e:5f:0e:64:3a brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new][COLOR=#ff0000]3: p255p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    link/ether 00:15:17:2e:62:44 brd ff:ff:ff:ff:ff:ff[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    inet [/COLOR][COLOR=#0000ff]192.168.0.10/24[/COLOR][COLOR=#ff0000] brd 192.168.0.255 scope global p255p1[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]       valid_lft forever preferred_lft forever[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    inet6 fe80::215:17ff:fe2e:6244/64 scope link[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]       valid_lft forever preferred_lft forever[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]4: p255p2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    link/ether 00:15:17:2e:62:45 brd ff:ff:ff:ff:ff:ff[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    inet [/COLOR][COLOR=#0000ff]220.239.102.151/20[/COLOR][COLOR=#ff0000] brd 220.239.111.255 scope global p255p2[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]       valid_lft forever preferred_lft forever[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]    inet6 fe80::215:17ff:fe2e:6245/64 scope link[/COLOR][/FONT]
[FONT=courier new][COLOR=#ff0000]       valid_lft forever preferred_lft foreve[/COLOR]r[/FONT]
[FONT=courier new]5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default[/FONT]
[FONT=courier new]    link/ether 08:2e:5f:0e:64:3a brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet 192.168.0.102/24 brd 192.168.0.255 scope global br0[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]    inet6 fe80::a2e:5fff:fe0e:643a/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default[/FONT]
[FONT=courier new]    link/ether d2:5c:3f:47:92:60 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]7: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500[/FONT]
[FONT=courier new]    link/ether fe:54:00:84:05:c5 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::fc54:ff:fe84:5c5/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]8: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500[/FONT]
[FONT=courier new]    link/ether fe:54:00:fa:f7:f0 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::fc54:ff:fefa:f7f0/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]9: vnet2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500[/FONT]
[FONT=courier new]    link/ether fe:54:00:ca:03:24 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::fc54:ff:feca:324/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]
[FONT=courier new]10: vnet3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500[/FONT]
[FONT=courier new]    link/ether fe:54:00:dc:9b:80 brd ff:ff:ff:ff:ff:ff[/FONT]
[FONT=courier new]    inet6 fe80::fc54:ff:fedc:9b80/64 scope link[/FONT]
[FONT=courier new]       valid_lft forever preferred_lft forever[/FONT]



My old CentOS KVM host had the NICs defined as follows (different format on CentOS than Ubuntu):

/etc/sysconfig/network-scripts/ifcfg-eno1 :
[FONT=courier new]TYPE="Ethernet"[/FONT]
[FONT=courier new]BOOTPROTO="dhcp"[/FONT]
[FONT=courier new]DEFROUTE="yes"[/FONT]
[FONT=courier new]PEERDNS="yes"[/FONT]
[FONT=courier new]PEERROUTES="yes"[/FONT]
[FONT=courier new]IPV4_FAILURE_FATAL="no"[/FONT]
[FONT=courier new]IPV6INIT="yes"[/FONT]
[FONT=courier new]IPV6_AUTOCONF="yes"[/FONT]
[FONT=courier new]IPV6_DEFROUTE="yes"[/FONT]
[FONT=courier new]IPV6_PEERDNS="yes"[/FONT]
[FONT=courier new]IPV6_PEERROUTES="yes"[/FONT]
[FONT=courier new]IPV6_FAILURE_FATAL="no"[/FONT]
[FONT=courier new]NAME="eno1"[/FONT]
[FONT=courier new]#UUID="d514c48c-a68a-43c6-8f70-093f39b128cf"[/FONT]
[FONT=courier new]DEVICE="eno1"[/FONT]
[FONT=courier new]ONBOOT="yes"[/FONT]
[FONT=courier new]BRIDGE=br0[/FONT]

/etc/sysconfig/network-scripts/ifcfg-enp5s0f0 :
[FONT=courier new]DEVICE=enp5s0f0[/FONT]
[FONT=courier new]ONBOOT=no[/FONT]
[FONT=courier new]BOOTPROTO=dhcp[/FONT]
[FONT=courier new]PEERDNS=yes[/FONT]
[FONT=courier new]IPV6INIT=yes[/FONT]
[FONT=courier new]IPV6_AUTOCONF=yes[/FONT]
[FONT=courier new]DHCPV6C=no[/FONT]

/etc/sysconfig/network-scripts/ifcfg-enp5s0f1 :
[FONT=courier new]DEVICE=enp5s0f1[/FONT]
[FONT=courier new]ONBOOT=yes[/FONT]
[FONT=courier new]BOOTPROTO=dhcp[/FONT]
[FONT=courier new]PEERDNS=yes[/FONT]
[FONT=courier new]IPV6INIT=yes[/FONT]
[FONT=courier new]IPV6_AUTOCONF=yes[/FONT]
[FONT=courier new]DHCPV6C=no[/FONT]


Can anyone please tell me how to define the host's physical NICs so that they don't get an IP address and "steal" the cable modem from the VM.

---

### Post by MAFoElffen on 2016-01-09
Could you please post your ubuntu (kvm host) /etc/network/interfaces file so that one of us could try to translsate what you have to what you had?

---

### Post by philled on 2016-01-10
> **MAFoElffen said:**
> Could you please post your ubuntu (kvm host) /etc/network/interfaces file so that one of us could try to translsate what you have to what you had?

Hi there, here's the /etc/network/interfaces file from my Ubuntu KVM host. You can see I've tried with auto on and auto off to see if that made a difference. em1 is working fine just how I want it to. It's the other two interfaces that I'm having problems with.

[FONT=courier new]auto br0[/FONT]
[FONT=courier new] iface br0 inet static[/FONT]
[FONT=courier new]         address 192.168.0.102[/FONT]
[FONT=courier new]         netmask 255.255.255.0[/FONT]
[FONT=courier new]         network 192.168.0.0[/FONT]
[FONT=courier new]         broadcast 192.168.0.255[/FONT]
[FONT=courier new]         gateway 192.168.0.254[/FONT]
[FONT=courier new]         dns-nameservers 192.168.0.254[/FONT]
[FONT=courier new]         dns-search edwards.local[/FONT]
[FONT=courier new]         bridge_ports em1[/FONT]
[FONT=courier new]         bridge_stp on[/FONT]
[FONT=courier new]         bridge_maxwait 0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]### This is the interface definitions for the other 2 NICs on the dual NIC card[/FONT]
[FONT=courier new]#auto p255p2[/FONT]
[FONT=courier new] iface p255p2 inet dhcp[/FONT]
[FONT=courier new] iface p255p1 inet dhcp[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]### This is the interface definitions for the other 2 NICs on the dual NIC card[/FONT]
[FONT=courier new]#auto p255p1[/FONT]
[FONT=courier new]# iface p255p1 inet dhcp[/FONT]
[FONT=courier new]
[/FONT][FONT=courier new]#auto p255p2[/FONT]
[FONT=courier new]# iface p255p2 inet dhcp[/FONT]



Here's the definitions on the other two NICs on my older CentOS server which is what I'm trying to replicate:

[FONT=courier new]DEVICE=enp5s0f0[/FONT]
[FONT=courier new]ONBOOT=no[/FONT]
[FONT=courier new]BOOTPROTO=dhcp[/FONT]
[FONT=courier new]PEERDNS=yes[/FONT]
[FONT=courier new]IPV6INIT=yes[/FONT]
[FONT=courier new]IPV6_AUTOCONF=yes[/FONT]
[FONT=courier new]DHCPV6C=no

[/FONT][FONT=courier new]DEVICE=enp5s0f1[/FONT]
[FONT=courier new]ONBOOT=yes[/FONT]
[FONT=courier new]BOOTPROTO=dhcp[/FONT]
[FONT=courier new]PEERDNS=yes[/FONT]
[FONT=courier new]IPV6INIT=yes[/FONT]
[FONT=courier new]IPV6_AUTOCONF=yes[/FONT]
[FONT=courier new]DHCPV6C=no[/FONT]

---

### Post by MAFoElffen on 2016-01-10
Okay, so look at my interface file. I use the primary NIC (eth2) as my comms to the server host, and it's services, whick kvm (virsh) is part of. I map br0 to my secondary NIC, for my virtual servers and other guests to communicate through. There is docker containers... in mine, but that part does not concern what you have...

My /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# snoopy is eth2 & eth 3

# The primary network interface
auto eth2
iface eth2 inet static
    address 192.168.2.15
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-search ferreiraent.com

# The secondary interface
auto br0
iface br0 inet static
    address 192.168.2.17
    netmask 255.255.255.0
    network 192.168.2.0
    gateway 192.168.2.1
    broadcast 192.168.2.255
    metric 1
    [COLOR=#ff0000]bridge_ports eth3[/COLOR]
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

```
When I ssh into my server:
```
 
Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-74-generic x86_64)
 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Jan 10 17:27:29 PST 2016

  System load:  0.9                 Users logged in:        1
  Usage of /:   57.5% of 492.03GB   IP address for eth2:    192.168.2.15
  Memory usage: 3%                 [COLOR=#ff0000] IP address for br0:     192.168.2.17[/COLOR]
  Swap usage:   0%                  IP address for docker0: 172.17.42.1
  Processes:    167                 IP address for virbr0:  192.168.122.1

  Graph this data and manage this system at:
    https://landscape.canonical.com/

Searching via station...
[caching result Olympia Airport, WA, United States]
Current conditions at Olympia Airport, WA
Last updated Jan 10, 2016 - 07:54 PM EST / 2016.01.11 0054 UTC
   Temperature: 39.0 F (3.9 C)
   Relative Humidity: 88%
   Wind: Calm
   Sky conditions: clear

```
My ifconfig:
```

mafoelffen@snoopy:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:1c:23:da:25:d8  
          inet addr:192.168.2.17  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feda:25d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44557 (44.5 KB)  TX bytes:648 (648.0 B)

docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99  
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:1c:23:da:25:d6  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feda:25d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6755077 (6.7 MB)  TX bytes:7482256 (7.4 MB)

eth3      Link encap:Ethernet  HWaddr 00:1c:23:da:25:d8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47203 (47.2 KB)  TX bytes:680 (680.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1080 (1.0 KB)  TX bytes:1080 (1.0 KB)

lxcbr0    Link encap:Ethernet  HWaddr be:a8:ca:c3:20:bc  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::bca8:caff:fec3:20bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:648 (648.0 B)


virbr0    Link encap:Ethernet  HWaddr a2:59:6f:0b:41:36  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by MAFoElffen on 2016-01-11
And as an aside, in a KVM guest on the Host from the previous post-- Xenial 16.04 LTS server > The ifconfig from that guest, showing active net connections through 3 virtual NIC's with outside-the-host connections of br0, NAT and virbr0.  There would still be the internal vlan network...

---

### Post by philled on 2016-01-14
> **MAFoElffen said:**
> Okay, so look at my interface file. I use the primary NIC (eth2) as my comms to the server host, and it's services, whick kvm (virsh) is part of. I map br0 to my secondary NIC, for my virtual servers and other guests to communicate through. There is docker containers... in mine, but that part does not concern what you have...

My /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# snoopy is eth2 & eth 3

# The primary network interface
auto eth2
iface eth2 inet static
    address 192.168.2.15
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-search ferreiraent.com

# The secondary interface
auto br0
iface br0 inet static
    address 192.168.2.17
    netmask 255.255.255.0
    network 192.168.2.0
    gateway 192.168.2.1
    broadcast 192.168.2.255
    metric 1
    [COLOR=#ff0000]bridge_ports eth3[/COLOR]
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

```

Hi MAFoElffen, thanks very much for this info. So are you suggesting I set up a bridge for my 2nd and 3rd NICs? This is how I was going to do it on my original CentOS host, but some recommendations from a mailing list at the time advised that I use macvlans instead and that's what I'm having trouble reproducing here. Perhaps Ubuntu KVM is different to KVM in this regard, I don't know. I really don't know what the difference between a bridge and a macvlan is. Do you have any comment on that?

---

### Post by MAFoElffen on 2016-01-15
Good explanation:
[http://events.linuxfoundation.org/sites/events/files/slides/LinuxConJapan2014_makita_0.pdf](http://events.linuxfoundation.org/sites/events/files/slides/LinuxConJapan2014_makita_0.pdf)

macvlan is considered a lite implementation. MAC VLAN can be created in one of 4 modes: private, vepa, bridge or passthru... defined at creation time. Default mode is vepa, even though there is not much use of that yet.. 
Good step-by-step
[http://www.bertera.it/index.php/2011/10/04/howto-configure-multiple-mac-address-over-a-single-ethernet-interface/](http://www.bertera.it/index.php/2011/10/04/howto-configure-multiple-mac-address-over-a-single-ethernet-interface/)
```

## Doing it as a bridge to the host's NID...
sudo ip link add virtual0 link eth3 type macvlan mode bridge
sudo ip address add 192.168.2.117/24 broadcast 192.168.2.255 dev virtual0

```
I followed Ubuntu's Bridge Page in the Wiki. It's been okay for what I want on my own subnet and network. I also do some custom config's depending what I'm doing. One of my VM's is a WRT router running in virtual.

I do vSphere here also... so let me share this, which has some good info, which the concepts of can be applied to more than just vSphere:
[https://www.vmware.com/files/pdf/virtual_networking_concepts.pdf]("http://www.bertera.it/index.php/2011/10/04/howto-configure-multiple-mac-address-over-a-single-ethernet-interface/")

*** Remember on adapting from old-school also. We used to take hard servers to use as domain controllers, routers, firewalls, etc. You can always create the same in virtual ... and you don't have to worry how many virtual NIC fit in virtual slots or in the case. So you can bridge an virtual internal network to another virtual network, or to an external network (NAT or your bridge).

And then there is [vlan]("https://wiki.ubuntu.com/vlan") (if that package is installed):
```

# /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# VLAN 1
auto vlan1 
iface vlan1 inet dhcp
vlan_raw_device eth0

# VLAN 2
auto vlan2
iface vlan2 inet static
address 192.168.0.8
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
mtu 1500
vlan_raw_device eth0

```

---

### Post by philled on 2016-01-19
Thanks for trying to help me with this. I'm afraid that preso you pointed to was way out of my league and I didn't understand a word of it. On CentOS this all "just worked" but I've spent hours and hours trying to get this working on Ubuntu and am having no success.

I think I got close at one point. It's difficult to articulate the problem properly. But here goes... on CentOS the 2nd and 3rd host NICs come up and show as "UP" in "ip a" and the their link lights are on when I look at the actual physical NICs at the back of the box. At this stage they don't have an IP address - and that's what I want because it's the VMs that need the IP addresses.

But on Ubuntu, I can get the host NICs to come up, but then the NIC connected to the cable modem gets allocated a WAN IP address by the modem and I don't want that, because the NIC on the virtual machine is the one that must get the WAN IP address.

So how do I get the NICs to be physically UP on boot, with link lights flashing etc, but not grabbing IP addresses? As I say, this "just works" on CentOS and if I could do it on Ubuntu I wouldn't need to be running any CentOS servers.

---

### Post by philled on 2016-01-19
> **philled said:**
> So how do I get the NICs to be physically UP on boot, with link lights flashing etc, but not grabbing IP addresses? As I say, this "just works" on CentOS and if I could do it on Ubuntu I wouldn't need to be running any CentOS servers.
I think I've finally nailed this. The configuration that got it working was to set up 3 bridges (br0, br1 and br2) all with static IPs on 192.168.0.0 network. I hadn't realised that they could all be on the same network - I thought they had to be on the same network that the VMs using them would be on (eg one of the NICs would be on 192.168.1.0). Anyway with this network definition on the host I have got things working:

[FONT=courier new]auto lo
iface lo inet loopback

auto br0
 iface br0 inet static
         address 192.168.0.102
         netmask 255.255.255.0
         network 192.168.0.0
         broadcast 192.168.0.255
         gateway 192.168.0.254
         dns-nameservers 192.168.0.254
         dns-search edwards.local
         bridge_ports em1
         bridge_stp on
         bridge_maxwait 0

auto br1
 iface br1 inet static
         address 192.168.0.111
         netmask 255.255.255.0
         network 192.168.0.0
         broadcast 192.168.0.255
         gateway 192.168.0.254
         dns-nameservers 192.168.0.254
         dns-search edwards.local
         bridge_ports p255p1
         bridge_stp on
         bridge_maxwait 0

auto br2
 iface br2 inet static
         address 192.168.0.112
         netmask 255.255.255.0
         network 192.168.0.0
         broadcast 192.168.0.255
         gateway 192.168.0.254
         dns-nameservers 192.168.0.254
         dns-search edwards.local
         bridge_ports p255p2
         bridge_stp on
         bridge_maxwait 0[/FONT]

On my Sophos UTM firewall VM I have defined the network sources for the VM's NICs as:
eth0 = Bridge br0: Host Device em1
eth1 = Bridge br1: Host device vnet5
eth2 = Bridge br1: Host device vnet6

Not sure where vnet5 and vnet6 come from but it's working so I'm not going to mess with it!

I have to say that I preferred how it worked on CentOS with eth1 and eth2 using macvtap devices as their sources, but I couldn't get macvtap to work on Ubuntu. When I tried it I got an error saying the macvtap device was already in use, but I don't know what was using it.

Thanks for all your help. Sorry it took me so long to get working!

---

### Post by philled on 2016-01-20
OK, so I have now *finally* got it how I want it. After a lot of googling, I realised that what I wanted to know is how to bring up a network interface without giving it an IP address. Two of my NICs needed to be physically up but not have an IP address. The page at [http://ubuntuforums.org/showthread.php?t=830481](http://ubuntuforums.org/showthread.php?t=830481) showed me the way, which is to define the network interface not as DHCP, or STATIC, but MANUAL. I didn't realise you could do that. 

So my /etc/network/interfaces file now looks like this:

```
auto lo
iface lo inet loopback

auto br0
 iface br0 inet static
         address 192.168.0.102
         netmask 255.255.255.0
         network 192.168.0.0
         broadcast 192.168.0.255
         gateway 192.168.0.254
         dns-nameservers 192.168.0.254
         dns-search edwards.local
         bridge_ports em1
         bridge_stp on
         bridge_maxwait 0

auto p255p1
iface p255p1 inet manual
up ifconfig p255p1 up

auto p255p2
 iface p255p2 inet manual
 up ifconfig p255p2 up
```

These NICs are physically up which means they can be used as a network source for VMs, but they don't have IP addresses:

```
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: em1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
    link/ether 08:2e:5f:0e:64:3a brd ff:ff:ff:ff:ff:ff
3: p255p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:15:17:2e:62:44 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::215:17ff:fe2e:6244/64 scope link
       valid_lft forever preferred_lft forever
4: p255p2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:15:17:2e:62:45 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::215:17ff:fe2e:6245/64 scope link
       valid_lft forever preferred_lft forever
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
    link/ether 08:2e:5f:0e:64:3a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.102/24 brd 192.168.0.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::a2e:5fff:fe0e:643a/64 scope link
       valid_lft forever preferred_lft forever
6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 4e:12:ee:b9:60:ea brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:84:05:c5 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe84:5c5/64 scope link
       valid_lft forever preferred_lft forever
8: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:dc:9b:80 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fedc:9b80/64 scope link
       valid_lft forever preferred_lft forever
9: vnet2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:fa:f7:f0 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fefa:f7f0/64 scope link
       valid_lft forever preferred_lft forever
10: vnet3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:ca:03:24 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:feca:324/64 scope link
       valid_lft forever preferred_lft forever
11: vnet4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:ea:a7:40 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:feea:a740/64 scope link
       valid_lft forever preferred_lft forever
12: macvtap0@p255p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/ether 00:0c:29:79:d4:e5 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::20c:29ff:fe79:d4e5/64 scope link
       valid_lft forever preferred_lft forever
13: macvtap1@p255p2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/ether 00:0c:29:79:d4:f2 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::20c:29ff:fe79:d4f2/64 scope link
       valid_lft forever preferred_lft forever
```



This is much better from a security perspective as you can isolate DMZ from LAN etc as there's no IP address to get connectivity through. Also, macvtap is supposed to put less drain on the server than a bridge. 

I hope this helps someone in future.

---

### Post by MAFoElffen on 2016-01-20
(I posted example of "manual" in post #4)

Are you good now? Please go back and edit/reformat your last post... to put that output within 'code' tags(?) The forum's policy, and easier for others to read.

Then. if working for you now, go to the link at the top left of this page, Thread Tools > Mark thread as "Solved."

---

### Post by philled on 2016-01-20
> **MAFoElffen said:**
> (I posted example of "manual" in post #4)
Sorry, I must have missed it or not realised the significance of it. I just had a look back at post #4 and I actually still can't see any of the interfaces defined as "manual". They look to be "static".

> **MAFoElffen said:**
> Please go back and edit/reformat your last post... to put that output within 'code' tags(?) The forum's policy, and easier for others to read.
Then. if working for you now, go to the link at the top left of this page, Thread Tools > Mark thread as "Solved."
Done. 

Thanks again for your help.

---

### Post by MAFoElffen on 2016-01-20
You are very welcome. Anytime.

---

