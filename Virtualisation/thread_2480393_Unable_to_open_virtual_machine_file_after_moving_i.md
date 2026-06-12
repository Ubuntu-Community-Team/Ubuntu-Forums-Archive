---
title: "Unable to open virtual machine file after moving it to a new partition"
date: 2022-10-28
forum: Virtualisation
---

### Post by fabjapan on 2022-10-28
Hi Guys,
I had to change the location of my virtual machine vbox file as I had to make some changes on my partition.
As I try to open it now, I get this below error message:

Failed to open virtual machine located in /mnt/WINDOWS/VirtualBox VMs/Windows10/Windows10.vbox.
Trying to open a VM config **'/mnt/WINDOWS/VirtualBox VMs/Windows10/Windows10.vbox'** which has the same UUID as an existing virtual machine.
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]MachineWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}[/TD]
[/TR]
[TR]
[TD]Callee:[/TD]
[TD]IVirtualBox {d0a0163f-e254-4e5b-a1f2-011cf991c38d}[/TD]
[/TR]
[/TABLE]


I would really appreciate if someone could guide me to a resolution (either an existing thread or directly letting me know the best way to approach it.

BTW, I am using Version 6.1.38 r153438 (Qt5.15.3) on Ubuntu 22.04

---

### Post by TheFu on 2022-10-28
```
Trying to open a VM config '/mnt/WINDOWS/VirtualBox VMs/Windows10/Windows10.vbox' which has the same UUID as an existing virtual machine.
```
Duplicate UUIDs for a VM aren't allowed by virtualbox.  Change it or delete the old VM if there are 2.

---

### Post by fabjapan on 2022-10-29
Thank you so much. I should have thought about it...

I tried and is now solved

---

