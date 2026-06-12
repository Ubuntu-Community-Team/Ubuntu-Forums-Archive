---
title: "Backup a Complete Virtual Machine?"
date: 2009-06-29
forum: Server Platforms
---

### Post by lightnb on 2009-06-29
If I wanted to backup an entire Virtual Machine (in case of host hardware failure), which files would I need to save? The Virtual Machines are KVM / Libvirt running on a 9.04 Host.

I would imagine the Machine Definition XML files in "/etc/libvirt/qemu" and the Virtual Hard Drive (disk0.qcow2) in "/etc/libvirt/Machines".

Anything else? Or is the XML Definitions and Virtual Hard Drives enough to drop on a new host and go?

Thanks,

Nick

---

### Post by R.Bucky on 2009-06-29
You would need to locate the folder for your Virtual Machines and simply copy that folder. i have done this many times without a hitch for Virtual MS based OS's, Linux, and FreeBSD.

---

### Post by lightnb on 2009-06-29
Thanks!

I guess in my case that would be "/etc/libvirt/" that gets backed-up.

---

### Post by juancarlospaco on 2009-06-29
etckeeper for automation, see server docs at ubuntu.com

---

### Post by lightnb on 2009-06-30
Can you backup a virtual machine hard drive while the VM is running? Or will that create a corrupt file?

---

### Post by TurboRush on 2009-06-30
It is probably safer to suspend the VM first. 

I personally wrote a small script to suspend my VMServer while I run a backup to make avoid any chance of corruption (I actually suspend it, copy the files to another location and then back them up).

---

