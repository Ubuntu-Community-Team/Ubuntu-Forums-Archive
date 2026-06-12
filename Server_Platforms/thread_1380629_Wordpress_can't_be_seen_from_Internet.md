---
title: "Wordpress can't be seen from Internet"
date: 2010-01-13
forum: Server Platforms
---

### Post by ubenturocks on 2010-01-13
I have a problem with my Wordpress installation.
It works from inside of my LAN but not from Internet.

I have opened for the port on my router and the default html page works from Apache2 from Internet.

How can I debug this?

Lars

---

### Post by volkswagner on 2010-01-14
You will need to provide more info.  

How/where did you install wordpress?  Did you create a vhost file for your wordpress site?  If so, post your vhost file.

---

### Post by ubenturocks on 2010-01-14
Ubuntu is running in VMWare workstation under Windows 7.
 
I found out the problem is my network in vmware.
when I set it network settings to NAT it works but is not supposed to be seen from outside of the LAN.
When I set vmware to bridged it does not work.

This looks like a WMware problem to me I will try to ask them.

---

### Post by Cheesemill on 2010-01-14
Set the VM to bridged netwoking and then change the port forwarding in your router to point to the new IP address of the VM.

---

### Post by ubenturocks on 2010-01-14
Yes, I already opened the router port.

I tried to install a new fresh Ubuntu to see what might be wrong.
When I run the install the dhcp fails, I set the network manually but now I can't ping it from my host.

I have attached a screen shoot from my Ubuntu installation please see attached files.

Any ideas?

Host Windows 7 network settings
>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : i7
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : TAP-Win32 Adapter V9
   Physical Address. . . . . . . . . : 00-FF-C6-59-00-F9
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter vpn1 - VPN Client:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : VPN Client Adapter - vpn1
   Physical Address. . . . . . . . . : 00-AC-03-BF-3A-93
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller #2
   Physical Address. . . . . . . . . : 00-26-18-08-5C-EC
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller
   Physical Address. . . . . . . . . : 00-26-18-08-5C-ED
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::11b8:b411:5356:9976%2(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.0.4(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, January 14, 2010 3:17:35 AM
   Lease Expires . . . . . . . . . . : Friday, January 15, 2010 6:20:22 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 201336344
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-11-D8-BE-E8-00-26-18-08-5C-ED
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VMware Network Adapter VMnet1:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet1
   Physical Address. . . . . . . . . : 00-50-56-C0-00-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f8cb:178e:62bb:249e%18(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.137.1(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 419450966
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-11-D8-BE-E8-00-26-18-08-5C-ED
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VMware Network Adapter VMnet8:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8
   Physical Address. . . . . . . . . : 00-50-56-C0-00-08
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f8ea:b0f6:c517:53ba%19(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.254.1(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 436228182
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-11-D8-BE-E8-00-26-18-08-5C-ED
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
   Physical Address. . . . . . . . . : 08-00-27-00-A8-BF
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::75b9:51cb:4b9b:8065%22(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.56.1(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 
   DHCPv6 IAID . . . . . . . . . . . : 369623079
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-11-D8-BE-E8-00-26-18-08-5C-ED
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{FD680579-FB4A-467F-BAF3-A7948837612B}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{C18DAE31-2110-427B-BE2E-50B57663241A}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{9690C2AD-89C4-4188-AE02-20FFC1FA76E3}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{C65900F9-17D6-4AB4-A96C-CB34EA7F389A}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{7DA81159-B719-4577-B33E-F92F1A7A4407}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #5
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{AF582351-B45C-4E4B-8F57-65F4B3C3040F}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #6
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{DE07A035-B63D-403C-8402-4A1FEB25501C}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #7
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Lars

---

### Post by ubenturocks on 2010-01-14
I got the answer now and it works.

continuum told me this:
you have more than one physical network-card - this means you MUST disable "automatic bridging" in Virtual Network Editor" - please check that first.

[http://communities.vmware.com/message/1457219#1457219](http://communities.vmware.com/message/1457219#1457219)

---

