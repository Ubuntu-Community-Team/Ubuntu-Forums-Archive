---
title: "Reboot message"
date: 2015-03-13
forum: Ubuntu Development Version
---

### Post by zkab on 2015-03-13
I have Ubuntu 15.04 (3.19.0-9) - both servers & desktops.
After upgrading from 3.19.0-8 -> 3.19.0-9 and reboot I received following before my ssh-connection was closed.

PolicyKit daemon disconnected from the bus.
We are no longer a registered authentication agent.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

dmesg & syslog don't show any errors or warnings ...

How can that be fixed ?

---

### Post by grahammechanical on 2015-03-13
> [COLOR=#000000]How can that be fixed ?[/COLOR]

By daily updating and hoping that the developers patch something. I got kernel 3.19.0-9 with today's update and it will not build a kernel module for the Nvidia driver. And I need to use Nvidia drivers. So, I am reverting to using kernel 3.19.0-7 until things are fixed.

I also got the switch from upstart as default to systemd as default and that has added and extra 80 seconds to loading time and I am getting a "failed to start Load Kernel modules" with kernel 3.19.0-7. I am also reverting to using upstart.

If things worked fine with kernel 3.19.0-8 then use that kernel. If systemd is giving problems then use upstart. We have a little more than 7 weeks to 15.04 release day. Time enough for there to be another kernel revision or systemd to be patched or put back as an Advance option with upstart as the default.

Regards.

---

### Post by ventrical on 2015-03-14
Yes.. the above is a very good synopsis of the state of things current.

Regards..

---

### Post by zkab on 2015-03-14
> **grahammechanical said:**
> By daily updating and hoping that the developers patch something

Thanks - that's the way to go ...

---

