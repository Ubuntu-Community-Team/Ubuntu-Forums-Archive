---
title: "Bootable USB Installing Kali Linux"
date: 2016-12-25
forum: Ubuntu/Debian BASED
---

### Post by mattonfire on 2016-12-25
I am aware this isn't technically Ubuntu, I just assumed it would be quite similar. For some reason I cannot install Kali on my computer, I create the bootable USB drive yet it won't show up on the boot menu. Kali doesn't support Efi, does this Bios only support EFI? Insydeh20 (BIOS), please help. It won't recognise my USB's. I've tried so much.

---

### Post by mikewhatever on 2016-12-25
...why would you assume that?

---

### Post by jeremy31 on 2016-12-25
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by sudodus on 2016-12-25
Welcome to the Ubuntu Forums :-)

Maybe it depends on the version, but I have a version (of Insydeh20 in a Toshiba laptop) with a menu entry to switch between UEFI and BIOS mode, which is called CSM in the menu.

---

### Post by yancek on 2016-12-25
What 'boot menu' are you referring to?  You need to check the BIOS and set the usb to first boot priority there.  First check to see if the usb is recognized in the BIOS and if it is, you should be able to set it first in boot priority.  The method for doing this varies widely depending upon the manufacturer.  Do you have another computer available where you can try to test boot the Kali usb?

---

### Post by mattonfire on 2016-12-25
Yup, I set all options as priority before the hard drive (Windows) the bios lets you change the priority of the options without needing them to be in the machine, so I was able to change the order of the queue of the disk for example without a disk being input. Yes, I have my main computer, it runs fine on that but that has a difference Bios. It is able to pickup the USB fine.

[Solved] Ask if someone has a problem with this.

---

### Post by sudodus on 2016-12-30
Congratulations :KS

Is post #6  describing your solution? If not please describe it now. Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

