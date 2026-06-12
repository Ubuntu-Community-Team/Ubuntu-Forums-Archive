---
title: "FA120 doesn't work in Sever, works in Desktop"
date: 2010-05-24
forum: Server Platforms
---

### Post by kellon on 2010-05-24
I recently moved from Ubuntu Desktop to Ubuntu Server.  I have a Dell D600 acting as a three prong firewall.  I use a Netgear FA120 USB NIC for the third prong.  After converting to Server, the NIC detects as Eth1.  I'm able to configure an IP, but the NIC never sends or receives packets.  The same NIC works great in Ubuntu Desktop.  Dmesg never shows the NIC being ready.  Anyone have any idea on what the differences could be?

---

### Post by arrrghhh on 2010-05-24
Perhaps restricted drivers you installed to get the netgear card to work on the -desktop install?

---

### Post by kellon on 2010-05-25
Thanks for the reply.  It wasn't a restricted driver.  Does that mean the same driver database is shared between both desktop and server?

---

### Post by arrrghhh on 2010-05-26
> **kellon said:**
> Thanks for the reply.  It wasn't a restricted driver.  Does that mean the same driver database is shared between both desktop and server?

Depends on the driver.  I'd say from a fresh install of both, they would both equally have the same potential of having a particular device work.

However, the -desktop version obviously has the ability to install restricted drivers quite easily, so I thought perhaps you had added that driver on top of your -desktop install to get the card working in the first place.

Try pulling & reinserting the card & then check dmesg again.  Also, does it show up properly in lsusb?

Have you tried getting a cxn on it in a more let's say traditional mode?  Like set it up for DHCP as your only interface for communication.  Isolate it, make sure it works by itself.  It may be something with your configuration.

---

