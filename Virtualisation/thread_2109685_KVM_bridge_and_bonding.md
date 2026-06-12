---
title: "KVM bridge and bonding"
date: 2013-01-28
forum: Virtualisation
---

### Post by Melges on 2013-01-28
Good day,

I would like to ask for help in setting up bundles bridge over bonding to work with KVM. Idea is this, there are two network interfaces eth0 and eth1 on a machine that is used as a host for virtual machines. Network interfaces connected to the same local network, I would like to set up bonding for load balancing between them.

I'm set up bonding, bridge over it, make bridge as an interface for virtual machines. Result: the host system network is working, even balanced and apparently all is well... But network in the virtual machines dosn't work.

So, configs:
```

~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface working in bonding
auto eth0
iface eth0 inet manual
	bond-master bond0
auto eth1
iface eth1 inet manual
	bond-master bond0

# Configure bonding
auto bond0
iface bond0 inet manual
	bond-mode balance-xor #
	bond-slaves none
	bond-miimon 100
#	bond-slaves eth0 eth1

# Interface for virtual machines
auto vbr0
iface vbr0 inet dhcp
#	vlan-raw-device bond0
        bridge_ports bond0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp on

```
```

~$ brctl show
bridge name	bridge id		STP enabled	interfaces
vbr0		8000.001a64b402b8	yes		bond0
							vnet0
							vnet1
							vnet2
							vnet3
							vnet4
							vnet5
							vnet6
							vnet7
virbr0		8000.000000000000	yes	

```
```

~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1a:64:b4:02:b8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3575 errors:0 dropped:1 overruns:0 frame:0
          TX packets:886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:531166 (531.1 KB)  TX bytes:98628 (98.6 KB)
          Interrupt:28 Memory:92000000-92012800 

eth1      Link encap:Ethernet  HWaddr 00:1a:64:b4:02:ba  
          inet6 addr: fe80::21a:64ff:feb4:2ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9155411 (9.1 MB)  TX bytes:13247789 (13.2 MB)
          Interrupt:40 Memory:94000000-94012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7859 (7.8 KB)  TX bytes:7859 (7.8 KB)

bond0      Link encap:Ethernet  HWaddr 00:1a:64:b4:02:b8  
          inet6 addr: fe80::21a:64ff:feb4:2b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124614 (124.6 KB)  TX bytes:2700 (2.7 KB)

vbr0      Link encap:Ethernet  HWaddr 00:1a:64:b4:02:b8  
          inet addr:192.168.74.9  Bcast:192.168.74.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:64ff:feb4:2b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124614 (124.6 KB)  TX bytes:2700 (2.7 KB)

virbr0    Link encap:Ethernet  HWaddr 42:c6:c1:4a:3d:38  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:2f:6b:0c  
          inet6 addr: fe80::fc54:ff:fe2f:6b0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:74757 (74.7 KB)  TX bytes:267199 (267.1 KB)

vnet1     Link encap:Ethernet  HWaddr fe:54:00:43:62:f8  
          inet6 addr: fe80::fc54:ff:fe43:62f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:12704 (12.7 KB)  TX bytes:11014 (11.0 KB)

vnet2     Link encap:Ethernet  HWaddr fe:54:00:72:28:66  
          inet6 addr: fe80::fc54:ff:fe72:2866/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3285 (3.2 KB)  TX bytes:9906 (9.9 KB)

vnet3     Link encap:Ethernet  HWaddr fe:54:00:91:4f:a1  
          inet6 addr: fe80::fc54:ff:fe91:4fa1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3285 (3.2 KB)  TX bytes:8322 (8.3 KB)

vnet4     Link encap:Ethernet  HWaddr fe:54:00:d0:b2:72  
          inet6 addr: fe80::fc54:ff:fed0:b272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2943 (2.9 KB)  TX bytes:7842 (7.8 KB)

vnet5     Link encap:Ethernet  HWaddr fe:54:00:0b:e8:3e  
          inet6 addr: fe80::fc54:ff:fe0b:e83e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:4657 (4.6 KB)

vnet6     Link encap:Ethernet  HWaddr fe:54:00:fe:4e:c6  
          inet6 addr: fe80::fc54:ff:fefe:4ec6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2264 (2.2 KB)  TX bytes:2964 (2.9 KB)

vnet7     Link encap:Ethernet  HWaddr fe:54:00:d5:d3:07  
          inet6 addr: fe80::fc54:ff:fed5:d307/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:2184 (2.1 KB)

```

Diagnostics with tcpdump showed that the packets go from virtual machines in a network, but do not come back. DHCP requests to observe the following: DHCP Request to see vnet0, vbr0, bond0 eth0 or eth1, DHCP reply to see eth0 or eth1, bond0, vbr0, but on vnet0 not see :(

I tried to do:
[list type = decimal]
[li] Add vlan-raw-device bond0 herein vbr0 and replace bridge_ports bond0 on bridge_ports bond0.11 or bond.10 [/li]
[li] Enable and disable STP [/li]
[li] A lot of google and read about the bugs in the incorrect processing arp bugtracker Ubuntu and redhata [/li]
[li] To learn Japanese [/li]
[/list]

Unfortunately nothing of the above did not help me. Perhaps someone more experienced tell me what is the problem?

Thank you in advance for your help.

---

### Post by heiko_s on 2013-02-01
I did some experimenting with virtual bridges under Xen, but it should be the same with KVM.

Some things you may want to eliminate from the equation:

1. network-manager: If it's installed and active, you can either deactivate it or deinstall it.
2. You run a virbr0 NAT bridge that was configured automatically and isn't used (see ifconfig output - there is no traffic going through). Disable it by deleting the "default.xml" link in etc/libvirt/qemu/networks/autostart. In case you wish to enable it again, just create the link with ln -s /etc/libvirt/qemu/networks/default.xml /etc/libvirt/qemu/networks/autostart/default.xml.

Run
```
sudo service networking restart
```
or reboot. See if it makes a difference.

If not, try the following:

3. Disable IPv6 (can cause slow network under Ubuntu) by editing /etc/sysctl.conf and adding these lines to the bottom:
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

as well as these to prevent the firewall (netfilter) from filtering bridged packets:

```
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0

```

4. This is a work around for Ubuntu bug #50093 to ensure that the bridge sysctl settings get loaded on boot. Edit the /etc/rc.local file and place the following line just above the line "exit 0":

```
/sbin/sysctl -p /etc/sysctl.conf
```

I'm not sure whether or not this bug was ever fixed in Ubuntu, so it may be worth trying.

All of the above isn't specific to bonding and may not help in your case, but at the very least you will be reducing the variables.

---

### Post by heiko_s on 2013-02-01
If your eth0 and eth1 run in bonded mode, whouldn't they show similar traffic throughput? Cause your ifconfig shows a lot more traffic on one interface. I might be totally wrong, though.

---

### Post by zeljkojagust on 2013-02-02
Here is mine /etc/network/interfaces configuration. It works like a charm:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet manual
    bond-mode balance-tlb
    bond-miimon 100
    bond-slaves none

# Enslave all the physical interfaces
auto eth0
iface eth0 inet manual
bond-master bond0

auto eth1
iface eth1 inet manual
bond-master bond0

# Configure the bridging interface
auto br0
iface br0 inet static
    address 192.168.0.50
    netmask 255.255.255.0
    gateway 192.168.0.1
    dns-nameservers 8.8.8.8
    bridge-ports bond0
    bridge-fd 9
    bridge-hello 2
    bridge-maxage 12
    bridge-stp off

---

### Post by Melges on 2013-02-21
Thanks for the help, but unfortunately did not help. It seems the problem in processing arp requests in bridge. On RedHat issue tracker i founded ticket, it seems that the decision has not yet been found. I switch bond0 to balance-tlb mode. This is not what we want, but at least outbound traffic is balanced.

---

