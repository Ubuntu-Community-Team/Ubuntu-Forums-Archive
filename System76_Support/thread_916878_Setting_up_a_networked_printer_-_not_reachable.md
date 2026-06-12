---
title: "Setting up a networked printer - not reachable"
date: 2008-09-11
forum: System76 Support
---

### Post by glacialfury on 2008-09-11
Just a pointer to the "official" thread in ubuntu forums.  You guys are less anonymous than the great wide world of Ubuntu.

I bought a linux-supported laser printer that I hooked up to the router, all is seen but nothing pingable.  Details are below.

[http://ubuntuforums.org/showthread.php?t=916815](http://ubuntuforums.org/showthread.php?t=916815)

**NOTE: the not-pinging is due to an error I made.**  The thread has been updated, and further explanation is available in the fifth post of this thread.

---

### Post by thomasaaron on 2008-09-11
So, you installed the drivers, but it is unclear as to whether or not you actually set up the printer via System > Administration > Printing.

Otherwise, I don't think Ubuntu will actually have a link to the printer.

---

### Post by glacialfury on 2008-09-11
After I ran the installation script that came with the printer, it showed up fine under system-admin-printers.  All the details are listed there, including the ipp address etc.

Since the printer is connected directly to the router, I should be able to ping it regardless of what computer on the network I'm pinging from, shouldn't I?  I was also unable to ping it from a Windows machine on the network.

---

### Post by thomasaaron on 2008-09-11
I don't know a ton about this, but if you can't ping it from multiple computers, it kind of sounds like it is a router setting that is off. Perhaps a 'Forwarding' setting?

---

### Post by glacialfury on 2008-09-11
I made a mistake in my thinking earlier.  I found out how to print the config page of the printer which lists the IP and mac address.  That mac address is not listed on the router page at all.  It gets confusing because the router doesn't actually list connected devices, it lists active leases, and has some insanely long lease period, so what I *assumed* was the printer was actually something that had been plugged in ages ago and is no longer plugged in - hence it not being pingable.

That said, that means the router doesn't see the printer at all.

Now, the printer lists its IP address as 192.0.0.192.  I know the DHCP range of the router is pretty standard, the 192.168.1.x - 192.168.1.y set.  Perhaps this is causing them not to see each other? However, when something is plugged into the router, that's when I thought it was automatically assigned a valid address on the network.

---

