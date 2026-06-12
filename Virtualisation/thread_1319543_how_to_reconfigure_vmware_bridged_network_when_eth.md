---
title: "how to reconfigure vmware bridged network when eth1 becomes eth0? etc.."
date: 2009-11-08
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-08
i have been playing around with network manager, added network card and the names keep changing. i was running on eth2 and eth4 now it is back to eth0 and eth1
 problem is vmware bridged network gets messed up and the network fails in the VM. the only solution i have seen so far is a complete uninstall-reinstall to let vmware redetect the network association to the the ubuntu names (eth0, eth1, eth2, eth3, etc...) and reassign the network bridges that vmware creates to each particular ubuntu ethernet card name.

the last time was 
vmnet0=name bridge = eth2
vmnet2 = name bridgedeth4 = eth4 

now i am back to eth0 and eth1 on the network manager assignment. and vmware server is not going to work again.

> scott@scott-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5186 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:3770397 (3.7 MB)  TX bytes:998393 (998.3 KB)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr 00:10:5a:73:c4:83  
          inet addr:169.254.8.189  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::210:5aff:fe73:c483/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8056 (8.0 KB)  TX bytes:80932 (80.9 KB)
          Interrupt:16 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1410095 (1.4 MB)  TX bytes:1410095 (1.4 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.174.1  Bcast:172.16.174.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.110.1  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by sdowney717 on 2009-11-08
> Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] editor

The following virtual networks have been defined:

. vmnet0 is bridged to eth2
. vmnet1 is a host-only network on private subnet 172.16.174.0.
. vmnet2 is bridged to eth4
. vmnet8 is a NAT network on private subnet 192.168.110.0.


i reran vmware-config.pl and then select editor, use a number for each network like vmnet0 is 0, etc...

---

### Post by fjgaude on 2009-11-08
I think if you simply run /usr/bin/vmware-config.pl

It will do what you wish. You might have to cd to the /usr/bin and do the command there as root or an sudo.

---

