---
title: "Best way to make a VM file of a Ubuntu 20 server"
date: 2024-11-13
forum: Virtualisation
---

### Post by NotQuiteSU on 2024-11-13
I need to rebuild my Ubuntu server. It's running, but hanging on by a thread, so I'd like to virtualize it, run it in VMWare Pro, HyperV, virtualbox, anything. (I'll rebuild on the hardware)

I wanted to use VMware converter, but it requires going to an esxi server, which I don't have running at the moment.

Any suggestions would be awesome, thanks!

---

### Post by TheFu on 2024-11-13
The way I used to do this was to use my normal backup methods, then create a VM with sufficient storage to hold everything I needed.  I think the last migration was from Xen to KVM/QEMU as the hypervisor.  Since moving the KVM/QEMU, I haven't had any issues moving to new hardware or new OSes on the host system.  I can probably find a VM backup with 10.04 on it and I know I have migrated some systems from 12.04 forward to 20.04.  Sometime in the next 6 months, I'll need to migrate those to a newer OS. Just need to make the final selection at this point, but my choices are a newer Ubuntu Server or a stable Debian Server.

Anyway, using the backup/restore method is the least risky AND it let's you test your backup/restore processes.   After all, if your HW fails, it is very unlikely you'll be able to replace it with identical HW, so being able to restore to different hardware is mandatory, especially for servers.   And if you don't have backups that support that already, I'd say the data/processing really isn't very important, so does it matter if it fails?

I vaguely remember that Redhat made a utility called **p2v** for this purpose.  [https://docs.redhat.com/en/documentation/Red_Hat_Enterprise_Linux/6/html/V2V_Guide/chap-V2V_Guide-P2V_Migration_Converting_Physical_Machines_to_Virtual_Machines.html](https://docs.redhat.com/en/documentation/Red_Hat_Enterprise_Linux/6/html/V2V_Guide/chap-V2V_Guide-P2V_Migration_Converting_Physical_Machines_to_Virtual_Machines.html)  Whether that is a paid tool or not, IDK.

Found this [https://github.com/libguestfs/virt-p2v](https://github.com/libguestfs/virt-p2v) too.

I've never used either.

---

