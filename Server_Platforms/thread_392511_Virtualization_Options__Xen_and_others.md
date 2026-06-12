---
title: "Virtualization Options / Xen and others"
date: 2007-03-24
forum: Server Platforms
---

### Post by josir on 2007-03-24
Hi folks,

this is my first attempt to start a virtualization project on my ubuntu development server. My virtualization needs is only with Linux. I don't need any MS or Mac stuffs.

This server is a AMD64 3200 / 2Gb RAM / Gigabite motherboard (Nvidia video) / 
Edgy 2.6.15-28-amd64-generic

Everything is working great, several 64bits applications were installed, even Beryl 0.2 was installed to impress MS-zealots :), etc.

1) I tried first XEN based on [https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy)

but I got a "kernel panic - not syncing - attempt to kill the idle task"

I've got confused because the howto said to issue:

sudo apt-get install xen-hypervisor-3.0-amd64 xen-image-xen0-2.6.17-6-generic-xen0 xen-utils-3.0 xen-ioemu-3.0

But the last amd64 kernel is 2.6.15 ?! Is this correct or I can't installed xen with this kernel?

Any tip will be welcome!
Josir Gomes

---

### Post by Brazen on 2007-03-24
Personally, I like VMWare Server.  It's easy to use, though I would like to switch to something Open Source.

---

### Post by josir on 2007-03-26
Hi Brazen, 

thanks for your reply.

VMWare is not a native virtualization option. It's generally slower than XEN or VServer. A good guide to see the differences in virtualization is:

[http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

But it's worthy to virtualize Windows SO, slow but useful.

Have you try any other program?

Josir

---

