---
title: "Ubuntu Doesn't See Network Interfaces"
date: 2010-04-29
forum: Server Platforms
---

### Post by swu on 2010-04-29
I have a web server running on Ubuntu 8.04 LTS that is having issues. In troubleshooting this I moved the HD over to a spare server of the same model Dell PE750 server.

When I boot the server, everything loads but it does not see the network interfaces. If I do a ifconfig, it only shows the loopback, not eth0 or eth1 that are defined in /etc/network/interfaces. The interfaces are enable in the BIOS and light up the switch, so they are active.

Can you not move a ubuntu install to another identical server? Or how do I get it to re-discover the network interfaces on this server?

Many thanks in advance!

---

### Post by cdenley on 2010-04-29
The kernel used for ubuntu 8.04 did not include a driver for the network cards in your server. You can either use a newer kernel (compile yourself), a newer release of ubuntu, another distro, or compile the driver yourself (and repeat for every kernel upgrade).

[http://cateee.net/lkddb/web-lkddb/IGB.html](http://cateee.net/lkddb/web-lkddb/IGB.html)
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=1636&DwnldID=9180&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=1636&DwnldID=9180&lang=eng)

---

### Post by Aquaseafoam on 2010-04-29
NOTE: I have only tried this on Lucid Lynx RC so far.

BACKUP THE FILE BEFORE ATTEMPTING ANY CHANGES

You may want to (In /etc/network/interfaces) try deleting all of the interfaces that include "eth0" as part of the their line.

For example, delete "auto eth0" but not "auto lo"

Reboot, then see if it recognises any of the interfaces now.

---

### Post by cdenley on 2010-04-29
> **Aquaseafoam said:**
> NOTE: I have only tried this on Lucid Lynx RC so far.

BACKUP THE FILE BEFORE ATTEMPTING ANY CHANGES

You may want to (In /etc/network/interfaces) try deleting all of the interfaces that include "eth0" as part of the their line.

For example, delete "auto eth0" but not "auto lo"

Reboot, then see if it recognises any of the interfaces now.

As I said, I don't think there is a driver for the network cards in the 2.6.24 kernel, so I don't think this is going to help. If your interfaces don't show up with this command
```

ifconfig -a

```
then nothing in /etc/network/interfaces is going to make them appear.

---

### Post by Iowan on 2010-04-29
**cdenley** is apparently familiar with what card is in your server and what drivers it should use - otherwise, I'd suggest **sudo lshw -C network** to get more information.

---

### Post by cdenley on 2010-04-29
> **Iowan said:**
> **cdenley** is apparently familiar with what card is in your server and what drivers it should use - otherwise, I'd suggest **sudo lshw -C network** to get more information.

Google can be very informative.
[http://en.community.dell.com/support-forums/servers/f/1466/t/7612115.aspx#ID001](http://en.community.dell.com/support-forums/servers/f/1466/t/7612115.aspx#ID001)

---

