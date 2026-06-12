---
title: "Problem with ping"
date: 2008-08-17
forum: Virtualisation
---

### Post by Julius1988 on 2008-08-17
I am running xp as a guest os in ubuntu using VMWare,The ping command fails when i give the local ip of xp machine from ubuntu any suggestions??

---

### Post by Mister.Vash on 2008-08-17
How is the network interface configured for the guest?  Is it Bridged, NAT, Host Only?

Which version of vmware are you using?  Vmware Server, etc.

Can the guest ping anything on the network?
Can the host ping anything on the network while the guest is running?

On the host, can you provide the output of
```
ifconfig
route -n
```

On the guest can you provide the output of:
```
ipconfig /all
route print
```

---

### Post by Julius1988 on 2008-08-19
ifconfig

> 
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:AB:3D:E4  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feab:3de4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1299413 (1.2 MB)  TX bytes:120400 (117.5 KB)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.220.1  Bcast:172.16.220.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.197.1  Bcast:172.16.197.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


route -n

> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.197.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.220.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0



ipconfig /all
> 
Windows IP Configuration



        Host Name . . . . . . . . . . . . : nil-2b34b97bb0e

        Primary Dns Suffix  . . . . . . . :

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . :

        Description . . . . . . . . . . . : VMware Accelerated AMD PCNet Adapter



        Physical Address. . . . . . . . . : 00-0C-29-AE-74-6A

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.1.4

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DHCP Server . . . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 192.168.1.1

        Lease Obtained. . . . . . . . . . : Tuesday, August 19, 2008 6:53:43 PM

        Lease Expires . . . . . . . . . . : Tuesday, August 19, 2008 9:41:43 PM


route print

> 
Interface List

0x1 ........................... MS TCP Loopback interface

0x10003 ...00 0c 29 ae 74 6a ...... AMD PCNET Family PCI Ethernet Adapter - Pack

et Scheduler Miniport

===========================================================================

===========================================================================

Active Routes:

Network Destination        Netmask          Gateway       Interface  Metric

          0.0.0.0          0.0.0.0      192.168.1.1     192.168.1.4       10

        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1

      192.168.1.0    255.255.255.0      192.168.1.4     192.168.1.4       10

      192.168.1.4  255.255.255.255        127.0.0.1       127.0.0.1       10

    192.168.1.255  255.255.255.255      192.168.1.4     192.168.1.4       10

        224.0.0.0        240.0.0.0      192.168.1.4     192.168.1.4       10

  255.255.255.255  255.255.255.255      192.168.1.4     192.168.1.4       1

Default Gateway:       192.168.1.1

===========================================================================

Persistent Routes:

  None


---

### Post by Julius1988 on 2008-08-20
Is there a way to resolve this issue:confused:

---

### Post by Malfredious on 2008-08-20
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
172.16.220.0 0.0.0.0 255.255.255.0 U 0 0 0 vmnet1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

Ignore the following if you are not assigning 192.168.1.3 statically.

The above makes me suspicious that your eth0 might have a problem.  I've seen some Linux distro's fall back to 169.254.0.0 addresses (I suspect NetworkManager).  Try pinging 192.168.1.4 (or whatever IP address the XP machine has now) from the Ubuntu machine and let me know what IP address replies, if it is 192.168.1.3 with a destination unreachable (or whatever IP the eth0 is assigned) then my suspicions aren't of concern.  If it replies with 169.254.0.0 the eth0 is overriding your static assignment of 192.168.1.3 and trying to pull a DHCP address.  I hope this helps otherwise you're still on your own....does the Ubuntu machine have access to other machines?

---

### Post by Julius1988 on 2008-08-20
> **Malfredious said:**
> 192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
172.16.220.0 0.0.0.0 255.255.255.0 U 0 0 0 vmnet1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

Ignore the following if you are not assigning 192.168.1.3 statically.

The above makes me suspicious that your eth0 might have a problem.  I've seen some Linux distro's fall back to 169.254.0.0 addresses (I suspect NetworkManager).  Try pinging 192.168.1.4 (or whatever IP address the XP machine has now) from the Ubuntu machine and let me know what IP address replies, if it is 192.168.1.3 with a destination unreachable (or whatever IP the eth0 is assigned) then my suspicions aren't of concern.  If it replies with 169.254.0.0 the eth0 is overriding your static assignment of 192.168.1.3 and trying to pull a DHCP address.  I hope this helps otherwise you're still on your own....does the Ubuntu machine have access to other machines?
when i do a ping it is stuck like this and does not seem to end...........
 ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.

---

### Post by Malfredious on 2008-08-20
Can you ping 192.168.1.1 from the Ubuntu machine? ...and what does the XP machine get in replies when you ping 192.168.1.1?

---

### Post by Julius1988 on 2008-09-04
Sorry to trouble you guys it was my fault i never turned off the firewall, now its working fine.

---

