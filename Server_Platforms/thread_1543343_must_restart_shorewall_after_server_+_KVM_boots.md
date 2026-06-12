---
title: "must restart shorewall after server + KVM boots"
date: 2010-07-31
forum: Server Platforms
---

### Post by DrJohn999 on 2010-07-31
This 9.10 server has two KVM virtual servers that autostart; shorewall-perl 4.2.10 provides NAT/SNAT to and from a multi-IP address eth0 interface, as well as the local 192.168.x.x interfaces. The KVM machine creates a virtual bridge virbr0 and assigns IP addresses for each of the VMs on the bridge at vnet0 and vnet1.

After rebooting the machine, the KVM VMs come up without any errors, and so does Shorewall, but it comes up in a non-working configuration and does not give access to the KVMs or across eth0 for that matter until it's restarted manually.

If I disable the autostart of the KVM machines (through virsh) then the system comes up with Shorewall working properly. Starting the VMs manually at this point puts Shorewall into the same state so it must be restarted to get it going.

Clearly Shorewall isn't picking up some piece of information about the VM interfaces until they are up.

I want to know if its possible to delay Shorewall starting until the KVM interfaces are ready. I tried using the wait_interface option in /etc/default/shorewall, but this hung the server completely such that I had to boot off CD to restore it to being bootable again (although that experiment was with a somewhat different interface configuration -- I'm just really hesitating to try it again).

Shorewall is not listed in any of the /etc/rc.n folders, so that doesn't seem like the way to go.

Here are some of the configuration files.
/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address a.b.c.170
        netmask 255.255.255.0
        network a.b.c.0
        broadcast a.b.c.255
        gateway a.b.c.1
        up ip addr add a.b.c.172 dev eth0
        up ip addr add a.b.c.174 dev eth0
 
auto eth1
iface eth1 inet static
	address 192.168.2.1
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255

auto eth2
iface eth2 inet static
	address 192.168.3.1
	netmask 255.255.255.0
	network 192.168.3.0
	broadcast 192.168.3.255


```
ifconfig command:
```
root@m2a74am:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:34:56:78:9a  
          inet addr:a.b.c.170  Bcast:a.b.c.255  Mask:255.255.255.0
          inet6 addr: ffff::123:ffff:ffff:fff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13170432 (13.1 MB)  TX bytes:3278044 (3.2 MB)
          Interrupt:26 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:1b:21:13:df:66  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe13:df66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2992343 (2.9 MB)  TX bytes:14691426 (14.6 MB)

eth2      Link encap:Ethernet  HWaddr 00:14:6c:74:c9:37  
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe74:c937/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14809 (14.8 KB)  TX bytes:210 (210.0 B)
          Interrupt:21 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29609 (29.6 KB)  TX bytes:29609 (29.6 KB)

virbr0    Link encap:Ethernet  HWaddr 4e:99:d7:ad:86:aa  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1860706 (1.8 MB)  TX bytes:387934 (387.9 KB)

vnet0     Link encap:Ethernet  HWaddr 4e:99:d7:ad:86:aa  
          inet6 addr: fe80::4c99:d7ff:fead:86aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1845571 (1.8 MB)  TX bytes:556410 (556.4 KB)

vnet1     Link encap:Ethernet  HWaddr b6:cb:16:86:bd:be  
          inet6 addr: fe80::b4cb:16ff:fe86:bdbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:65619 (65.6 KB)  TX bytes:298341 (298.3 KB)

root@m2a74am:/# 
```
/etc/shorewall/zones:
```
#ZONE	TYPE	OPTIONS			IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net	ipv4
loc	ipv4
dmz	ipv4

```
/etc/shorewall/interfaces:
```
ZONE	INTERFACE	BROADCAST	OPTIONS
net     eth0            detect          bridge,tcpflags,nosmurfs,routefilter,logmartians
loc     eth1            detect          tcpflags,dhcp,nosmurfs,routefilter,logmartians
loc	eth2		detect		tcpflags,dhcp,nosmurfs,routefilter,logmartians
dmz     virbr0           detect		bridge,tcpflags,nosmurfs,optional
dmz     vnet0           detect		bridge,tcpflags,nosmurfs,optional
dmz	vnet1		detect          bridge,tcpflags,nosmurfs,optional

```
/etc/shorewall/masq
```
#INTERFACE		SOURCE		ADDRESS		PROTO	PORT(S)	IPSEC	MARK
eth0			eth1
eth0			eth2
eth0			virbr0

```
I dont' think there's a problem with policy or rules, since these work just fine either a) if the KVMs aren't allowed to start or b) if Shorewall is restarted.

---

### Post by tavasti on 2011-02-11
I have similar problem on ubuntu 10.04. SNAT rules don't work after reboot without restarting shorewall.

---

### Post by Kokopelli on 2011-02-23
I realize this is a bit old but for posterity sake....

The problem, and reason you are needing to restart shorewall, is that you are using detect on virbr0 but virbr0 is not up when shorewall starts.

The way to get around this is to define the address range in masq and interfaces.

so in interfaces change
```

dmz     virbr0           detect	bridge,tcpflags,nosmurfs,optional

```

to
```

dmz     virbr0           192.168.122.255	bridge,tcpflags,nosmurfs,optional

```

assuming the standard zone of 192.168.122.0/24

and in masq change
```

eth0			virbr0

```

to

```

eth0			192.168.122.0/24

```

assuming the standard IP range for KVM. 

Cheers

---

### Post by DrJohn999 on 2011-02-27
Thanks, but the broadcast address is rejected by Shorewall 4.4. With
```
dmz     virbr0          192.168.122.255		bridge,tcpflags,nosmurfs,routeback
```
in /etc/shorewall interfaces,
```
   WARNING: Shorewall no longer uses broadcast addresses in rule generation when Address Type Match is available : /etc/shorewall/interfaces (line 22)
12:01:39    Interface "dmz virbr0 192.168.122.255 bridge,tcpflags,nosmurfs,routeback" Validated
```

and no difference in behavior occurs. Changing to the known address of the virtual bridge shown by ifconfig:
```
dmz     virbr0          192.168.122.1		bridge,tcpflags,nosmurfs,routeback
``` produces the same warning and does not work either.

This behavior with Shorewall 4.4 is [documented]("http://www.shorewall.net/LennyToSqueeze.html") and in particular for kernels that include Address Type Match support. It seems clear that the Broadcast field should be 'detect' or '-' for these systems.

I plan to test using a 'real' virtual bridge that's declared explicitly as br0. Perhaps this will come up early enough to be detected.

---

