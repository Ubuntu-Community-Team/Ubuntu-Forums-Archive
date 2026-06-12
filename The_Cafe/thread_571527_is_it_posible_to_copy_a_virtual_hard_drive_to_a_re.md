---
title: "is it posible to copy a virtual hard drive to a real one?"
date: 2007-10-09
forum: The Cafe
---

### Post by markp1989 on 2007-10-09
i have set u p a virtual pc exactly how i want it, i was wondering if it was possible using dd or something similar to copy the virtual to a real hard disk?

i tried dd if=/path/to/virtualdrive.vdi of=/dev/sdb

 but that just gives me and invalid partition table on my usb hard drive

can any one cast some light on this situation, and i will be extreamly great full

---

### Post by HermanAB on 2007-10-09
VMware has a tool to do that.  With other virtual systems you are probably out of luck.

---

### Post by markp1989 on 2007-10-09
> **HermanAB said:**
> VMware has a tool to do that.  With other virtual systems you are probably out of luck.

ok, thanks for you help, i will look in to vmware some time soon

---

### Post by reacocard on 2007-10-09
It the virtual OS linux? If so you can probably just set up a network share from the VM and copy files over, then install GRUB to the MBR of the new partition by hand and edit /etc/fstab and /boot/grub/menu.lst to reflect the new drive.

---

### Post by HermanAB on 2007-10-09
This thing can do it:
[http://vmware.com/products/converter/](http://vmware.com/products/converter/)

You can do conversions like this manually, but since the tool is free there is not much point in struggling with it.

Cheers,

H.

---

### Post by markp1989 on 2007-10-09
> **HermanAB said:**
> This thing can do it:
[http://vmware.com/products/converter/](http://vmware.com/products/converter/)

You can do conversions like this manually, but since the tool is free there is not much point in struggling with it.

Cheers,

H.

i tried this , but it doesnt see image files from virtualbox

---

### Post by Jose Catre-Vandis on 2007-10-09
Do as reacocard says, (for a Linux install) and just copy files to a new partition. You will probably have to do some hardware reconfiguration e.g. graphics/xorg, but it should work. With XP/Vista you will be on stony ground, these two get really hacked off about the different hardware, although with XP you can try a repair install from CD, which will keep some of your settings (but you may have to reinstall apps). Vista I do not know about, but i guess it will be even more hacked off than XP, and probably refuse any action :)

---

### Post by RAV TUX on 2007-10-09
> **markp1989 said:**
> i have set u p a virtual pc exactly how i want it, i was wondering if it was possible using dd or something similar to copy the virtual to a real hard disk?

i tried dd if=/path/to/virtualdrive.vdi of=/dev/sdb

 but that just gives me and invalid partition table on my usb hard drive

can any one cast some light on this situation, and i will be extreamly great fullYou can do this in QEMU.

---

