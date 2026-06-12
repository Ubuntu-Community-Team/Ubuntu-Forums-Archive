---
title: "which dhcp package to install?"
date: 2006-11-27
forum: Server Platforms
---

### Post by ArcticSnowman on 2006-11-27
So I installed 6.10 onto a box and set about creating a
DNS/DHCP/LAMP server....   Followed the instructions given in the documentation section..

DNS/LAMP working ok.... basic DHCP working ok with simple subnet..

Now I want to do dynamic update of the DNS with the DHCP leases for the Windows boxes... However the dhcpd package I installed does not like any of the ddns-*** commands in the dhcpd.conf file...

```
sudo apt-get install dhcpd
```

So I was wondering, which dhcpd package(s) should I have?

```

snowman@lordvetinari:/etc$ apt-cache search dhcpd
dhcp3-server - DHCP server for automatic IP address assignment
dhcp - DHCP server for automatic IP address assignment
dhcpdump - Parse DHCP packets from tcpdump
gadmintools - GTK+ server administration tools
gdhcpd - GTK+ configuration tool for dhcpd3-server
udhcpc - very small DHCP client
udhcpd - very small DHCP server

```

---

### Post by Iowan on 2006-11-28
I installed **dhcp3-server**... but mostly because I didn't realize the other options existed.  I couldn't tell you if it does dynamic update of the DNS - my DNS is on another box (the router...).

---

