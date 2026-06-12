---
title: "VirtualBox: Creating a bootable USB"
date: 2013-06-30
forum: Virtualisation
---

### Post by honzi97 on 2013-06-30
Hello everybody,
when I try to create a vmdk file in order to boot from USB (in VirtualBox) I get this error message:  

VBoxManage: error: Error code VERR_FILE_NOT_FOUND at /build/buildd/virtualbox-4.1.12-dfsg/src/VBox/Storage/VMDK.cpp(3614) in function int vmdkCreateRawImage(PVMDKIMAGE, PVBOXHDDRAW, uint64_t)
VBoxManage: error: Cannot create the raw disk VMDK: VERR_FILE_NOT_FOUND
VBoxManage: error: The raw disk vmdk file was not created

Can you help me with this?
Thanks

---

### Post by Cheesemill on 2013-07-01
I'm not sure about your errors but I've used the [Plop]("http://www.plop.at/en/bootmanagers.html") iso to successfully boot VirtualBox from a USB drive.

---

