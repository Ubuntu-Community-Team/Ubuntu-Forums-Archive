---
title: "KVM guest unable to access the primary OVS bridge interface"
date: 2015-12-10
forum: Virtualisation
---

### Post by Priscilla_Ng on 2015-12-10
I am new to OpenvSwitch. I create two OVS bridges as below config, one in 10.32.0.0/24 (br0) subnet and the other in 10.32.10.0/24 (br1) subnet. I able to ping the default gateway of br0 or br1 from the host. If I create a guest VM on br1, everything work fine and guest able to ping get DHCP add and ping default gateway. However, if I create a guest VM on br0, it's not able to access the br0 ip or default gateway. Any idea why? Am I missing any config?


```
root@uCPE:/var/lib/libvirt/guest_images# ovs-vsctl show
ca93f2c5-dd68-492d-a634-b77d57fae1a9
    Bridge "br0"
        Port "br0"
            Interface "br0"
                type: internal
        Port "em1"
            Interface "em1"
        Port "vnet1"
            Interface "vnet1"
    Bridge "br1"
        Port "em2"
            Interface "em2"
        Port "vnet2"
            Interface "vnet2"
        Port "br1"
            Interface "br1"
                type: internal
        Port "vnet0"
            Interface "vnet0"
        Port "vnet3"
            Interface "vnet3"
    ovs_version: "2.0.2"
```
```
root@uCPE:/var/lib/libvirt/guest_images# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The primary network interface
auto em1
iface em1 inet manual


# The secondary network interface
auto em2
iface em2 inet manual


#The OVS Internet bridge interface WAN
auto br0
iface br0 inet static
address 10.32.0.111
netmask 255.255.255.0
gateway 10.32.0.1
dns-nameservers 10.32.0.1
pre-up brctl addbr br0
pre-up brctl addif br0 em1
post-down ip link set em1 down
post-down brctl delif br0 em1
post-down brctl delbr br0


#The OVS Internal bridge interface LAN
auto br1
iface br1 inet static
address 10.32.10.111
netmask 255.255.255.0
gateway 10.32.10.1
dns-nameservers 10.32.10.1
```



```
root@uCPE:/var/lib/libvirt/guest_images# ifconfig
br0       Link encap:Ethernet  HWaddr 00:25:90:5d:0d:dc  
          inet addr:10.32.0.111  Bcast:10.32.0.255  Mask:255.255.255.0
          inet6 addr: 2601:646:8b01:6900:225:90ff:fe5d:ddc/64 Scope:Global
          inet6 addr: 2601:646:8b01:6900:94d:73be:2b97:2cf3/64 Scope:Global
          inet6 addr: fe80::225:90ff:fe5d:ddc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3925 errors:0 dropped:7 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:256869 (256.8 KB)  TX bytes:121562 (121.5 KB)


br1       Link encap:Ethernet  HWaddr 00:25:90:5d:0d:dd  
          inet addr:10.32.10.111  Bcast:10.32.10.255  Mask:255.255.255.0
          inet6 addr: fe80::248d:4eff:fe82:d724/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:685 errors:0 dropped:18 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78798 (78.7 KB)  TX bytes:2090 (2.0 KB)


em1       Link encap:Ethernet  HWaddr 00:25:90:5d:0d:dc  
          inet6 addr: fe80::225:90ff:fe5d:ddc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:338815 (338.8 KB)  TX bytes:127524 (127.5 KB)
          Memory:fb120000-fb13ffff 


em2       Link encap:Ethernet  HWaddr 00:25:90:5d:0d:dd  
          inet6 addr: fe80::225:90ff:fe5d:ddd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:337426 (337.4 KB)  TX bytes:1706845 (1.7 MB)
          Memory:fb100000-fb11ffff 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:61797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9432016 (9.4 MB)  TX bytes:9432016 (9.4 MB)


vnet0     Link encap:Ethernet  HWaddr fe:54:00:81:a0:50  
          inet6 addr: fe80::fc54:ff:fe81:a050/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:7692 (7.6 KB)  TX bytes:84164 (84.1 KB)


vnet1     Link encap:Ethernet  HWaddr fe:54:00:6d:2b:83  
          inet6 addr: fe80::fc54:ff:fe6d:2b83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:45000 (45.0 KB)  TX bytes:5177 (5.1 KB)


vnet2     Link encap:Ethernet  HWaddr fe:54:00:ef:30:b8  
          inet6 addr: fe80::fc54:ff:feef:30b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1693093 (1.6 MB)  TX bytes:116310 (116.3 KB)
```


```
root@uCPE:/var/lib/libvirt/guest_images# ping 10.32.0.1
PING 10.32.0.1 (10.32.0.1) 56(84) bytes of data.
64 bytes from 10.32.0.1: icmp_seq=1 ttl=64 time=0.959 ms
64 bytes from 10.32.0.1: icmp_seq=2 ttl=64 time=0.706 ms
^C
--- 10.32.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.706/0.832/0.959/0.129 ms
root@uCPE:/var/lib/libvirt/guest_images# ping 10.32.10.1
PING 10.32.10.1 (10.32.10.1) 56(84) bytes of data.
64 bytes from 10.32.10.1: icmp_seq=1 ttl=255 time=1.23 ms
64 bytes from 10.32.10.1: icmp_seq=2 ttl=255 time=0.848 ms
^C
--- 10.32.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.848/1.042/1.236/0.194 ms
root@uCPE:/var/lib/libvirt/guest_images#
```

---

### Post by deadflowr on 2015-12-10
Moved to Virtualisation

and please use code tags when posting output, for better readability.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by Priscilla_Ng on 2015-12-10
Thanks. I'll pay attention next time. This is my first time posting. :) 

I want to find out whether it's possible to create multiple OVS bridge for different subnet and have Guest VM on both subnet. :)

---

