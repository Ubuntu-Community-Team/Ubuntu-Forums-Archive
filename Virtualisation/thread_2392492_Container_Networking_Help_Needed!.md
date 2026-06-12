---
title: "Container Networking Help Needed!"
date: 2018-05-21
forum: Virtualisation
---

### Post by rayj00 on 2018-05-21
Warning:  I am not a networking expert by any means so be gentle!  :)

So I nave a test network at home.  My host is a Windows 7 Pro box.
I am using Vbox and have one VM with Ubuntu 18.04. 
I created the VM with Bridged Adapter.
I have one LXD container with Ubuntu 16.04.04.

**[COLOR="#FF0000"]My Win 7 host ipconfig:[/COLOR]**

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 192.168.0.5
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::7870:25a7:ce20:6921%14
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Ethernet adapter VirtualBox Host-Only Network #2:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::3564:1033:605f:754a%20
   IPv4 Address. . . . . . . . . . . : 192.168.92.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{29E107B4-B450-4266-A92D-DC179CE9B03E}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{99D1090F-B1BF-4D9D-82F8-58FE4E61BF74}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{98E9B6DF-0C58-483C-BA70-08EA69F352E7}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

**[COLOR="#FF0000"]My VM ifconfig:[/COLOR]**

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.21.198.1  netmask 255.255.255.0  broadcast 0.0.0.0
        inet6 fd42:13ed:2591:c2e9::1  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::24fc:9eff:fe69:42f0  prefixlen 64  scopeid 0x20<link>
        ether fe:a2:4f:cf:43:02  txqueuelen 1000  (Ethernet)
        RX packets 6568  bytes 410906 (410.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8543  bytes 27220663 (27.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.25  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:fe2f:d423  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:2f:d4:23  txqueuelen 1000  (Ethernet)
        RX packets 279939  bytes 390369282 (390.3 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 65896  bytes 5244520 (5.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 305  bytes 25691 (25.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 305  bytes 25691 (25.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vethJ2CSRN: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fca2:4fff:fecf:4302  prefixlen 64  scopeid 0x20<link>
        ether fe:a2:4f:cf:43:02  txqueuelen 1000  (Ethernet)
        RX packets 437  bytes 49661 (49.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 448  bytes 363829 (363.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

**[COLOR="#FF0000"]My Container ifconfig:[/COLOR]**

eth0      Link encap:Ethernet  HWaddr 00:16:3e:d7:a3:88
          inet addr:10.21.198.134  Bcast:10.21.198.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fed7:a388/64 Scope:Link
          inet6 addr: fd42:13ed:2591:c2e9:216:3eff:fed7:a388/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:364400 (364.4 KB)  TX bytes:50087 (50.0 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lxdbr0    Link encap:Ethernet  HWaddr 06:23:6f:8b:32:a4
          inet6 addr: fe80::423:6fff:fe8b:32a4/64 Scope:Link
          inet6 addr: fe80::1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:960 (960.0 B)


So, the VM can ping the container on the 10.x.x.x network.
The container can ping the VM on the 10.x.x.x network.
The host can ping the VM on the 192.x.x.x network
The VM **[COLOR="#FF0000"]cannot[/COLOR]** ping the host on the 192.x.x.x network.

My goal is for the containers to have access to the internet as well as the intranet.
I want to be able to ping everything from everything.

Make sense?

So what do I need to do?

Thanks and I appreciate your help.

Ray

---

