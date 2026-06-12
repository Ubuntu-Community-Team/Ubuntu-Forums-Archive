---
title: "usb drive"
date: 2008-02-09
forum: Virtualisation
---

### Post by junaid.kollam on 2008-02-09
i install windows xp in qemu.but i can't access usb card reader in it.is it possible to access usb card reader.help me to access it

---

### Post by fjgaude on 2008-02-09
I don't use the VM you are using but I think adding a line to your **fstab** file could do the trick:

```
gksudo gedit /etc/fstab
```

Add this line at the bottom of the file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Let us know if it works.

---

