---
title: "[SOLVED] Can't ping from Linux host to Windows VM guest"
date: 2008-11-17
forum: Virtualisation
---

### Post by akelsall on 2008-11-17
I've tried several different ways to get connectivity between my Linux host and WinXP guest (running inside VirtualBox) with some luck, but I need some help.

As it stands now, I can ping both my Linux host and my gateway (which is my router) from within VBox. However, I can NOT ping the WinXP guest from the Linux host. 

I'm using Eth1 to connect to the Internet (via my router) and have it configured with an IP of 192.168.2.8 / 24 (see below). My WinXP guest is set for DHCP, which is working fine (the router is providing a pool of addresses to draw from). The following is the output that might help someone show me what I've done wrong:


cat /etc/network/interfaces
auto lo
iface lo inet loopback
#
auto tap0
iface tap0 inet manual
tunctl_user hiker
uml_proxy_arpa 192.168.2.8
uml_proxy_ether eth1
#
auto eth1
iface eth1 inet static
address 192.168.2.8
netmask 255.255.255.0
gateway 192.168.2.1
#
auto br0
iface br0 inet static
address 192.168.2.8
netmask 255.255.255.0
gateway 192.168.2.1
bridge_ports eth1 tap0
bridge_maxwait 0
=============================

Output from ifconfig (I deleted the output of Eth0, since it's not in use):

br0       Link encap:Ethernet  HWaddr 00:11:09:2d:55:a0  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe2d:55a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:296230 (289.2 KB)  TX bytes:94169 (91.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:11:09:2d:55:a0  
          inet6 addr: fe80::211:9ff:fe2d:55a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6335407 (6.0 MB)  TX bytes:484898 (473.5 KB)
          Interrupt:20 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128209 (125.2 KB)  TX bytes:128209 (125.2 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:b0:a5:7b:7c  
          inet6 addr: fe80::2ff:b0ff:fea5:7b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2470 errors:0 dropped:55 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:99179 (96.8 KB)  TX bytes:2870780 (2.7 MB)
==================================================================

$ route
Kernel IP routing table
Destination  Gateway Genmask       Flags Metric   Ref    Use Iface
192.168.2.0     *    255.255.255.0   U    0        0     0   br0  link-local      *   255.255.0.0     U     1000   0        0 br0
default    192.168.2.1  0.0.0.0         UG    100    0        0 br0

========================================================

$brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.0011092d55a0	no		eth1
							tap0
==============================================================

Here's the output of ipconfig in the VM (running WinXP Pro):

C:\>ipconfig
Windows IP Configuration

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : Pinetree
        IP Address. . . . . . . . . . . . : 192.168.2.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
==============================================================

I did stop and start network services (**sudo /etc/init.d/networking [start | stop]** before and after making the changes, and even rebooted with no change.

Also, I do have the VM set to use the Host interface with the interface name set to tap0.

I could sure use some help with this one. It's driving me nuts (but it has been a good learning experience. Never would have learned about starting and stopping network services, or the interfaces file).

Thanks,

Andy

---

### Post by akelsall on 2008-11-25
bump

---

### Post by akelsall on 2008-12-11
Not getting much help on this one, so marking it SOLVED to close it out.

---

### Post by PilotJLR on 2008-12-11
No need to mark as solved if it isn't.  :-)


For the XP guest... is the firewall on? XP has the firewall on by default, which will block pings.

---

### Post by akelsall on 2008-12-11
I've tried it with the FW enabled and disabled with no change. I think this weekend I'll try using NAT and see how that works.

---

### Post by PilotJLR on 2008-12-11
Pinging the guest shouldn't work in NAT mode... you would have to have the guest in bridged mode for this to work. Or "supposed" to work.  :-)

---

