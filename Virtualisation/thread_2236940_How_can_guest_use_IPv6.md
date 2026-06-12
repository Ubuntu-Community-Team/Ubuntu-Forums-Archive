---
title: "How can guest use IPv6?"
date: 2014-07-29
forum: Virtualisation
---

### Post by amturnip on 2014-07-29
In virt-manager, I chose "Virtual network 'default': NAT" for the Windows I bought and installed.  Later, I got a new wifi router that's IPv6-capable and suddenly my Ubuntu has a global IPv6 address.  But the Windows (guest) does not seem to be enjoying it.  According to Windows' ipconfig, the guest has an IPv4 address and a "pseudo" IPv6.  In Ubuntu ifconfig shows "virbr0" (I do not know if this is important) with only an IPv4 address, 192.168.122.1.  How can I let the guest (Windows) enjoy IPv6 without the pseudo thing?

---

### Post by TheFu on 2014-07-30
Inside the guestOS, what is the output from **ipconfig /all**?

BTW, most ISPs do not support IPv6, so this will only be useful for learning inside your personal network, and only on those devices which support v6.  

For any lurkers, there is free IPv6 training available at [https://ipv6.he.net/certification/](https://ipv6.he.net/certification/)

If you are into security and are NOT ready for IPv6, it is best to completely block it at the router. IPv6 can be tunneled through IPv4 and it will appear like it is outside any firewall, naked on the internet. Be careful out there.

---

### Post by amturnip on 2014-08-02
Here's the ipconfig output.  I see a link-local IPv6 and a Toledo Tunneling Pseudo Interface but no honest-to-goodness IPv6 address. 

I saw in the news that my ISP, Comcast, reported 100% IPv6 deployment and indeed all I had to do was remove an obstacle-- my old incapable wifi router.  Now in Ubuntu, when I say "host google.com", the answer includes 2607:f8b0:4004:802::1005.  And I can ping6 that address.  Anyway here's what the guest says (and in the guest I cannot ping the aforementioned google address; the request times out).  

```
Windows IP Configuration

   Host Name . . . . . . . . . . . . : Eeyore
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8139C+ Fast Ethernet NIC
   Physical Address. . . . . . . . . : 52-54-00-5D-E9-B0
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::50c9:7806:acd7:437%3(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.122.87(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, August 2, 2014 8:50:48 AM
   Lease Expires . . . . . . . . . . : Saturday, August 2, 2014 9:50:48 AM
   Default Gateway . . . . . . . . . : 192.168.122.1
   DHCP Server . . . . . . . . . . . : 192.168.122.1
   DHCPv6 IAID . . . . . . . . . . . : 55727104
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1B-47-11-78-52-54-00-5D-E9-B0
   DNS Servers . . . . . . . . . . . : 192.168.122.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{5094EF66-E65B-4F6F-9F8D-180F517769CA}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:90d7:103a:3720:3f57:85a8(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::103a:3720:3f57:85a8%5(Preferred) 
   Default Gateway . . . . . . . . . : ::
   DHCPv6 IAID . . . . . . . . . . . : 134217728
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1B-47-11-78-52-54-00-5D-E9-B0
   NetBIOS over Tcpip. . . . . . . . : Disabled
```

---

### Post by TheFu on 2014-08-02
> **amturnip said:**
> Here's the ipconfig output.  I see a link-local IPv6 and a Toledo Tunneling Pseudo Interface but no honest-to-goodness IPv6 address. 

I saw in the news that my ISP, Comcast, reported 100% IPv6 deployment 

That cannot be true.  I'm on comcast and cannot get native IPv6 on my connection. There are specific areas - relatively tiny - around with IPv6, but if you didn't sign up for the beta testing, I don't think you have it.

I have IPv6 addresses on some of my machines too - that means nothing.  Check the WAN interface of the router to know.

---

