---
title: "Cant get online !"
date: 2008-08-22
forum: Virtualisation
---

### Post by xbo on 2008-08-22
Guys

Got a problem and could really do with some help sorting it out, its being plaguing me for a few days now :confused:

I have a WinXP Box with VMWare Workstation 6, i  have virtualized Kubuntu 8.

Problem is, is that i can get online with Kubuntu !

My set up is as :

Host - WinXP SP3
Guest - Kubuntu 8
Vmware Workstation 6
I have a Belkin Router from which i have a wired ethernet connection - this works great for WinXP

The problem is that i cant get online from Kubuntu, I really dont know anything about DNS, DHCP, NAT, Bridged connection etc. So I dont really what i should be setting or unsetting.

From Vmware Wokstation i have selected  a Bridge conneciton


-------------------------------------
ifconfig from kubuntu is

eth0      Link encap:Ethernet  HWaddr 00:0c:29:2d:e2:43
          inet6 addr: fe80::20c:29ff:fe2d:e243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:842 (842.0 B)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0x2024

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-------------------------------------------------------------------

Ipconfig from WinXP :-

Windows IP Configuration

        Host Name . . . . . . . . . . . . : desktop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : Belkin

Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8
        Physical Address. . . . . . . . . : 00-50-56-C0-00-08
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.126.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet1
        Physical Address. . . . . . . . . : 00-50-56-C0-00-01
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.80.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Microsoft Loopback Adapter
        Physical Address. . . . . . . . . : 02-00-4C-4F-4F-50
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 10.10.10.10
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : Belkin
        Description . . . . . . . . . . . : Attansic L1 Gigabit Ethernet 10/100/1000Base-T Controller
        Physical Address. . . . . . . . . : 00-1E-8C-02-6A-19
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.2.7
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
        DHCP Server . . . . . . . . . . . : 192.168.2.1
        DNS Servers . . . . . . . . . . . : 192.168.2.1
        Lease Obtained. . . . . . . . . . : 17 August 2008 07:35:59
        Lease Expires . . . . . . . . . . : 04 July 1907 01:07:43


THANKS FOR ANY HELP....AND I NEED IT...

Cheers

---

