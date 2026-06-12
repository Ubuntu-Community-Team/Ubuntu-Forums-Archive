---
title: "DHCP needed for pxe boot?"
date: 2008-05-18
forum: Server Platforms
---

### Post by phynix on 2008-05-18
I have a computer that I would like to use as a pxe boot server, but I am confused about dhcp. Right now I have a Clark Connect box which acts as an internet gateway between my router and modem. My question is whether I need to edit that dhcp server inorder to make pxe to work.

---

### Post by Lapp-Same on 2008-05-19
> **phynix said:**
> I have a computer that I would like to use as a pxe boot server, but I am confused about dhcp. Right now I have a Clark Connect box which acts as an internet gateway between my router and modem. My question is whether I need to edit that dhcp server inorder to make pxe to work.

have you installed dhcp3-server On the server??
or are you using a allready configured edition?

Anyway

If you allready have DHCP installed you just go in to you're router and edit the standard gateway to the ip-adress of the server...

-Christoffer-

---

### Post by phynix on 2008-05-20
Ok wait does the dhcp server have to be between the modem and the switch or can it be connected through the switch.

---

### Post by phynix on 2008-05-20
ok so if it is between the router and the modem how do you set which interface connects to the wan or the lan

---

