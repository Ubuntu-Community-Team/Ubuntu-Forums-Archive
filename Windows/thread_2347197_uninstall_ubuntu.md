---
title: "uninstall ubuntu"
date: 2016-12-22
forum: Windows
---

### Post by alexkoganov on 2016-12-22
how do i install win 10 instead of ubuntu assuming that i allready have a bootable win 10 usb??

its important to say that my ubuntu running on efi:
alex@alex:~$ dmesg | grep "EFI v"
[    0.000000] efi: EFI v2.31 by American Megatrends


thanks

---

### Post by howefield on 2016-12-22
Moved to the "*Windows*" forum.

---

### Post by oldfred on 2016-12-22
Drive with be gpt. Windows will then only install in UEFI boot mode.
So you must be sure to boot Windows installer in UEFI boot mode. UEFI should offer two boot modes one UEFI and one not.

[https://ubuntuforums.org/showthread.php?t=2257711&p=13200435#post13200435](https://ubuntuforums.org/showthread.php?t=2257711&p=13200435#post13200435)

---

