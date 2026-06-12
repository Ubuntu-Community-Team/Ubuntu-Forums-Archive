---
title: "Linux Lite ACPI error"
date: 2022-07-16
forum: Ubuntu/Debian BASED
---

### Post by tyhhrr on 2022-07-16
Hey there! im new with  linux OS and have this messeges at the start of the Os "APCI BIOS ERROER FAILURE CREATING NAMED OBJECT".. 
so i do some research, and find this tool "boot-repair", but its say s that it would be better to ask before repair, just to be sure, here is the link with the info

[https://paste.ubuntu.com/p/8yTnszKGV9/](https://paste.ubuntu.com/p/8yTnszKGV9/)

im using a linux lite version,
any advice or suggestion would be nice! ty all

---

### Post by oldfred on 2022-07-16
Moved to your own thread. You should not post in another thread with new issue.
Not Ubuntu so moved to Ubuntu/Debian based sub-forum.

Most ACPI errors can be ignored.
You show both BIOS & UEFI installs.
But grub in gpt's protective MBR, will not work as you show ESP - efi system partition and mount of ESP in fstab. So last update must have been UEFI based.
You may just need to change UEFI settings to default boot in UEFI mode.
Not sure grub reinstall even required, but if doing it in UEFI mode, it should not make any real difference.
Just never boot in BIOS/CSM/Legacy mode as that will just give you a grub> entry as grub in MBR is now invalid.

---

