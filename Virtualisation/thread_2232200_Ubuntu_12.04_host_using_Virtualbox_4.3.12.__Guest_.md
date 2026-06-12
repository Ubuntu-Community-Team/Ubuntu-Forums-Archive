---
title: "Ubuntu 12.04 host using Virtualbox 4.3.12.  Guest is Windows 7 – No Network"
date: 2014-06-30
forum: Virtualisation
---

### Post by lmancusojr on 2014-06-30
I'm using Ubuntu 12.04 on an Acer Aspire 5742-7645 laptop with 4GB memory, Intel Core i3 processor, Intel HD Graphics, DVD drive, 802.1 b/g/n, and 500 GB HD. I connect to my router via a wireless connection.

I have installed Virutalbox 4.1.12 from the Ubuntu Software Center and installed Guest additions 4.1.12 in the Windows 7 guest session.

I have Windows XP and Windows 7 installed as guests in Virtual box The network settings are different for XP and 7 – see below.

Network Settings XP guest = Adapter 1: PCnet-FAST III (NAT) - Network works perfectly and has worked well for several years.

Network Settings Win 7 = Adapter 1: Intel PRO/1000 MT Desktop (Bridged adapter, eth1) Promiscuous Mode = allow all Cable connected = checked

When I originally installed Windows 7, I tried NAT and the guest network would not connect. Once I changed the setting to the above (Bridged) the Network worked perfectly. However, what I believe is after updates (not sure if it was an Ubuntu or Windows update) the guest network stopped working and I can not get it to connect.

After posting on HowtoForge, it was recommended to upgrade to the latest version of VB.  I upgrades to VB 4.3.12 r93733 I added guest additions and the extension pack for this version.

Problem continues to exist.

/etc/network/interfaces file as below:
Interfaces file content
auto lo
iface lo inet loopback

lou@lou-Aspire-5742:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:09:f6:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 4c:0f:6e:7c:9f:01  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4e0f:6eff:fe7c:9f01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1026849 errors:98 dropped:0 overruns:0 frame:3091226
          TX packets:607154 errors:74 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1348085348 (1.3 GB)  TX bytes:72519957 (72.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3584394 (3.5 MB)  TX bytes:3584394 (3.5 MB)

VBoxManage list bridgedifs yields the following:
lou@lou-Aspire-5742:~$ VBoxManage list bridgedifs
Name:            eth1
GUID:            31687465-0000-4000-8000-4c0f6e7c9f01
DHCP:            Disabled
IPAddress:       192.168.1.19
NetworkMask:     255.255.255.0
IPV6Address:     fe80:0000:0000:0000:4e0f:6eff:fe7c:9f01
IPV6NetworkMaskPrefixLength: 64
HardwareAddress: 4c:0f:6e:7c:9f:01
MediumType:      Ethernet
Status:          Up
VBoxNetworkName: HostInterfaceNetworking-eth1

Name:            eth0
GUID:            30687465-0000-4000-8000-1c750809f65c
DHCP:            Disabled
IPAddress:       0.0.0.0
NetworkMask:     0.0.0.0
IPV6Address:     
IPV6NetworkMaskPrefixLength: 0
HardwareAddress: 1c:75:08:09:f6:5c
MediumType:      Ethernet
Status:          Up
VBoxNetworkName: HostInterfaceNetworking-eth0


I'm not sure what else to do. Can someone provide the troubleshooting steps to determine what the problem is and possible solution?

---

### Post by slooksterpsv on 2014-07-01
What version of Windows 7?
Is it a "stripped" down version via an app like 7lite?

Have you checked the network connection properties in the guest? If it's using NAT it should show something like a 10.0.2.2 or something along those lines.
Are you running any firewall software, antivirus, etc.? If it's Norton or Trend Micro - those two are the biggest offenders in my opinion.
Have you tried having Windows diagnose the connection?

---

### Post by lmancusojr on 2014-07-01
[**[COLOR=#000000]slooksterpsv[/COLOR]**]("http://ubuntuforums.org/member.php?u=38762"),
Thanks for getting back to me.  I have noted answers below and also included information from a windows IPCONGFIG /ALL.
Window  =  Windows 7 Professional.  I use Avast on the Windows 7 guest which I  installed when I first installed W7.  It was active when the Windows 7  network worked.
As I mentioned in my post, I used NAT originally but  couldn't get the network to connect.  After some research I found a  recommendation to use Bridged.  I tried Bridged which worked for several  months.  I'm not sure what changed but after a few months the network  connection stopped.  
When I try to diagnose network with windows it indicates a network isn't available.
Do you know or can you recommend a step by step process I can use to determine the cause?


COMMAND PROMPT RESULTS: 
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\lou>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Acer-Win7
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Desktop Adapter
   Physical Address. . . . . . . . . : 08-00-27-4D-F8-EA
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::38ba:dbca:a21d:c3d1%13(Preferred)
   Autoconfiguration IPv4 Address. . : 169.254.195.209(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 185073703
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1B-19-70-A2-08-00-27-4D-F8-EA

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{B292E440-679D-4FC5-8E34-77D6804669C8}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

C:\Users\lou>

---

### Post by slooksterpsv on 2014-07-03
It's obtaining a 169.254.x.x address which means it can't get an address from whatever device it's bridged with. 

Is your host using wifi or ethernet for internet? Then under the bridge setting you'll need to select that one for it to use that bridge. - Just want to make sure on that one.
Is your Wifi for your host using dynamic or static?

You can try changing the network controller on VirtualBox, it's showing you're using the Intel Pro; try the PCnet-FAST III - thats what I'm using on a Server 2008 R2 virtualized instance.

Have you installed the Guest Additions for Windows?

---

### Post by lmancusojr on 2014-07-06
slooksterpsv,
Thanks for the time you have spent attempting to resolve my problem. However the problem was not corrected but resolved.  I reloaded Windows in VB and all appears OK.  However it was OK after I loaded it originally and for the life of me I can not find what occurred to loose network connectivity.  In closing I want to thank you again and know that you provide a wonderful service to us that are not as knowledgeable as you.
Best,
Lou

---

### Post by slooksterpsv on 2014-07-06
You're welcome, if you could mark the thread as solved under thread tools at the top of the page, that'd be great. Sometimes it's weird what happens with the installation. Don't be afraid to ask questions, that's what the forums are for. =D Cheers.

---

