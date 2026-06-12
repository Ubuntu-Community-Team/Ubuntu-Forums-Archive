---
title: "Setting up wireless on Ubuntu Server"
date: 2009-04-13
forum: Server Platforms
---

### Post by cmwslw on 2009-04-13
I am trying to set up a simple web server but the computer I'm using isn't directly connected to the Internet. I have just bought a [PCI wireless card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166021"), which is supported by Ubuntu. I installed Ubuntu Server, but I don't know how to enable wireless in order to connect to the Internet. The installation auto-configuration of the network failed because the network was apparently "not using the DHCP protocol". I assume this is not a problem since the [guide I am using]("http://www.howtoforge.org/perfect-server-ubuntu8.04-lts-p3") instructs me to disable DHCP anyways. Does anyone know how can I set up wireless support?

Thanks in advance,
Cory Walker

---

### Post by ugm6hr on 2009-04-13
Enable the wifi card using the commandline:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by hyper_ch on 2009-04-13
IMHO running a server off a wifi is not such a good method. Preferrably would be to have it attached to a router or switch.

---

### Post by RedSingularity on 2009-04-13
Yeah a hard line to the net is probably the better way to go.......if possible of course.

---

### Post by cmwslw on 2009-04-13
> **hyper_ch said:**
> IMHO running a server off a wifi is not such a good method. Preferrably would be to have it attached to a router or switch.

Okay, I guess I will do that. If I attatch the computer to the router, will it be the same as having it directly connected? Also, can I set up the server to use a static IP while still having the other computers on my network use dynamic IP's? All of this is so confusing to me ](*,).

Cory

---

### Post by ugm6hr on 2009-04-13
> **cmwslw said:**
> If I attatch the computer to the router, will it be the same as having it directly connected?
I'm not sure I know what you mean by "directly connected" - perhaps if you tell us how your network is currently set up?

If you have 1 router, and 1 modem (or a combined modem-router), then just plug an ethernet patch cable from the server into the router and set up port-forwarding of port 80 to the server (on the router setup page).

If you don't have a router (with firewall) at all, then you could consider using the server as a firewall / router and web server.  This would require 2 networking cards though.

> Also, can I set up the server to use a static IP while still having the other computers on my network use dynamic IP's?

Yes.  Just use the same IP subnet range and set the gateway the same.

e.g. my router / gateway IP = 192.168.1.1
my DHCP computers = 192.168.1.2 to 192.168.1.4 (router range 192.168.1.2 to 192.168.1.254)
my server static IP = 192.168.1.250 (well outside my needs for DHCP connections).

---

