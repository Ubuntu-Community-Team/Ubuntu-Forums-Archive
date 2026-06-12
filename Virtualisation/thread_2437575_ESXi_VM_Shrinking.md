---
title: "ESXi VM Shrinking"
date: 2020-02-26
forum: Virtualisation
---

### Post by ligistx on 2020-02-26
This isn't specific to Ubuntu, but the VM's in question are ubuntu 18.04.4 LTS so I figure folks here likely could help.

I have an ESXi homelab and I very much accidentally assigned way to much disc space to some VM's that don't need it. I do have Veeam running on a Windows LTSC VM in case things go south, but I am not even sure where to start. The VM's in question are Ubuntu 18.04.4 LTS and they are running under ESXi 6.5 U2 and are thick provisioned. I am just not sure the best way to go about this at all. I am not even sure where to start.
 
My Veeam backup of one example is 5 GB but I gave the VM 20 GB (its a VM that won't really grow for any appreciable reason on its own, and 10 GB would be PLENTY). Obviously, 10 GB isn't a huge issue, but I have a handful of VM's I could trim down similarly, and ~40 GB is non-trivial. Sure, another SSD for a second datastore is also ~50 bucks which is trivial, but still, homelabs are here for us to learn on, so I figure why not figure out how to do this....
 
Any help would be great!

TDLR; Need help shrinking an Ubuntu VM under ESXi that is thick provisioned.

---

### Post by TheFu on 2020-02-26
I haven't used ESX/i in about a decade.  Most people here will be using KVM, Xen or VirtualBox.  I've used all of them, but use KVM exclusively now. 
There's a tool, **qemu-img        resize [-q] filename [+ | -]size**
From the qemu-img manpage, seems vmdk file from VMware are supported:
```
       Other
           QEMU also supports various other image file formats for
           compatibility with older QEMU versions or other hypervisors,
           including VMDK, VDI, VHD (vpc), VHDX, qcow1 and QED. For a full
           list of supported formats see "qemu-img --help".  For a more
           detailed description of these formats, see the QEMU Emulation User
           Documentation.
```

Backup everything before starting.  Bad things happen sometimes.

---

