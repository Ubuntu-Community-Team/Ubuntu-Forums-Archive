---
title: "Unable to login to Xen instance after update on Hardy!?"
date: 2009-03-12
forum: Server Platforms
---

### Post by tominglis on 2009-03-12
I have Xubuntu Server 8.04.2 running the Xen Hypervisor 3.2. I have 7 Xen instances running Apache / PHP / Passenger, vsFTPd, MySQL servers.

I recently updated my server with a number of updates, mainly to do with Xen and Pidgin, and I am now no longer able to communicate with my Xen instances via SSH or the XM Console. I can see the web pages they are hosting in my browser.

Does anyone know what could be the problem?

---

### Post by windependence on 2009-03-12
The update probably updated your kernel. Xen runs it's on kernel and any updates can mess it up. That's one of the reasons I run VMware.

In case you're interested, VMware has two free hypervisors. VMware Server runs on top of Ubuntu, whereas VMware ESXi runs on the bare metal, no OS is required. Both products are free along with the management tools to run them.

-Tim

---

