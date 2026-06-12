---
title: "virtualized router"
date: 2011-11-18
forum: Server Platforms
---

### Post by vortmax on 2011-11-18
I'm the sysadmin for a small research cluster and I'm running out of rack space, so I'm consolidating systems.  I just acquired an old Pentium D server with 4 Gig of ram that I want to set up with either KVM or VMware server, and move some of my servers over to it (dhcp, DNS, NIS domain controller, network monitoring server, etc).  One of the machines I want to consolidate into it is my gateway router.  

Before I begin this project, are there any major reasons why this wouldn't work?  I have dual NIC's, so one would be completely dedicated to the outside line and the other would be the inside line running to the main switch.

---

### Post by gregfaust on 2011-11-19
I don't think an old Pentium-D will support Intel VT (virtualization extensions) required by KVM.  Xen might be a good choice for a hypervisor if all of the guests will be Linux.  VMware ESXi will work without VT, but without VT it will use about 50% more CPU overhead than Xen.

---

