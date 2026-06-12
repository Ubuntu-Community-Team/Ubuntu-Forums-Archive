---
title: "VirtualBox and KVM on 9.10 Server?"
date: 2010-04-24
forum: Virtualisation
---

### Post by TheFu on 2010-04-24
The question is - **Can both KVM and VirtualBox be run simultaneously on the same server with both acting as the hypervisor?**

I'm working on a disaster recovery plan for a small business. They use VirtualBox on Windows for desktop virtualization and are planning to use KVM on an Ubuntu Server for Windows and Linux server virtualization. 

Each user has their own vbox image and it is backed up weekly. They'd like to use a netbook and VNC/RDP into the XP image running under VirtualBox on an existing server already running KVM. Removal of KVM isn't an option and there are no spare PCs or servers to dedicate for this task capable of running virtualbox.

In fact, if this method proves to be viable, they may only use netbooks in the future and always run "productivity apps" remotely. For now, being able to move the image file around between Windows and Linux hosts is important.

We already use OpenOffice and other Linux-based tools, but sometimes we need MS-Office (MS-Visio in particular) and require 100% compatibility with MS-only customers.

Thoughts?

---

### Post by abacate_vw on 2010-05-16
> **TheFu said:**
> The question is - **Can both KVM and VirtualBox be run simultaneously on the same server with both acting as the hypervisor?**

No, unfortunately you can't. As both use hardware CPU extensions, use only one hypervisor at a time.

---

### Post by TheFu on 2010-05-16
So if I really want to do this, then I'd be best off by creating a few partitions and booting accordingly.

swap (shared)
/ (KVM boot)
/ (virtualbox boot)
/home (shared)
/var (shared)   <--- can this be shared? Aren't APT caches kept here?
/opt (shared)

Honestly, I'd setup a 10GB partition for the least used kernel, settings  and  20GB for my main config. Then setup grub to boot each to avoid the mixed hypervisor  package issue.

Workable?

---

### Post by Toon Macharis on 2010-11-17
You would be able to convert a VirtualBox image to a QEMU image and from there to a KVM image?  I am not sure how it works, you should check the Internet.

I have however my doubts that running virtualized remote desktops on netbooks is the most productive way of doing things (but no one prevents you experimenting to find out).

---

### Post by Toon Macharis on 2010-11-17
> **Toon Macharis said:**
> I have however my doubts that running virtualized remote desktops on netbooks is the most productive way of doing things (but no one prevents you experimenting to find out).

Let me explain why I think the approach above would not work:

* if you virtualize all desktops on 1 server, the CPU/disk/network will be shared among all virtual desktops.  A powerfull CPU may be able to handle multiple desktops, a shared disk and network will probably be very slow.

* A remote desktop introduces lag and requires a fair amount of network bandwidth.  If you lose the network, so do you lose your remote desktop on your thin client.

* Netbooks have a tiny screen, keyboard and CPU.  They are fine to take on the go.  Yet I am not sure if they are the best for intensive use?  Since you are talking about a back up every week, I assume the computers are used rather intensively?

Instead of virtualizing desktops, you might consider setting up a repository in a version control system as Subversion, have the employees commit their files in this version control system on a central server and back up this repository instead?

---

