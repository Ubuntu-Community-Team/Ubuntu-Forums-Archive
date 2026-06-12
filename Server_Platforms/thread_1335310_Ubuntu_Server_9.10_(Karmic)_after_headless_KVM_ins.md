---
title: "Ubuntu Server 9.10 (Karmic): after headless KVM install, server VM has no console"
date: 2009-11-23
forum: Server Platforms
---

### Post by grenoml on 2009-11-23
I did  headless text-based install of Ubuntu Server 9.10 (Karmic) into a KVM virtual machine.  This went fine and at the end of the install the VM rebooted.  The hypervisor restarted the VM and reconnected me to the domain console but there is no output.

I had added the console parameters to the kernel line during the installation screens but it seems that wasn't enough to get a console screen.  Either that or something else is wrong like maybe grub didn't install the boot loader properly.  

Has anyone experienced this issue?

---

