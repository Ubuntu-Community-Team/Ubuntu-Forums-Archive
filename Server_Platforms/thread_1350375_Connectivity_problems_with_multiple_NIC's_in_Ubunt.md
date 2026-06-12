---
title: "Connectivity problems with multiple NIC's in Ubuntu Server 9.10"
date: 2009-12-09
forum: Server Platforms
---

### Post by ejay563 on 2009-12-09
Hello All, 

I have a shiny new server at work, and it's my job to set it up the way I want/need it to work. It has 2 NICS built in, and I would like to take advantage of them, as I am running a couple virtual servers with KVM on it. However, when I set them up to both run at the same time, whether it be with DHCP or static ip, I lose connectivity to the internet, although the internal network seems to be fine. When I take one of the interfaces down, internet connectivity returns (both with dhcp and static ip). I've done some google searches, but have not found anything regarding an issue such as this. I am running Ubuntu Server 9.10 amd64. Any help would be greatly appreciated.

~ejay563

---

### Post by ejay563 on 2009-12-17
Linux 1, me 0. Any ideas, or requests for information that may be helpful? I am by no means a Linux expert, and do not know what information would be helpful in this case. I would really appreciate your help!:confused:

---

### Post by windependence on 2009-12-17
Can you post an ifconfig, the contents of your /etc/resolv.conf, /etc/network/interfaces, and /etc/hosts?

Once we have that info, we can better tell what to do next.

-Tim

---

### Post by Iowan on 2009-12-17
*/etc/network/interfaces* will probably show it, too, but **route** might reveal if there are multiple (default) gateways.

---

### Post by ejay563 on 2009-12-29
Hi, sorry for the delay in a response. I though I would get an e-mail when a response was posted like I have in the past. Here are the requested items.

ifconfig
```

br0       Link encap:Ethernet  HWaddr 00:24:e8:44:90:66  
          inet addr:10.115.110.10  Bcast:10.115.110.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe44:9066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25103140 (25.1 MB)  TX bytes:40931 (40.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:24:e8:44:90:66  
          inet6 addr: fe80::224:e8ff:fe44:9066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41624299 (41.6 MB)  TX bytes:22675608 (22.6 MB)
          Interrupt:16 Memory:da000000-da012800 

eth1      Link encap:Ethernet  HWaddr 00:24:e8:44:90:67  
          inet6 addr: fe80::224:e8ff:fe44:9067/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100310 errors:1 dropped:0 overruns:0 frame:1
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26887059 (26.8 MB)  TX bytes:2222 (2.2 KB)
          Interrupt:17 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1032 (1.0 KB)  TX bytes:1032 (1.0 KB)

virbr0    Link encap:Ethernet  HWaddr ea:51:38:39:12:b1  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr d6:92:cd:d1:82:f4  
          inet6 addr: fe80::d492:cdff:fed1:82f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:9209217 (9.2 MB)  TX bytes:33174051 (33.1 MB)

vnet1     Link encap:Ethernet  HWaddr ca:82:42:b2:90:60  
          inet6 addr: fe80::c882:42ff:feb2:9060/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:12867862 (12.8 MB)  TX bytes:34153986 (34.1 MB)


```.

/etc/resolv.conf
```
domain fateb.local
search fateb.local
nameserver 10.115.110.13
```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

#The secondary network interface
#auto eth1
#iface eth1 inet dhcp

#Virtual Bridge for webserver
auto br0
iface br0 inet static
	address 10.115.110.10
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
	bridge_ports eth0
	bridge_stp off
	bridge_fd 0
	bridge_maxwait 0

```
*Note that eth1 is commented out because when it is not, it causes the connectivity problems

/etc/hosts
```
127.0.0.1	localhost
127.0.1.1	FATEB.FATEB	FATEB

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.115.110.0    *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         gw.fateb.local  0.0.0.0         UG    100    0        0 br0

```

I recently was successful at setting up a virtual DNS server on top of this server at 10.115.110.13 if that makes any difference. Thanks!

---

### Post by ejay563 on 2010-02-03
Ok, after some input from a friend, I have decided that bonding the NICS would be the way to go. I followed a combination of the following links: [NIC Bonding/Teaming]("http://www.howtoforge.com/nic_bonding"), [Modbrobe.d aliases File Gone]("http://ubuntuforums.org/showthread.php?t=1147741"), and [Setting Up Dual-Dual NIC Bonding On Ubuntu In 30 Seconds]("http://linuxshellaccount.blogspot.com/2009/01/setting-up-dual-dual-nic-bonding-on.html"). By taking relevent information form these three sources, I got the bond working for a bit, but then it stopped. I have no idea why it stopped, but now when I do:```
$ sudo /etc/init.d/netowrking restart
``` I get: ```
SIOCDELRT: No such process
``` I will attach the files I posted above which have been modified since they were posted. I greatly appreciate any ideas any one may have.

---

### Post by KiLaHuRtZ on 2010-02-03
Lol, just answered one of these questions not that long ago.  Scrap the bridge and your current bond settings and follow my instructions in this post.

[http://ubuntuforums.org/showpost.php?p=8763893&postcount=3]("http://ubuntuforums.org/showpost.php?p=8763893&postcount=3")

P.S., there are other modes you can use besides "active-backup".  Google "ifenslave" and you'll get some more info.  Also, if you do not want the "preempt", leave out the part "primary=XXX".

---

### Post by ejay563 on 2010-02-03
> **KiLaHuRtZ said:**
> Scrap the bridge... 


Thanks for the reply. I will give it a try when the power is more stable. I just have a question. If i am to scrap the bridge, how am I to provide my virtual machines with a connection? Do you think it will work if I just change the connection from br0 to bond0 in the xml file? For the KVM Ntworking I followed the instruction [Here]("https://help.ubuntu.com/community/KVM/Networking"). So, I'm assuming I would change this example machine:
```
<interface type='bridge'>
      <mac address='00:11:22:33:44:55'/>
      <source bridge='br0'/>
    </interface>

```
to
```
<interface type='bridge'>
      <mac address='00:11:22:33:44:55'/>
      <source bridge='bond0'/>
    </interface>

```
Thanks!

---

### Post by KiLaHuRtZ on 2010-02-03
Oh, I must have missed that part.  That may work, but it might be best to create the bond and then a bridge to the bond.  The bond will provide the fault tolerance you seek, however you may still need a bridge from the bond to your virtual machines.  See if this makes sense to you...

```
NET     NET
 |       |
 |       |
 +---+---+
eth0 | eth1
     |
 +---+---> Local Machine
 | bond0
 |
 +-------> Virtual Machines
br0
```

---

### Post by ejay563 on 2010-02-03
Yes, that makes sense. I'll give it a try and let you know how it works. Thanks for the clarification.

---

### Post by KiLaHuRtZ on 2010-02-03
Perhaps add this to '/etc/network/interfaces' in adjacent to the bond config from my post.

```
auto br0
iface br0 inet static
        address 10.115.110.10
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
        bridge_ports bond0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        metric 1

auto br1
iface br1 inet static
        address 10.115.110.11
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
        bridge_ports bond0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        metric 1

auto br2
iface br2 inet static
        address 10.115.110.12
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
        bridge_ports bond0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        metric 1

etc...
```

---

### Post by ejay563 on 2010-02-04
OK, I took out everything I did yesterday for the bond0 interface, and followed the instructions you gave me KiLaHuRtZ, and now it says there is no interface bond0.I looked everything over twice, and it is how you instructed, so I'm not sure what's going wrong. Here are the files for you to take a look at.
/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

bonding modde=active-backup miimon=100 

```
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#create an interface for both NICs
auto bond0
iface bond0 inet static
	address 10.115.110.15
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
	post-up ifenslave bond0 eth0 eth1
	pre-down ifenslave -d bond0 eth0 eth1

#Virtual Bridge for virtual machines
auto br0
iface br0 inet static
	address 10.115.110.15
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
	bridge_ports bond0
	bridge_stp off
	bridge_fd 0
	bridge_maxwait 0
	metric 1

auto br1
iface br1 inet static
	address 10.115.110.16
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
	bridge_ports bond0
	bridge_stp off
	bridge_fd 0
	bridge_maxwait 0
	metric 1


```

Any ideas on what to try next?

Thanks!

---

### Post by KiLaHuRtZ on 2010-02-04
Look closer at what you have...

```
bonding [COLOR="Red"]modde[/COLOR]=active-backup miimon=100
```

That should be...

```
bonding [COLOR="Green"]mode[/COLOR]=active-backup miimon=100
```

Also, make sure you reboot so the kernel can load the necessary modules.

---

### Post by KiLaHuRtZ on 2010-02-04
Also, each interface needs its own unique IP address.  And I would point the gateway address of your 'br#' interfaces to the IP address of 'bond0'.

---

### Post by ejay563 on 2010-02-05
OK, I fixed the typo (and just so you don't think I'm a complete idiot, I am legally blind, and the server does not have magnification capabilities, but still, I should have caught it.), and changed the /etc/network/interfaces to conform to your recommendations. Now ifconfig gives me this:```
bond0     Link encap:Ethernet  HWaddr 00:24:e8:44:90:66  
          inet6 addr: fe80::224:e8ff:fe44:9066/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:1059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:225217 (225.2 KB)  TX bytes:4795 (4.7 KB)

br0       Link encap:Ethernet  HWaddr 00:24:e8:44:90:66  
          inet addr:10.115.110.16  Bcast:10.115.110.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe44:9066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102136 (102.1 KB)  TX bytes:468 (468.0 B)

eth0      Link encap:Ethernet  HWaddr 00:24:e8:44:90:66  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113027 (113.0 KB)  TX bytes:4795 (4.7 KB)
          Interrupt:16 Memory:da000000-da012800 

eth1      Link encap:Ethernet  HWaddr 00:24:e8:44:90:66  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112190 (112.1 KB)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

virbr0    Link encap:Ethernet  HWaddr 02:5c:a7:47:3e:ca  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr 56:c0:3c:c3:23:59  
          inet6 addr: fe80::54c0:3cff:fec3:2359/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3152 (3.1 KB)  TX bytes:111151 (111.1 KB)

vnet1     Link encap:Ethernet  HWaddr c6:cb:02:68:43:71  
          inet6 addr: fe80::c4cb:2ff:fe68:4371/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1390 (1.3 KB)  TX bytes:110437 (110.4 KB)


```
and when I try to restart the networking service, I get this:```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
SIOCDELRT: No such process
                                                                                                                            [ OK ]


```

I also ended up having to comment out the second bridge, otherwise I got this:```
$ sudo /etc/init.d/networking restart * Reconfiguring network interfaces...                                          
SIOCDELRT: No such process
device bond0 is already a member of a bridge; can't enslave it to bridge br1.
                                                                                                                           [ OK ]

```

Here are the updated config files
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#create an interface for both NICs
auto bond0
iface bond0 inet static
	address 10.115.110.15
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
	post-up ifenslave bond0 eth0 eth1
	pre-down ifenslave -d bond0 eth0 eth1

#Virtual Bridge for virtual machines
auto br0
iface br0 inet static
	address 10.115.110.16
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.15
	bridge_ports bond0
	bridge_stp off
	bridge_fd 0
	bridge_maxwait 0
	metric 1

#auto br1
#iface br1 inet static
#	address 10.115.110.17
#	network 10.115.110.0
#	netmask 255.255.255.0
#	broadcast 10.115.110.255
#	gateway 10.115.110.15
#	bridge_ports bond0
#	bridge_stp off
#	bridge_fd 0
#	bridge_maxwait 
```
/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

bonding mode=active-backup miimon=100 

```
So why isn't bond0 getting the IP address, and what's the SIOCDELRT thing?

Thanks

---

### Post by ejay563 on 2010-02-05
Other Questions:

Since an interface can seemingly only be included in one bridge, would it be more efficient to go with my original idea in trying to create a bridge for each physical NIC? So, the webserver would use br0, and the DNS server would use br1, br0 would connect to eth0, and br1 would connect with eth1. 

If yes to above, back to my original question, how can I get both interfaces working on the same network at the same time (with their own ip address of course)? I'm widely open to any suggestion at this point. 

Thanks again!

---

### Post by KiLaHuRtZ on 2010-02-05
In that, just trash the bridge interfaces altogether and try this...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#create an interface for both NICs
auto bond0
iface bond0 inet static
	address 10.115.110.15
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255
	gateway 10.115.110.1
	post-up ifenslave bond0 eth0 eth1
	pre-down ifenslave -d bond0 eth0 eth1

[COLOR="Blue"]auto bond0:0
iface bond0:0 inet static
	address 10.115.110.16
	network 10.115.110.0
	netmask 255.255.255.0
	broadcast 10.115.110.255[/COLOR]
```

---

### Post by KiLaHuRtZ on 2010-02-05
And you can add as many addresses as you want...

bond0:1
bond0:2
bond0:3
bond0:4 ... etc

Then just assign and interface/address to each virtual machine directly.  Bridging is not even required at this point.

---

### Post by ejay563 on 2010-02-08
Sorry, that didn't work either. I'm just going to use 1 NIC for now, and maybe in a year or two when things get straightened out I'll try again. I have more important things to do than get this stupid bond working. I did do some testing, and the bond itself works on the physical server, but there's no good way to route it to the VM's. Well, thanks for the effort. 

~ejay563

---

