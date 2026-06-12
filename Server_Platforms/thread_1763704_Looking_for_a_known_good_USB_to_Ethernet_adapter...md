---
title: "Looking for a known good USB to Ethernet adapter..."
date: 2011-05-20
forum: Server Platforms
---

### Post by focaccio on 2011-05-20
Greetings!

There has to be someone(s) out here that needed two ethernet ports on their Ubuntu Server laptop...and got an USB to Ethernet adapter working to make it happen. 

Please share your experience!  I am building Ubuntu server laptops.  They get shipped to customer locations and connected to the network for testing.  Having the ability to get an interface on the inside and outside is very handy.

Thanks,
Greg

---

### Post by volkswagner on 2011-05-21
I don't know how good it is, but it works, it's cheap, and is recognized with most any Linux distro I throw at it.

[http://cgi.ebay.com/New-USB-Ethernet-10-100-RJ45-LAN-Network-Adapter-USA-/200530330670?pt=LH_DefaultDomain_0&hash=item2eb08a042e](http://cgi.ebay.com/New-USB-Ethernet-10-100-RJ45-LAN-Network-Adapter-USA-/200530330670?pt=LH_DefaultDomain_0&hash=item2eb08a042e)

```
 *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:10:13:48:d4:60
       size: 10MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=dm9601 driverversion=22-Aug-2005 duplex=half firmware=Davicom DM9601 USB Ethernet link=no multicast=yes port=MII speed=10MB/s
```

---

### Post by focaccio on 2011-05-31
Thanks for the input.  I appreciate it.  If I test it out I will let you know how it works.

---

