---
title: "Xbox 360 controller 'grayed out' in VirtualBox"
date: 2011-05-11
forum: Virtualisation
---

### Post by v1nsai on 2011-05-11
I've got a fake knockoff Xbox 360 controller that I'm *this* close to being able to play onlive with in my VirtualBox.  Vbox sees it, but its grayed out and I can't attach it to the system.  I'm guessing this is because my host system still has a hold on it, but I don't know how to 'eject' it so that vbox can grab it.

Any help appreciated, I'm thiiiiis close to not having to reboot into wind0ze to game.

---

### Post by 3177 on 2011-05-11
please post the output of:```
lsusb
```

---

### Post by v1nsai on 2011-05-12
```
v1nsai@v1nsai-mint ~ $ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 002: ID 1bad:f900 Harmonix Music **
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


I've bolded the controller as it shows up in lsusb.  I've tried adding filters for it in VirtualBox, if that's what your going to suggest ;)  I removed all the information except for the vendor ID, and it still was grayed out when I started the vm.

---

### Post by 3177 on 2011-05-13
which vbox are you using?
OSE, or the one strait from oracle.
OSE doesn't support usb.

---

