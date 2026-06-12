---
title: "KVM Ubuntu Host and Ubuntu guest - network problem"
date: 2008-06-03
forum: Virtualisation
---

### Post by josir on 2008-06-03
Hi folks,
I installed kvm with this configuration:

- Host: Ubuntu 8.04 64bits 192.168.0.6
- Guest: Ubuntu 8.04 64bits 192.168.0.10

Installation was based on:

[https://help.ubuntu.com/8.04/serverguide/C/libvirt.html](https://help.ubuntu.com/8.04/serverguide/C/libvirt.html)

Everything is working fine (xwindow,mouse,virt-manager,etc) except network. My goal is to have both host and guest visible to my internal network. 

I can ping from host to a external machine.
I can ping from external machine to guest (192.168.0.10)
I CANNOT ping from external machine to host (192.168.0.6)

But when I try to connect via ssh@192.168.0.10, I connect the host machine!?!! 

What I am doing wrong? Can somebody has any tip or insight?
If somebody have any doco on how to work with bridged network, I will appreciate also.

Here is the /etc/network/interfaces

```

auto eth0
iface eth0 inet static
	address 192.168.0.6
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	dns-nameservers 192.168.0.1
        dns-search local

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

and Host ifconfig:
eth0 does not have an IP address??? Is this normal on a bridged interface?

```

josir@linux06:~$ sudo ifconfig
[sudo] password for josir: 
br0       Link encap:Ethernet  HWaddr 00:1a:64:1f:18:64  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:64ff:fe1f:1864/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48355 (47.2 KB)  TX bytes:21606 (21.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:64:1f:18:64  
          inet6 addr: fe80::21a:64ff:fe1f:1864/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60976 (59.5 KB)  TX bytes:23974 (23.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23693842 (22.5 MB)  TX bytes:23693842 (22.5 MB)

vnet0     Link encap:Ethernet  HWaddr 36:83:3d:b5:d4:f7  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::3483:3dff:feb5:d4f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

vnet1     Link encap:Ethernet  HWaddr 00:ff:c9:22:ab:91  
          inet6 addr: fe80::2ff:c9ff:fe22:ab91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1966 (1.9 KB)  TX bytes:28355 (27.6 KB)

```

---

### Post by josir on 2009-02-10
Just to post the solution for someone with the same problem:

When you configure the br0, you don't need to configure the eth0 !
So the correct configuration is:

--- start ---
auto br0
iface br0 inet static
        address 192.168.0.6
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
--- end ---

That is, the HOST IP should be 192.168.0.6 and the GUEST should be configured ONLY the guest machine. 

Summary: 
The Ubuntu Help Guide ([https://help.ubuntu.com/8.04/serverguide/C/libvirt.html](https://help.ubuntu.com/8.04/serverguide/C/libvirt.html)) is perfect. My understanding was completely wrong....

---

