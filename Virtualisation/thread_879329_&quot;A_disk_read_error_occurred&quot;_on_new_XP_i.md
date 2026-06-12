---
title: "&quot;A disk read error occurred&quot; on new XP install"
date: 2008-08-03
forum: Virtualisation
---

### Post by scotters on 2008-08-03
Just did a clean install of Ubuntu after having run this configuration for several months. Ubuntu 8.04, KVM/qemu. Previously had no issue at all. After this install, got KVM/qemu set, set up the VM, and began the XP install. After the initial install, XP requires reboot. On boot, "a disk read error occurred". Re-did, no change. Wha....?

---

### Post by abreslav on 2008-10-01
I have the same problem

---

### Post by yuriry on 2008-11-03
I had the same problem while using Virtual Machine Manager UI. But when using a command line it seem to go beyond the failure point:

I used the image file created by the UI:

```

kvm -m 512 -cdrom /dev/cdrom -boot d /home/user/XP.img
```

After the re-boot I used this command line, which boots from a hard disk

```

kvm -m 512 -cdrom /dev/cdrom -boot c /home/user/XP.img
```

The last command is probably the only one required to continue the installation after the **a disk read error occurred** error.

---

### Post by beflapje on 2008-11-06
Got exactly the same problem .
The suggestion you gave does not work for me.

there is a bugreq open Bug #105195

---

### Post by Panam on 2008-11-28
I also have the same issue with WinXP. Probably because I cant put it in accelerate mode without undefining the vm and start all over again. That is why it would also be nice to have the possibility to add more XML elements to that libvirt template file, like --accelerate.
It also could be due to missing 'vmware-like' txt-mode drivers on the Windows XP ISO image or boot CD.

---

### Post by Yann2 on 2008-12-01
Hello guys! I can help here. Haven't had time to add this to the wiki yet.
The problem comes from virt-install that doesn't generate a qcow2 image. Use qemu-img to convert the image to qcow2 just after you run virt-install  before starting the VM:

sudo qemu-img convert windows.qcow2 -O qcow2 windows2.qcow2

Once this is run on the image, I got the VM run fine accelerate without problems. I have run in some problems using KVM without virtio, so I would recommend you install virtio drivers for windows; you should also get a lot better network performances. Just google for virtio and windows, can't remember the address right now :)

Good luck, KVM rocks ;)

---

### Post by st0kes on 2009-01-21
> **yuriry said:**
> I had the same problem while using Virtual Machine Manager UI. But when using a command line it seem to go beyond the failure point:

I used the image file created by the UI:

```

kvm -m 512 -cdrom /dev/cdrom -boot d /home/user/XP.img
```

After the re-boot I used this command line, which boots from a hard disk

```

kvm -m 512 -cdrom /dev/cdrom -boot c /home/user/XP.img
```

The last command is probably the only one required to continue the installation after the **a disk read error occurred** error.

Hi yuriry: I have exactly the same problem and your solution worked for me. But I would prefer to use virt-manager to run my VM, is there a way to get this to work in the GUI? Since I completed the installation my VM will not start at all in virt-manager.

---

### Post by geichel on 2010-06-23
If your command line qemu is working but not under virt-manager, check the file permissions for your disk image. Make sure the user running virt-manager has write permissions. -G

---

