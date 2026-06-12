---
title: "KVM / Libvirtd -&gt; bridge does not work"
date: 2009-08-11
forum: Virtualisation
---

### Post by thirddeep on 2009-08-11
I am trying to get a virtual machine running with bridged networking.  I am using KVM with libvirtd.

kvm/jaunty-updates uptodate 1:84+dfsg-0ubuntu12.3
libvirt-bin/jaunty-updates uptodate 0.6.1-0ubuntu5.1
qemu/jaunty uptodate 0.10.0-1ubuntu1

My host network configuration looks like this :

```

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
	address 192.168.1.100
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	bridge_ports eth0
	bridge_stp off
	bridge_maxwait 5
	bridge_hello 2
	bridge_fd 9
	bridge_maxage 12

```

That results in :

```

br0       Link encap:Ethernet  HWaddr 00:24:1d:22:97:39  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe22:9739/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         

eth0      Link encap:Ethernet  HWaddr 00:24:1d:22:97:39  
          inet6 addr: fe80::224:1dff:fe22:9739/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
virbr0    Link encap:Ethernet  HWaddr d6:e1:ee:be:c1:cb  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::d4e1:eeff:febe:c1cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```
Abbreviated of course...

And just for completeness, brctl show
```

bridge name	bridge id		STP enabled	interfaces
br0		8000.00241d229739	no		eth0
pan0		8000.000000000000	no		
virbr0		8000.000000000000	yes	

```

With this configuration, networking is fine, else I would not be typing here ;-)

Now, my VM instance has the following bit in it's configuration :

```

    <interface type='user'>
      <source bridge='br0'/>
      <mac address='54:52:00:2e:c3:2d'/>
    </interface>

```

However, the VM can not ping the outer host, nor the gateway.  I am unsure if this is relevant, but under the hardware tab -> NIC it shows "Source device" as "-".  Should this not show br0 ?

Iptables in the VM is off, and iptables on my host looks like this:
```

Chain INPUT (policy ACCEPT 14021 packets, 18M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
    0     0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
    0     0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      virbr0  0.0.0.0/0            192.168.122.0/24    state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  virbr0 *       192.168.122.0/24     0.0.0.0/0           
    0     0 ACCEPT     all  --  virbr0 virbr0  0.0.0.0/0            0.0.0.0/0           
    0     0 REJECT     all  --  *      virbr0  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 REJECT     all  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT 13739 packets, 15M bytes)
 pkts bytes target     prot opt in     out     source               destination         


```
Those rules looks like it deals with the standard NAT.

Any help would be appreciated.

Thd.

---

### Post by forrestxm on 2009-08-27
I met similar problem, but my kvm is 72, and on ubuntu hardy 8.04.3. The bridge network does not work in guest system. Why?

I also searched web, no useful answers to my problem.

So could anyone ubuntu super guy answer our questions? Thanks a lot!

---

### Post by uopjohnson on 2009-12-30
Did you ever solve this?  I had bridged networking going just fine with 8.04 a fresh install using 9.10 however and the guests can no longer ping out.  I'm getting zero error messages or usefull information.

---

### Post by geekshlby on 2009-12-31
Change the interface type of the VM e.g. <interface type='bridge'>

---

