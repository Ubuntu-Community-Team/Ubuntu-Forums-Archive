---
title: "Unidentified Network issue"
date: 2015-04-05
forum: Windows
---

### Post by Shamik_Biswas on 2015-04-05
Hi all,

I am using local BroadBand connection through Ethernet cable directly  connected to the CPU. The problem I am facing for the last 72 hrs. is  that [COLOR=#ff0000]I cannot connect to the Internet. The Network Connection shows  'Ethernet Unidentified Network'.[/COLOR]

ISP provider has given me the following IPv4 configuration :

IP -              172.16.115.236
Subnet -          255.255.255.192
Defauly gateway - 172.16.115.193

Preferred DNS - 172.16.115.193
Alt DNS -       8.8.8.8


ipconfig/all shows the following :


Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe FE Family Controller
   Physical Address. . . . . . . . . : 28-92-4A-4C-C1-EE
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::bd55:ed6b:4806[IMG]http://m.bestofmedia.com/sfp/images/design/usr/smilies/biggrin.gif[/IMG] 120%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 172.16.115.236(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.192
   Default Gateway . . . . . . . . . : 172.16.115.193
   DHCPv6 IAID . . . . . . . . . . . : 262190028
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-17-DD-33-79-28-92-4A-4C-C1-EE

   DNS Servers . . . . . . . . . . . : 172.16.115.193
                                       8.8.8.8
   NetBIOS over Tcpip. . . . . . . . : Enabled


ping 172.16.115.193 -t

Request timed out
Destination host unreacheable


ping 172.16.115.236 -t
showing proper message

Reply from 172.16.115.236 bytes 32 time 1ms TTL 128

[B]
Please suggest what is the resolution.[/B]

---

### Post by Kenneth_Benson on 2015-04-06
Have you checked the Win 7 firewall to see if it's correctly configured?

---

