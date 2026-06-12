---
title: "Double reboot to get eth0 going?"
date: 2012-04-30
forum: Server Platforms
---

### Post by fizgig on 2012-04-30
Using 10.04 server on bare metal and I can't reboot remotely since the eth0 interface wont come up on every other reboot.  Has anyone else seen this?  I've found some posts related to this but they involve virtual machines which I'm not doing.

---

### Post by Krupski on 2012-04-30
> **fizgig said:**
> Using 10.04 server on bare metal and I can't reboot remotely since the eth0 interface wont come up on every other reboot.  Has anyone else seen this?  I've found some posts related to this but they involve virtual machines which I'm not doing.

Try this:

Take the file [FONT="Lucida Console"]**[COLOR="Blue"]/etc/udev/rules.d/70-persistent-net.rules[/COLOR]**[/FONT] and rename it to [FONT="Lucida Console"]**[COLOR="Blue"]/etc/udev/rules.d/70-persistent-net.rules.original[/COLOR]**[/FONT] and then reboot.

The system will re-generate that file with the correct info for your NIC and (hopefully) this will solve your problem.

If it all fails, rename your backed up file (*.original) to it's normal name.

Hope this helps.

---

### Post by fizgig on 2012-04-30
By the way, I don't even see the (integrated) ethernet device in lspci on these occasions.

The device is:
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)

---

### Post by fizgig on 2012-04-30
Thanks for the idea.  Didn't seem to work...


> **Krupski said:**
> Try this:

Take the file [FONT="Lucida Console"]**[COLOR="Blue"]/etc/udev/rules.d/70-persistent-net.rules[/COLOR]**[/FONT] and rename it to [FONT="Lucida Console"]**[COLOR="Blue"]/etc/udev/rules.d/70-persistent-net.rules.original[/COLOR]**[/FONT] and then reboot.

The system will re-generate that file with the correct info for your NIC and (hopefully) this will solve your problem.

If it all fails, rename your backed up file (*.original) to it's normal name.

Hope this helps.

---

### Post by elico on 2012-05-01
what BCM5787driver are you using? what kernel?
you can check if the net card module is loaded.
or might reload it to make sure it's loaded.

---

### Post by fizgig on 2012-05-10
The kernel being used is: 2.6.32-41-generic-pae

I'm not sure how to find out what network driver I'm using but shouldn't that not matter when it comes to lspci?  Shouldn't lspci list the device on the pci bus whether a driver is installed or not?

Sometimes it's shown in the list, other times it isn't.

---

