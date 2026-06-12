---
title: "KVM Bridged Network - solutions and problems"
date: 2008-08-13
forum: Virtualisation
---

### Post by drplix on 2008-08-13
Edit:  This was very easy to solve.  Thanks to a quick search I found this link...

[http://blog.cynapses.org/2007/07/12/qemu-kvm-internal-network-setup/](http://blog.cynapses.org/2007/07/12/qemu-kvm-internal-network-setup/)

Down near the bottom

> 
Note that the VMs have different MAC addresses. It took me a long time to find why I couldn’t ping from one guest to another ;)


Somehow I'd managed to give each virtual machine the same MAC.  Bridge routing cannot work then since it uses the MAC at layer2 to do the bridging.

With this changed everything works like a charm - I even have a virtualized VPN gateway working now.
--


I have successfully got a couple of KVM virtual servers running on an 8-way ubuntu host with a single NIC on local physical network 192.168.100.0/24.  I have a gateway router at 192.168.100.1 and a few other physical servers on the network.

My experience so far with KVM and libvirt is pretty nice.  Default networking works fine.  But now I want to turn the virtual servers into production workhorses so I need to give them static IPs on a bridged host network.

So far I've tried two configurations...

**1) Simple Bridged**

Following a combination of the Ubuntu KVM howto 

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

and the libvirt wiki

[http://wiki.libvirt.org/page/Networking#Altering_the_interface_config](http://wiki.libvirt.org/page/Networking#Altering_the_interface_config)

I've managed to give my two VMs IP addresses 192.168.100.101 and 192.168.100.102.  Both machines are visible to the host.  Both machines can ping the physical router.  So far so good.  Here's the /etc/network/interfaces configuration:

> 
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.100.10
netmask 255.255.255.0
gateway 192.168.100.1

auto eth0

auto br0
iface br0 inet static
        address 192.168.100.10
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        gateway 192.168.100.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


The hard part was figuring out that libvirt needs this configuration for a bridged network guest in the vm definition file

```

 <interface type='bridge'>
     <mac address='52:54:e9:81:87:15'/>
     <source bridge='br0'/>
 </interface>

```

So the now the problems.

i)  Intermittent packet loss with 'ping 192.168.100.10x' from a physical server on the physical network.  Also see latency on first connection with up to 10 packets lost at the start of ping.  Seem to behave fine with a flood 'ping -f'

ii) Worse problem, neither virtual machine can see the other.  Cannot ping 192.168.100.10x at all.  This is a killer since these VMs will provide an n-tier application platform.

Suggestions on how I can fix this would be appreciated.  But I tried another network configuration too...

**2) VDE (Virtual Distributed Networking)**

I used the following guide to try a VDE network...

[http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking](http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking)

Have sucessfully got all virtual machines on the virtual network and each can ping the other, and the host can ping each of them.  Here's my /etc/network/interfaces for this ...

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.100.10
        netmask 255.255.255.0
        gateway 192.168.100.1


# KVM/QEMU Virtual Machine Network
auto kvm0
iface kvm0 inet static
        address 192.168.110.254
        netmask 255.255.255.0
        pre-up /usr/bin/vde_switch --tap ${IFACE} --daemon --group vde2-net --sock /var/run/${IFACE}.ctl \
         --mod 775 --mgmtmode 770 --mgmt /var/run/${IFACE}-manage --pidfile /var/run/${IFACE}_vde.pid
        up /usr/sbin/dnsmasq --interface=${IFACE}  --except-interface=lo --bind-interfaces --user=nobody \
         --dhcp-range=kvm,192.168.110.1,192.168.110.99,255.255.255.0,192.168.110.255,8h \
         --domain=1060research.com --pid-file=/var/run/${IFACE}_dnsmasq.pid --conf-file
        up echo "`route -n | sed -n 's/^0\.0\.0\.0 .* \(.*\)$/\1/p'`" > /var/run/${IFACE}_route
        up iptables -t nat -A POSTROUTING -o `cat /var/run/${IFACE}_route` -j MASQUERADE
        down iptables -t nat -D POSTROUTING -o `cat /var/run/${IFACE}_route` -j MASQUERADE
        down kill -s TERM `cat /var/run/${IFACE}_dnsmasq.pid` && rm -f /var/run/${IFACE}_dnsmasq.pid
        post-down kill -s HUP `cat /var/run/${IFACE}_vde.pid`
        post-down rm -f /var/run/${IFACE}_route 


```

Problem with this

i) My virtual network is on 192.168.110.0/24 and my physical network is on 192.168.100.0/24.  I don't know how to bridge the physical network to the eth0 interface and connect up the VDE network.  So the VDE network is purely logical and can't see the outside world - nor can be found from the physical network.  How do I bridge it?

My preference is to solve the bridging for config 1) since libvirt makes production management of the VMs very easy.  Option 2) works great and looks like the future but VDE is not yet supported by libvirt so it is going to take a lot of work to get the VMs manageable for production.

Hope these experiences help someone and if you've got any tips for me they'd be greatly appreciated.

In general, KVM seems like a good option, I've used VMware server but its a pain that it requires rebuilding each time the host server gets a kernel security fix.  KVM is just a kernel module so it stays in step and so is very easy to manage long term.  Performance is excellent (barring the network issues I need to solve).

---

### Post by Pettman on 2008-08-22
Is the static configuration of eth0 required or is it just because you need it on your LAN?

---

### Post by sheph on 2009-04-14
Well I'm seeing something similar to your scenario 1, and the mac addresses are different. 
Every so often the inside interface eth0 starts to drop out, and my remote ssh session will fail.  I do routing through this box so I lose all external connectivity when this happens.

I have 2 NICs so my /etc/network/interfaces file is:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual
auto br0
iface br0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        bridge_ports eth0
        bridge_fd 0
        bridge_hello 2
        bridge_maxage 12
        bridge_stp on
# Secondary
auto eth1
iface eth1 inet manual
auto br1
iface br1 inet static
        address 192.168.10.5
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
        gateway 192.168.10.1
        bridge_ports eth1
        bridge_fd 1
        bridge_hello 2
        bridge_maxage 12
        bridge_stp on
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.106 192.168.0.11
        dns-search mydomain.com
```

ifconfig yeilds:
```
br0       Link encap:Ethernet  HWaddr 00:e0:81:b0:fb:2c  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb0:fb2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13139783 (13.1 MB)  TX bytes:31771326 (31.7 MB)

br1       Link encap:Ethernet  HWaddr 00:e0:81:b0:fb:2d  
          inet addr:192.168.10.5  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb0:fb2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34595789 (34.5 MB)  TX bytes:11529481 (11.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:e0:81:b0:fb:2c  
          inet6 addr: fe80::2e0:81ff:feb0:fb2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:25193018 (25.1 MB)  TX bytes:47270423 (47.2 MB)
          Memory:d3000000-d3020000 

eth1      Link encap:Ethernet  HWaddr 00:e0:81:b0:fb:2d  
          inet6 addr: fe80::2e0:81ff:feb0:fb2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:55747765 (55.7 MB)  TX bytes:24450319 (24.4 MB)
          Memory:d3020000-d3040000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72029076 (72.0 MB)  TX bytes:72029076 (72.0 MB)

vnet0     Link encap:Ethernet  HWaddr de:ea:ed:8a:c0:bb  
          inet6 addr: fe80::dcea:edff:fe8a:c0bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:10977464 (10.9 MB)  TX bytes:16254696 (16.2 MB)

vnet1     Link encap:Ethernet  HWaddr 46:bf:c4:1f:94:27  
          inet6 addr: fe80::44bf:c4ff:fe1f:9427/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:11927177 (11.9 MB)  TX bytes:23459593 (23.4 MB)
```

I tried to get rid of vnet0 and vnet1 thinking that they were causing the issue, but they're obviously being pulled from somewhere I haven't thought to look.

My vm xml file has this:
```
 <interface type='bridge'>
      <mac address='00:16:36:65:7f:d9'/>
      <source bridge='br0'/>
    </interface>
    <interface type='bridge'>
      <mac address='00:16:36:5f:e0:7a'/>
      <source bridge='br1'/>
    </interface>
```

I'm wondering if there is a problem trying to use both nics on a vm instance.  I dunno.  If I remove either of them the problem goes away.  However, I kind of need both in order to provide service inside and outside of the network.

---

