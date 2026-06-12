---
title: "Making file system usable..."
date: 2014-05-10
forum: Virtualisation
---

### Post by LastDino on 2014-05-10
I recently came across this peculiar thing while running LX-pup on my VM.

[ATTACH=CONFIG]253034[/ATTACH]

It's stuck there for like more than 40 Min. I'm curious, what's exactly going on? Is it something to do with type of disk we select for VM? I chose parallel virtual disk.

---

### Post by tfrue on 2014-05-10
I believe it's just giving you root access (Switch_root) of the file system and then probably mounting the filesystem (Making the FS usable)

Chris

---

### Post by TheFu on 2014-05-10
I don't know what "parallel virtual disk" means. Modern distros should support **virtio**, failing that, use **SATA** for the disk controller.

Which hypervisor is being used?

---

### Post by LastDino on 2014-05-10
> **tfrue said:**
> I believe it's just giving you root access (Switch_root) of the file system and then probably mounting the filesystem (Making the FS usable)

Chris
It takes that much time? I actually had to shut it down since it wasn't rally doing anything. You could see that on disk and hd indicators at bottom of VM. They were not blinking, so probably no process was going on.

> **TheFu said:**
> I don't know what "parallel virtual disk" means. Modern distros should support **virtio**, failing that, use **SATA** for the disk controller.

Which hypervisor is being used?

Hypervisor? o-o
I'm not sure exactly what you're referring to but VirtualBox is the software and Xubuntu is host.
/pardon my lack of knowledge.

---

### Post by TheFu on 2014-05-10
Change the disk controller to virtio and use a fully pre-allocated vHDD for storage. You should see 90% of native I/O performance that way for a single VM.  40 minutes is too long for anything. Clearly, a low-end CPU and limited RAM will also impact performance, especially in Vbox.

---

### Post by LastDino on 2014-05-11
> **TheFu said:**
> Change the disk controller to virtio and use a fully pre-allocated vHDD for storage. You should see 90% of native I/O performance that way for a single VM.  40 minutes is too long for anything. Clearly, a low-end CPU and limited RAM will also impact performance, especially in Vbox.

Thanks, I'll try it and get back here if any changes.

---

