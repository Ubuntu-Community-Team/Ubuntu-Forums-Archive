---
title: "For those who roll their own 2.6.14 is out"
date: 2005-10-28
forum: The Cafe
---

### Post by matthew on 2005-10-28
Linux kernel 2.6.14 is now in stable release for those interested.

[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by mlomker on 2005-10-28
Coolio.  I'm going to give it another whirl.  The last time I tried to run 2.6.13 on Hoary I found a few things (VMWare) that wouldn't compile for me.

---

### Post by berserker on 2005-10-28
My Logitech MX1000 laser mouse works in 2.6.13.4 but not in 2.6.14.  Here's the output of /var/log/Xorg.0.log

```
**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Buttons" "12"
(**) Option "Emulate3Buttons" "false"
(**) Option "ZAxisMapping" "11 12 10 9"
(**) Configured Mouse: ZAxisMapping: buttons 11, 12, 10 and 9
(**) Configured Mouse: Buttons: 12
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:02:0c.2-2.2/input0"
(EE) Configured Mouse: cannot open input device
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:02:0c.2-2.2/input0"
(EE) Configured Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices
```

I changed nothing in xorg.conf and used the config file from 2.6.13.4.

Any ideas?

---

