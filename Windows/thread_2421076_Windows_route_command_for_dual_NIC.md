---
title: "Windows route command for dual NIC"
date: 2019-06-16
forum: Windows
---

### Post by MaindotC on 2019-06-16
My primary NIC uses the 192.168.1.x address range from my home router.  I'd like all 192.168.2.x traffic routed to my secondary NIC.  I've tried a few route commands but no matter what I do when I activate the secondary NIC it "takes over" and I lose my Internet connection through the primary NIC.  How can I properly add a route so only 192.168.2.x traffic goes through the secondary NIC?

```

===========================================================================
Interface List
 32...02 00 4c 4f 4f 50 ......Npcap Loopback Adapter
 29...00 1e e5 dc f8 e6 ......Microsoft Virtual WiFi Miniport Adapter #3
 28...00 1e e5 dc f8 e7 ......Linksys WUSB600N Dual-Band Wireless-N USB Network Adapter #
 13...00 ff a3 01 80 1f ......TAP-Win32 Adapter V9
 10...fc aa 14 55 18 79 ......Realtek PCIe GBE Family Controller
 14...0a 00 27 00 00 0e ......VirtualBox Host-Only Ethernet Adapter
  1...........................Software Loopback Interface 1
 34...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 11...00 00 00 00 00 00 00 e0 Teredo Tunneling Pseudo-Interface
 24...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #2
 26...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #3
 30...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
 25...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #5
 33...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #6
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1     192.168.1.12     20
      192.168.1.0    255.255.255.0         On-link      192.168.1.12    276
     192.168.1.12  255.255.255.255         On-link      192.168.1.12    276
    192.168.1.255  255.255.255.255         On-link      192.168.1.12    276
        224.0.0.0        240.0.0.0         On-link      192.168.1.12    276
  255.255.255.255  255.255.255.255         On-link      192.168.1.12    276
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 28    276 fe80::/64                On-link
 28    276 fe80::9c20:1e22:891:24ee/128
                                    On-link
 28    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

```

I want all 192.168.2.x traffic to go through the IP assigned to my secondary NIC 192.168.2.26.
```

C:\Windows\system32>route add 192.168.2.0 mask 255.255.255.0 192.168.2.26

C:\Windows\system32>route print
===========================================================================
Interface List
 32...02 00 4c 4f 4f 50 ......Npcap Loopback Adapter
 29...00 1e e5 dc f8 e6 ......Microsoft Virtual WiFi Miniport Adapter #3
 28...00 1e e5 dc f8 e7 ......Linksys WUSB600N Dual-Band Wireless-N USB Network Adapter #6
 13...00 ff a3 01 80 1f ......TAP-Win32 Adapter V9
 10...fc aa 14 55 18 79 ......Realtek PCIe GBE Family Controller
 14...0a 00 27 00 00 0e ......VirtualBox Host-Only Ethernet Adapter
  1...........................Software Loopback Interface 1
 34...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 11...00 00 00 00 00 00 00 e0 Teredo Tunneling Pseudo-Interface
 24...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #2
 26...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #3
 30...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
 25...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #5
 33...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #6
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1     192.168.1.12     20
          0.0.0.0          0.0.0.0      192.168.2.1     192.168.2.26     10
      192.168.1.0    255.255.255.0         On-link      192.168.1.12    276
     192.168.1.12  255.255.255.255         On-link      192.168.1.12    276
    192.168.1.255  255.255.255.255         On-link      192.168.1.12    276
      192.168.2.0    255.255.255.0         On-link      192.168.2.26    266
     192.168.2.26  255.255.255.255         On-link      192.168.2.26    266
    192.168.2.255  255.255.255.255         On-link      192.168.2.26    266
        224.0.0.0        240.0.0.0         On-link      192.168.1.12    276
        224.0.0.0        240.0.0.0         On-link      192.168.2.26    266
  255.255.255.255  255.255.255.255         On-link      192.168.1.12    276
  255.255.255.255  255.255.255.255         On-link      192.168.2.26    266
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 28    276 fe80::/64                On-link
 10    266 fe80::/64                On-link
 10    266 fe80::6996:c63:d3ab:68f1/128
                                    On-link
 28    276 fe80::9c20:1e22:891:24ee/128
                                    On-link
 28    276 ff00::/8                 On-link
 10    266 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

```

I realize you only want 1 default gateway but it seems the route command doesn't let me define the interface if I don't include a default gateway.

---

### Post by The Cog on 2019-06-16
I don't think the route command you show is creating the default route. I think DHCP is doing it when you connect the second interface up, along with the route that you are trying to add manually. And I notice that the second default has a lower metric, which makes it the preferred default route. I would be inclined to either delete the unwanted default route again, or add a new default route for the first interface with a lower metric again, e.g. "route add 0.0.0.0 mask 255.255.255.255 192.168.1.12 5".

---

### Post by MaindotC on 2019-06-16
> **The Cog said:**
> I don't think the route command you show is creating the default route. I think DHCP is doing it when you connect the second interface up, along with the route that you are trying to add manually. And I notice that the second default has a lower metric, which makes it the preferred default route. I would be inclined to either delete the unwanted default route again, or add a new default route for the first interface with a lower metric again, e.g. "route add 0.0.0.0 mask 255.255.255.255 192.168.1.12 5".

Wow...yes it was DHCP.  I'm working on configuring a dd-wrt on the same model of my current home router and I had DHCP enabled.  I turned off DHCP, set the IP address of my connecting NIC, and re-enabled it and it works now.  No interruption to Internet-facing router.  Thank you so much!

---

