---
title: "How to install windows 7 on usb with grub"
date: 2017-03-03
forum: Windows
---

### Post by pe89+ on 2017-03-03
Title says it all

---

### Post by yancek on 2017-03-03
The windows installer is designed to NOT install to a usb drive.  If you try it you will see the following Message:

> windows setup does 
not support configuration or installation to a disk connected through usb or IEEE 1394 ports

You can extract thee windows files from an iso file and copy them to a flash drive and boot it with Grub but Grub has nothing to do with installing as it is only a bootloader.

---

### Post by pe89+ on 2017-03-03
Oh ok thanks. But the reason I asked that was because I think i installed grub in the wrong partion and now instead of booting into ubuntu, it boots into grub

---

### Post by pe89+ on 2017-03-03
I want to install windows 7 and i get  message saying canot find normal.mod in i386 folder but the file is in the x86_64-efi folder is there any way i can change the directory in grub rescue

---

### Post by deadflowr on 2017-03-03
To take a quick stab at this I would assume this means Ubuntu is installed, and it it installed in UEFI mode.
But that the Windows 7 install media is for 32-bit, which cannot be installed in UEFI mode.

If this is the case, unfortunately you will need to completely wipe out the Ubuntu install, reset your BIOS from UEFI mode to legacy BIOS and then try installing again.

But that's a mildly educated guess based on the fact that 
a) 32-bit versions of Windows 7 installation medias are very common and 
b) you have a populated x86_64-efi folder, and that folder would not be populated if it the system that installed it was not in UEFI mode, or at least shouldn't be populated.

That is my two cents,
right or wrong

---

### Post by howefield on 2017-03-04
Moved to the "*Windows*" forum and related threads merged.

---

