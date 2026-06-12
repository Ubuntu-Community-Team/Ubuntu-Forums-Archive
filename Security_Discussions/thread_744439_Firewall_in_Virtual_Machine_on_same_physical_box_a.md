---
title: "Firewall in Virtual Machine on same physical box as data"
date: 2008-04-03
forum: Security Discussions
---

### Post by nofrak on 2008-04-03
I've been asked to help design a server for a web application.  We're thinking about making three VMs, a firewall(linux), reverse proxy(linux), and app server(windows), all on the same host machine (linux). Is this a security risk, or is this as safe as having multiple physical boxes?

---

### Post by The Cog on 2008-04-03
I guess it's marginally less secure in that you have 4 operating systems instead of 3.

I am not sure that you can run a firewall inside a VM properly. The host is inevitably going to be exposed to the both the dirty and clean sides (and provide a handy firewall bypass for intruders) even if you can arrange two bridge groups inside it. So I would argue that the firewall should be a separate box.

---

### Post by rickyjones on 2008-04-03
The firewall should always be on separate hardware. Having it in a virtual machine will not work the correct way (or the secure way). 

Beyond that, yes, having the rest as virtual machines will work just fine. Just ensure that the host server has redundant network and power connections. I would also keep a second server around for further redundancy.

Sincerely,
Richard

---

### Post by netlogic on 2008-04-03
> **nofrak said:**
> I've been asked to help design a server for a web application.  We're thinking about making three VMs, a firewall(linux), reverse proxy(linux), and app server(windows), all on the same host machine (linux). Is this a security risk, or is this as safe as having multiple physical boxes?

Yes. It depends on the VM server you will be using. If it offers secure a virtual switching, it can be done. Make sure you do a various vulnerability testing before the deployment.

---

