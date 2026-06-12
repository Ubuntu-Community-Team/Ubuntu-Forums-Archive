---
title: "[SOLVED] Gamepad in vmware server"
date: 2008-02-19
forum: Virtualisation
---

### Post by Zalbor on 2008-02-19
I have a usb gamepad which was designed for windows XP. I'm using Gutsy and I have an installation of XP in vmware server.
Plugging in the gamepad, it seems that Ubuntu recognizes the device:
(end of dmesg output)
```
[ 2013.516946] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 2013.708733] usb 4-2: configuration #1 chosen from 1 choice
[ 2013.810792] usbcore: registered new interface driver xpad
[ 2013.810985] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
```

Normally, usb devices appear in the VM>Removable Devices>USB Devices of vmware server (my printer and external hard drive appear there). But there's no entry for the gamepad, so I can't connect it to the VM.

Does anyone know why that happens?

---

### Post by Zalbor on 2008-02-19
Apparently it being recognised wasn't enough, I had to install an extra driver (in Ubuntu).

---

### Post by fjgaude on 2008-02-19
That makes sense. For something to be recognized in vm guest it has to be recognized by the host, even though the host can't actually use that something.

---

### Post by Zalbor on 2008-02-19
Yeah, but what I found out was that even though the host did recognize it (isn't that what the dmesg output indicates?) it still needed the proper driver before it would work in the guest.

---

### Post by fjgaude on 2008-02-19
Did you have an install disk for the pad for Windows?

It's like saying I have a driver for one of my printers that work fine in Windows but not in Ubuntu. Anyway, one way or another we get things to do what we wish them to do, eh?

---

### Post by Zalbor on 2008-02-19
Mm, not sure if you understood what I meant...
I had to install a driver for the gamepad in ubuntu, before vmware would recognize it as a USB device and allow me to connect it to windows (where another driver installation was needed).
The output from dmesg though, was from before I installed the ubuntu driver.

---

