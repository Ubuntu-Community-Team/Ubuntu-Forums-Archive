---
title: "Vista Home in VirtualBox Internet Connection: Consistently Inconsistent"
date: 2007-12-25
forum: Virtualisation
---

### Post by JoshHendo on 2007-12-25
Hi,

I recently installed Vista Home (Dells version) in Virtual Box under Gutsy,

Everything seems to work fine, except for the network/internet connection. I have been able to access the internet twice, and not for that long (as in, after I access the Google homepage, I cannot access anything else).

I have both Guest Additions installed and the network card driver separately (from [http://ubuntuforums.org/showthread.php?t=500166](http://ubuntuforums.org/showthread.php?t=500166)).

Any help would be appreciated, as unfortunately, for my school work next year I will be most likely be needing Windows, but I don't know for sure.

- Josh

---

### Post by popch on 2007-12-26
In order to find the source of your problem, the output of the command 'ipconfig /all' could be useful.

[LIST]
[*]Start Windows in your virtual machine.
[*]Open a command window in Windows
[*]Enter the command 'ipconfig /all'
[*]Copy all of the answer and paste it into the forum for us to see.[/LIST]

---

### Post by JoshHendo on 2008-01-05
> **popch said:**
> In order to find the source of your problem, the output of the command 'ipconfig /all' could be useful.

[LIST]
[*]Start Windows in your virtual machine.
[*]Open a command window in Windows
[*]Enter the command 'ipconfig /all'
[*]Copy all of the answer and paste it into the forum for us to see.[/LIST]
```

Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\josh>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Scruffy-Vista
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : AMD PCNET Family Ethernet Adapter (PCI)
   Physical Address. . . . . . . . . : 08-00-27-C8-D9-86
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 10.0.2.15(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, 5 January 2008 4:43:27 PM
   Lease Expires . . . . . . . . . . : Sunday, 6 January 2008 4:43:26 PM
   Default Gateway . . . . . . . . . : 10.0.2.2
   DHCP Server . . . . . . . . . . . : 10.0.2.2
   DNS Servers . . . . . . . . . . . : 10.0.2.3
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{CA09D971-196A-4428-A7CE-03491AA7C
B73}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{CA09D971-196A-4428-A7CE-03491AA7C
B73}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:10.0.2.15%12(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 10.0.2.3
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Users\josh>

```

---

### Post by fjgaude on 2008-01-05
From where are you getting your Internet service? That ipv4 of 10.etc. is interesting, at least to me.

From what I see you don't go through a router?

---

### Post by JoshHendo on 2008-01-05
I am connected to a wireless router on my Ubuntu computer, and that wireless router is connected to the internet modem/router.

In VirtualBox, the network settings are set to NAT, and I have been able to get Internet occasionally (since I posted this, there was a time where I was able to get Internet most times I restarted).

I don't think it would have anything to do with the signal strength? Later today I will try wireing my computer to the wireless router and see if that makes a difference.

- Josh

---

### Post by popch on 2008-01-06
The ipconfig data which you supplied look clean. The network, router and DNS addresses are those VMBox usually supplies, and the MAC address of the virtual NIC looks about right, too.

Do you happen to know if the internet was accessible for your Vista VM at the time you issued the ipconfig command?

Do you happen to know if the internet is accessible for your Ubuntu computer at the times it is not accessible for the Vista VM? In other words: is it the real connection of your PC to the internet or the virtual connection of your virtual PC to the (real) internet which causes the problem?

---

### Post by Slingshot on 2008-01-06
Have you tried manually setting the address?

Correct me if I am wrong as its been a while when I lasted used windows in VirtualBox, but shouldn't the address point to the same place not a separate DNS address?

---

