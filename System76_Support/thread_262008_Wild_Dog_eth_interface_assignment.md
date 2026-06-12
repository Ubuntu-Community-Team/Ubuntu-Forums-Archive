---
title: "Wild Dog eth interface assignment"
date: 2006-09-21
forum: System76 Support
---

### Post by lord trousers on 2006-09-21
My Wild Dog can't decide which network card should be eth2 and which should be eth3. Sometimes it switches them when I reboot, which is sort of annoying. I've never had a Linux system do this before. Is there a way to make it behave?

---

### Post by crichell on 2006-09-21
I've heard of this on lots of machines with two interfaces (some laptops with ethernet and wireless seem to do it too).  We kind of get around that by just using network-manager-gnome on laptops and desktops - save for the Wild Dog.

With two ethernet cards and potentially a wireless card it doesn't make sense to go with network-manager-gnome.  Nonetheless - back to your question - I don't see this problem in servers when configuring the interfaces via /etc/network/interfaces - although this shouldn't be different than the GUI possibly setting the cards properties there may help.

I'd like to really know what's going on with this as well - it's a strange occurance that seemed to be introduced to avoid problems when upgrading from Breezy to Dapper.  During our test of the upgrade process on lots of different machines the Dapper upgrade always upped the eth#.

---

### Post by newlinux on 2006-09-21
I had this same problem on my laptop. I ended up setting them in /etc/iftab using the MAC addresses obtained from ifconfig. Haven't had the problem since.

---

### Post by lord trousers on 2006-09-21
Well, this is interesting. Check out my /etc/iftab:

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:17:41:6f:da arp 1
eth1 mac 00:16:17:41:72:3a arp 1

```

Those aren't my MAC addresses. Maybe this has something to do with upping the interface numbers on Dapper?

Anyhow, I'm going to put my real MAC addresses in there to see if that fixes it.

---

### Post by lord trousers on 2006-09-21
My interfaces are now eth0 and eth1, and they *shouldn't* swap again because I'm assigning them by MAC address.

I don't have the time to clear the file out and test to see if they get assigned differently when I reboot. I'll leave that to System76, I guess. :D

---

