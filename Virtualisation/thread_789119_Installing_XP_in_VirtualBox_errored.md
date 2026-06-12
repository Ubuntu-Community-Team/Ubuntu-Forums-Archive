---
title: "Installing XP in VirtualBox errored"
date: 2008-05-10
forum: Virtualisation
---

### Post by ade234uk on 2008-05-10
I started installing XP inside VirtualBox. Towards the end of the set up process the damn thing bsod me. I deleted the Virtual Machine and went to try and install again. When I goto specify the disk size I get the following error. How do I get around this? Thank you


Falied to create a hard disk image '/home/xxxx/.VirtualBox/VDI/win.vdi' (VERR_DISK_FULL).


Result Code: 
0x80004005
Component: 
VirtualDiskImage
Interface: 
IVirtualDiskImage {a8265b5a-0d20-4a46-a02f-65693a4e8239}

---

### Post by TenPlus1 on 2008-05-10
It seems that the file (virtual hard-drive) you are trying to make is too big for the filesystem you are using...  Are you running Ubuntu on it's own ext3 drive or wubi under Windows XP/Vista ???

---

### Post by ade234uk on 2008-05-10
I am running it under Wubi.

---

