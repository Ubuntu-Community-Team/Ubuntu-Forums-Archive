---
title: "[SOLVED] Problems trying to run my vista-partition under VBox"
date: 2008-11-17
forum: Virtualisation
---

### Post by JeyPeyy on 2008-11-17
I'm trying to get access to my vista partition from Virtualbox, but I have some problems getting it right. This is what I have done so far:

I downloaded the closed-source version of VirtualBox, installed it and ran the command 
```
sudo VBoxManage internalcommands createrawvmdk -filename /home/jp/.VirtualBox/VMDK/Vista.vmdk -rawdisk /dev/sda -partitions 1

```

The terminal tells me the VMDK file was created successfully, so everything seems to be fine. I take a look in that folder and see two vmdk-files. Vista.vmdk and Vista-pt.vmdk.

But when I try to add Vista.vmdk to the virtual disk manager, I get this error message:
```

VD: error opening image file '/home/jp/.VirtualBox/VMDK/Vista.vmdk' (VERR_ACCESS_DENIED).


Result Code:    NS_ERROR_FAILURE (0x80004005)
Component:      HardDisk
Interface:      IHardDisk {fd443ec1-000f-4f5b-9282-d72760a66916}
Callee:         IVirtualBox {557a07bc-e6ae-4520-a361-4a8493199137}

```

So what do I do? I get the same error message when I try to add Vista-pt.vmdk.

---

### Post by chris_nava on 2008-11-17
Check the permissions of /dev/sda You likely don't have permission to access (write to) it as a generic user.

---

