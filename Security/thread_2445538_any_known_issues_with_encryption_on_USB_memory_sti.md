---
title: "any known issues with encryption on USB memory sticks?"
date: 2020-06-15
forum: Security
---

### Post by Skaperen on 2020-06-15
are there any known issues with fulldisk style (or that way by partition) encryption on a USB 3.0 _memory stick_ (or external flash drive).  i'm curious about experiences.  i want to disable automount on the stick itself even if i plug it into a system with automount enabled (my laptop normally has automount disabled).  i might want to network it up to the cloud to mount it there (and make sure the cloud instance is doing the crypto).  i'll probably be doing *ext4* in the secure space but am open to other ideas.

---

### Post by C.S.Cameron on 2020-06-15
I have recently been playing with Full disk encryption on a Ubuntu Full install Sandisk Cruzer Fit USB drive.
I used the regular installer with advanced features installation type. [https://askubuntu.com/questions/1244344/trying-to-create-a-persistent-live-usb-with-full-disk-luks-encryption/1244409#1244409](https://askubuntu.com/questions/1244344/trying-to-create-a-persistent-live-usb-with-full-disk-luks-encryption/1244409#1244409)
Had to remove the HDD to make the USB and it only worked in BIOS mode, the mode I made it in.
I previously made a Full disk encryption on a Ubuntu Full install using Paddy Landau's method.
[https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption)
It took a little longer but worked on both BIOS and UEFI.

---

### Post by Skaperen on 2020-06-16
so it needed to see the USB disk as [COLOR=#0000ff][FONT=courier new]**/dev/sda**[/FONT][/COLOR] (it would have been [COLOR=#0000ff][FONT=courier new]**/dev/sdb**[/FONT][/COLOR] if the HDD  was still attached)?

---

### Post by C.S.Cameron on 2020-06-17
Yes, sda if only one drive plugged in.

---

### Post by Skaperen on 2020-06-18
and what did you install from?  bootable CD or DVD?

---

### Post by C.S.Cameron on 2020-06-19
Often I install a Live System to the target USB and boot toram. I am then able to install to the same disk which would be sda. The BIOS/UEFI booter can be created booting in BIOS mode, EFI system partition is created ahead of time.

---

