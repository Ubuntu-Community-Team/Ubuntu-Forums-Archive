---
title: "How to Configure Ethernet on Ubuntu Server"
date: 2013-02-02
forum: Server Platforms
---

### Post by schemex on 2013-02-02
When you initially install Ubuntu server they allow you to auto-configure it to your router. Today we upgraded internet, and that would change internet settings (changing routers, providers, etc.) I would appreciate if someone could tell me how to run the automatic configure code for internet configuration. If I have to manually do it I will appreciate some explanation because I am new at Ubuntu Servers.

NEW INFO
The new internet:
(AT&T) 2Wire modem -> netgear ethernet switch-> computer
the old one was:
(Comcast) Motorola Cable Modem -> Netgear Router -> netgear ethernet switch-> computer

---

### Post by d4m1r on 2013-02-02
Type of internet? Is the server connected to a router?

---

### Post by lisati on 2013-02-02
*Thread moved to **Server Platforms**.*

---

### Post by Cheesemill on 2013-02-02
If the server uses DHCP to get its address then no reconfiguration is needed.

If the server has a static IP set up then you need to edit the /etc/network/interfaces file to make any changes.

---

### Post by schemex on 2013-02-02
> **d4m1r said:**
> Type of internet? Is the server connected to a router?
NEW INFO
The new internet:
(AT&T) 2Wire modem -> netgear ethernet switch-> computer
the old one was:
(Comcast) Motorola Cable Modem -> Netgear Router -> netgear ethernet switch-> computer
added to initial post

---

### Post by darkod on 2013-02-02
You have to be precise with the terms. Earlier you had a modem then a router, and then the switch. In this case, a dhcp or static setting would be enough because the router is in between the public WAN and local LAN.

If in the new setup, the modem is only a modem, as you wrote, you can't expect it to continue working. You will probably need to set up some sort of PPPoE connection on the server. Your provider might need to provide the details of the connection like username, password, etc.
Or simply insert a router in between, but the WAN port of the router would still need to be configured with PPPoE unless your modem is doing that.

A lot of ISP devices are actually a combined modem/router, in which case it would do the job of your older modem+router setup and you don't need any major changes to the server interface settings. Maybe chanching the static IP if the modem/router uses different subnet, etc.

It depends what exactly is the modem passing on.

---

