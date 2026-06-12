---
title: "Ubuntu server 10.04 LTS x64 (subnet) behind a router"
date: 2011-05-04
forum: Server Platforms
---

### Post by dawnne on 2011-05-04
Hello All
I am trying to set up a subnet using the Linksys router (for trial only) which is attached to company LAN (Windows Server 2003) with static IP address.

[Setup]
Two Ubuntu boxes are linked to the router:
A server with static IP address: 192.168.1.101
And a desktop with dynamic IP: 192.168.1.102

[Outcome]
The server cannot access to internet.
Ping the desktop
$ ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
...

Ping the router, got a similar message.
Its routing table
$ route -n
Destination   Gateway       Genmask         Flags  Metric  Fef   Use  Iface
192.168.2.0   0.0.0.0       255.255.255.0   U      0       0     0    eth1
192.168.1.0   0.0.0.0       255.255.255.0   U      0       0     0    eth0
0.0.0.0       192.168.1.1   0.0.0.0         UG     0       100   0    eth0

On the other hand, the desktop works just find with auto detect network connection
Ping the router is fine and also good if ping the outside of the router (i.e. our company LAN) except the server (192.168.1.101)

The desktop's routing table
$ route -n
Destination   Gateway       Genmask         Flags  Metric  Fef   Use  Iface
192.168.1.0   0.0.0.0       255.255.255.0   U      0       0     0    eth0
0.0.0.0       192.168.1.1   0.0.0.0         UG     0       0     0    eth0

[Settings...]
The server (192.168.1.101)
# /etc/network/interfaces
# This file was empty, and I have added the following lines
auto lo
iface lo inet loopback

# Build-in NIC with one interface
auto eth0
iface eth0 inet static
   address 192.168.1.101
   network 192.168.1.0
   netmask 255.255.255.0
   broadcast 192.168.1.255
   gateway 192.168.1.1

# Second NIC with two interfaces
# 1st interface
auto eth1
iface eth1 inet static
   address 192.168.1.100
   network 192.168.1.0
   netmask 255.255.255.0
   broadcast 192.168.1.255

# Second NIC with two interfaces
# 2nd interface
# Not configured yet

The desktop (192.168.1.102)
# /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

Note. I have installed around 10 Ubuntu desktop with no connection problem regardless I use LAN connection or behind Linksys router.

Please help me.  Thanks!

Dawnne

---

### Post by volkswagner on 2011-05-04
> **dawnne said:**
> 

Ping the router, got a similar message.
Its routing table
$ route -n
Destination   Gateway       Genmask         Flags  Metric  Fef   Use  Iface
192.168.2.0   0.0.0.0       255.255.255.0   U      0       0     0    eth1
192.168.1.0   0.0.0.0       255.255.255.0   U      0       0     0    eth0
0.0.0.0       192.168.1.1   0.0.0.0         UG     0       100   0    eth0


[Settings...]
The server (192.168.1.101)
# /etc/network/interfaces
# This file was empty, and I have added the following lines
auto lo
iface lo inet loopback

# Build-in NIC with one interface
auto eth0
iface eth0 inet static
   address 192.168.1.101
   network 192.168.1.0
   netmask 255.255.255.0
   broadcast 192.168.1.255
   gateway 192.168.1.1

# Second NIC with two interfaces
# 1st interface
auto eth1
iface eth1 inet static
   address 192.168.1.100
   network 192.168.1.0
   netmask 255.255.255.0
   broadcast 192.168.1.255



It seems to me that your info does not agree.  

route -n for eth1 does not match your /network/interfaces file (notice the '2' in third octet).

Also what is the dhcp range of the router.  It seems your static addressing is possibly inside the dynamic range.

Can you try dhcp on the server to see if it can connect to the gateway?
When you run

```
ifconfig
```

on the desktop, do the network settings match those for your static settings (gateway, netmask, etc.)?

Did you restart networking service or reboot after making the changes?

An acceptable sometimes preferred way to set static ip is via the router, assigning an ip to the mac address.  This allows DHCP to be set on the card, and can help with local DNS resolution.

---

### Post by dawnne on 2011-05-04
Hi volkswagner
 
Thanks for your response.  You are right. I did not correctly copy the second NIC info, sorry.
 
In the actually /etc/network/interfaces file, it looks like the following:
 
# Second NIC with two interfaces
# 1st interface
auto eth1
iface eth1 inet static
   address 192.168.2.1
   network 192.168.2.0
   netmask 255.255.255.0
   broadcast 192.168.2.255
 
Our LAN network is 10.160.24.0 and I set the router with a static IP 10.160.24.200 (use WAN port), and the router switches for two Ubuntu boxes with dhcp range from 192.168.1.100 to 192.168.1.144 (I need to check the range value).
 
I have tried the server eth0 with dhcp, 
 
auto eth0
iface eth0 inet dhcp
 
then restart network,
 
$ sudo /etc/init.d/networking restart
 
I got an error message couldn't find some file and something else... (I cannot remember, tomorrow I will have a look at work)
 
Also, I will try what you suggested, thanks a lot.
 
Dawnne

---

### Post by dawnne on 2011-05-05
Server (192.168.1.101) with static IP address after restart network...

* Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
ssh stop/waiting
ssh start/running, process 3290
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
ssh stop/waiting
ssh start/running, process 3348
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
                                                                                                 [OK]
$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:10:18:93:be:60
     inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
     UP BROADCAST MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
     Interrupt:16 Memory:da000000-da012800

---

### Post by dawnne on 2011-05-05
Tried:
1. Ubuntu server eth0 setting (use dhcp)
/etc/network/interfaces file
# The primary network interface
auto eth0
iface eth0 inet dhcp

Restart network
$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pic with pid 2439
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:10:18:93:be:60
Sending on LPF/eth0/00:10:18:93:be:60
Sending on Socket/fallback
DHCPDISOVER on eth0 to 255.255.255.255 port 67 intervval 7
DHCPDISOVER on eth0 to 255.255.255.255 port 67 intervval 9
DHCPDISOVER on eth0 to 255.255.255.255 port 67 intervval 14
DHCPDISOVER on eth0 to 255.255.255.255 port 67 intervval 20
DHCPDISOVER on eth0 to 255.255.255.255 port 67 intervval 11
No DHCPDISOVER received.
No working leases in persistent database - sleeping.
ssh stop/waiting
ssh start/running, process 2972
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
ssh stop/waiting
ssh start/running, process 3034
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
                                                                      [OK]

Check the routing table and interfaces
$ route -n
Destination   Gateway       Genmask         Flags  Metric  Fef   Use  Iface
192.168.2.0   0.0.0.0       255.255.255.0   U      0       0     0    eth1

$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:10:18:93:be:60
     UP BROADCAST MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
     Interrupt:16 Memory:da000000-da012800

---

### Post by dawnne on 2011-05-05
Also tried:
2. Ubuntu server eth0 setting (set it to the same as desktop (192.168.1.102)
/etc/network/interfaces file
# The primary network interface
auto eth0
#iface eth0 inet dhcp

Restart network
$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Ignoring unknown interface eth0=eth0.
ssh stop/waiting
ssh start/running, process 2640
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
                                                                      [OK]

Check the routing table and interfaces
$ route -n
Destination   Gateway       Genmask         Flags  Metric  Fef   Use  Iface
192.168.2.0   0.0.0.0       255.255.255.0   U      0       0     0    eth1

$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:10:18:93:be:60
     UP BROADCAST MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
     Interrupt:16 Memory:da000000-da012800

---

### Post by volkswagner on 2011-05-05
Hmn,  is this a fresh install?  Did you follow any how-to's?  I see one error that puzzles me:

```
ignoring unknown interface eth0=eth0
```


I am curious if it is a hardware issue as far as drivers not loaded.  Perhaps there is some sort of config conflict.

Did you bind any interface to a service already?

What type of cards are installed?
```
lspci -v | grep Network
```


Perhaps dmesg can shed some light what is going on.  Can you check your log.

```
less /var/log/dmesg
```

You can search for eth0 with less if you don't know how... Lead your search query with /

```
/eth0
```
then just hit enter, use 'n' for next occurrence.

---

### Post by dawnne on 2011-05-05
Hi volkswagner
 
I have tried to install VMware ESXi once before install Ubuntu server.  Then I was thinking install Ubuntu server and Windows server on VMs due to Dell technician claimed that VMware ESXi works on T110, but I found S100 RAID only works with Windows.  So, I give up on VMware.
 
Now, I install Ubuntu server (kind fresh) with RAID 1 (with Ubuntu software RAID).  Right after installation, I have checked the interfaces (ifconfig), I can see there was a "virbr0", so I guess that is from VMware.
 
I "uninstalled" the virbr0.
 
Another thing is most Ubuntu desktop version that I installed has a link-local 169.254.0.0 in the routing table.  But my Ubuntu server's routing table does not show it.
 
Anyway, the reason that I am doing this is try to get the server work, then move part users (400+) from Windows network to Ubuntu network.
 
I do appreciate your help.
 
Dawnne
P.S.  Tomorrow I will try your suggested codes, thanks.

---

### Post by dawnne on 2011-05-06
Used lspci -v, I got:

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
Subsystem: Broadcom Corporation Device 0907
Flages: bus master, fast devsel, latency 0, IRQ 16
Memory at da000000 (64-bit, non-prefetchable) [size=32M]
Capabilities: <access denied>
Kernel driver in use: bnx2
Kernel modules: bnx2

03:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
Subsystem: Broadcom Corporation Device 0907
Flages: bus master, fast devsel, latency 0, IRQ 17
Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
Capabilities: <access denied>
Kernel driver in use: bnx2
Kernel modules: bnx2

04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
Subsystem: Dell Device 02a6
Flages: bus master, fast devsel, latency 0, IRQ 16
Memory at df1f0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: tg3
Kernel modules: tg3

I just wonder that "03:00.0 Ethernet controller" (plug-in) and "04:00.0 Ethernet controller" (built-in) are sharing the same IRQ 16 ???

---

### Post by dawnne on 2011-05-06
Opened the following file
/var/log/dmesg
...
[1.774492] eth0: Tigon3 [partno(BCM95722) rev a200] (PCI Express) MAC address bc:30:5b:d8:11:71
[1.774494] eth0: attached PHY is 5722/5756 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[1.774496] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[1.774498] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
...
[12.867247]  eth1: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found  at mem da000000, IRQ 16, node addr 00:10:18:93:be:60
...
[12.869712] eth2: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI  Express found at mem dc000000, IRQ 17, node addr 00:10:18:93:be:62
[12.882282] udev: renamed network interface eth1 to eth0
[12.882836] udev: renamed network interface eth2 to eth1
[12.932204] udev: renamed network interface eth0_rename to eth2
...

Don't know why eth* are swapped, but I have just swapped them back.  Now I can ping other machines.  The problem is solved :)

Thank you, volkswagner!!!

Dawnne

---

### Post by alain.roger on 2011-12-16
Hi,

i have thesame issue eth0 is rename to eth1.

how di you solve this issue ?

---

### Post by thor.cms on 2012-04-13
Can you elaborate on HOW you opened the /var/log/dmesg file and edited it for we novices?

---

