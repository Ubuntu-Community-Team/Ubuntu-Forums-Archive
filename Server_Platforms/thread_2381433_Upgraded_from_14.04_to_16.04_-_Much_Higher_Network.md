---
title: "Upgraded from 14.04 to 16.04 - Much Higher Network Utilization"
date: 2017-12-31
forum: Server Platforms
---

### Post by bsntech on 2017-12-31
Main question - is there any specific/easy way to find out where network utilization is coming from?

More detailed info -

I have a bare-bones host OS.  It has KVM/qemu installed, x2go server, lxde.  That is pretty much it - simply to support virtual machines.

In 14.04, the bridge network connection averaged maybe 30 kbps inbound.

Now with 16.04, the bridge network connection averages 350 kbps.

It isn't really "breaking" anything but that is a HUGE difference in average network utilization for a server that shouldn't be doing much of anything.

---

### Post by TheFu on 2017-12-31
netstat, lsof, iostat and the firewall logs.  Every service/daemon should also have logs, especially for connections.

If my network traffic was 10x higher than previously and I'd just installed a new OS, I would check all connections for attack attempts and data extraction.  If connections are from/to places that don't make sense, then my WAN firewall and server firewall aren't doing the job correctly.  At least 2 layers of protection is required, so when 1 is bypassed, then the other is still there working.

---

