---
title: "vm's cannot get DHCP address from headless ubuntu 16.04 server"
date: 2016-07-29
forum: Virtualisation
---

### Post by jleiss on 2016-07-29
Hello, i've spent hours looking over this but unable to find a solution. I am unable to get my virtual machines proper network connectivity. My setup is a headless ubuntu 16.04 server with virtualbox 5.1.2 with bridge networking setup.

the headless server connects and pulls a DHCP address fine and can talk to everything, but the VM's cannot whether DHCP or manual network config.

here is my network config for the headless server

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto enp2s0
#iface enp2s0 inet dhcp

# The primary network interface
auto br0
iface br0 inet dhcp
    bridge_ports enp2s0

iface eth0 inet manual


and here is the ifconfig -a output for that server

jleiss@ubuntu:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:26:2d:87:93:69  
          inet addr:192.168.0.203  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe87:9369/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:706418892 (706.4 MB)  TX bytes:6816311 (6.8 MB)

enp2s0    Link encap:Ethernet  HWaddr 00:26:2d:87:93:69  
          inet6 addr: fe80::226:2dff:fe87:9369/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:492807 errors:0 dropped:2 overruns:0 frame:0
          TX packets:84288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:735611877 (735.6 MB)  TX bytes:7182685 (7.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)

wlp4s0    Link encap:Ethernet  HWaddr c4:17:fe:a9:e3:53  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Any help on why my machines don't get connecivity?

---

### Post by ajgreeny on 2016-07-29
I can not really help you with a proper solution to this problem apart from mentioning that I had big difficulties with VBox 5.1 when I tried it a week or two ago.

I use Xubuntu 14.04 as the host and all the 4.3 and 5.0. versions have given me none, or very few problems ever.
When I noticed 5.1 was available I immediately tried it but it was a major problem with graphics, USBs, and networking.  I did not bother trying to solve this but immediately downgraded back to the 5.0.# version.  With that version, immediately the problems went away.

Perhaps worth trying that yourself to see if you have the same success with Vbox-5.0.26, the current version.

---

### Post by jleiss on 2016-07-29
> **ajgreeny said:**
> I can not really help you with a proper solution to this problem apart from mentioning that I had big difficulties with VBox 5.1 when I tried it a week or two ago.

I use Xubuntu 14.04 as the host and all the 4.3 and 5.0. versions have given me none, or very few problems ever.
When I noticed 5.1 was available I immediately tried it but it was a major problem with graphics, USBs, and networking.  I did not bother trying to solve this but immediately downgraded back to the 5.0.# version.  With that version, immediately the problems went away.

Perhaps worth trying that yourself to see if you have the same success with Vbox-5.0.26, the current version.


Thanks I did that and my networking works!

---

### Post by ajgreeny on 2016-07-29
Great! Please mark as SOLVED from the Thread Tools menu at the top; it is a great help for users searching the forum.

---

