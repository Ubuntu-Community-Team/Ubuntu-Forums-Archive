---
title: "Finding optimal virtualization solution."
date: 2010-11-09
forum: Virtualisation
---

### Post by kharnam on 2010-11-09
Hello all,

I'm looking for virtualization solution to implement the following scenario:

[LIST=1]
[*]Creating Virtual Machine (VM) + Installing guest OS (Windows/Linux), applications, DB etc.
[*]Creating image of VM (including all things installed on it) and possibly compressing this image to reduce storage space consumption (assumed creating of repository contains images of VMs).
[*]Fast managing of VM images including fast deployment, cloning etc.[/LIST]
So, my question is:
What is virtualization software meeting my requirements (I mean VMWare ESXi, Xen, KVM etc.)? May be it's a bundle of software (solution)?

I tried a VMWare ESXi but it doesn't have any tools to create/manage images.

---

### Post by ghostborg on 2010-11-09
Give Virtualbox (Oracle) a try. Get it from the website because the one in the repository, at least in the past , the usb ports are not implemented.

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

