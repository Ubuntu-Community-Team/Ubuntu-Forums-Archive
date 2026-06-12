---
title: "xhci host controller not responding assume dead"
date: 2020-06-18
forum: Ubuntu Dev Link Forum
---

### Post by rksyeung on 2020-06-18
Hi everyone,

Firstly, let me say that I'm new to this forum.  So please kindly guide me to the right place if this is not it.

As the title suggests, this is the issue I'd like to ask about.  I've a USB 3.0 link to a USB2.0 end-point device, on an embedded system using uboot, and Ubuntu 18.04, Linux 4.14.122.  The error message is reported towards end of Linux initialization.  This error seems to go way back to years ago.

1. Is this indicative of a host controller (possibly its software) or is this the end-point on the other end of the bus?
2. Any good utilities other than lsusb that may review anything about the issue?
3. I've used ehci driver before.  Since end-point is 2.0, presumably I could use ehci instead of xhci.  Any idea how I could reconfigure it to ehci (in case it's the driver)?
4. Would USB analyzer help here?
5. As first step, I'm thinking about checking the power (VBUS, D+/D-).  But this would make any sense only if failure is on end-point.

Any other brainstorming idea?

Thanks,
Raymond

---

