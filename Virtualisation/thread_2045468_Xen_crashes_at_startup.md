---
title: "Xen crashes at startup"
date: 2012-08-21
forum: Virtualisation
---

### Post by Dy1anW on 2012-08-21
So, I'm pretty new to VT, and I've just installed Xen (have yet to install Win7 as a guest). Strangely it seems that the startup is a bit fickle; sometimes it will start, and sometimes it'll hang. When it does hang I get the message:

could not write bytes: Broken pipe
[20.231840] XENBUS: Unable to read cpu state
[20.232064] XENBUS: Unable to read cpu state
[20.232276] XENBUS: Unable to read cpu state
[20.232482] XENBUS: Unable to read cpu state
[20.232765] XENBUS: Unable to read cpu state
[20.233021] XENBUS: Unable to read cpu state
[20.233228] XENBUS: Unable to read cpu state
[20.233433] XENBUS: Unable to read cpu state

What's going wrong?
I'm running Ubuntu 12.04 on a laptop, and using xen-hypervisor-4.1-amd64 and xen-tools from repos.

Many thanks.

---

