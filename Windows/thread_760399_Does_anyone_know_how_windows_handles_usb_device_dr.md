---
title: "Does anyone know how windows handles usb device drivers?"
date: 2008-04-20
forum: Windows
---

### Post by Tuna-Fish on 2008-04-20
So I heard something rather unbelievable from a friend, namely that when you plug in a small usb device, like an usb memory stick, windows reads some driver code from the device, and executes it in kernel. I tried to find if this was false by reading some WDM documents, but frankly, I couldn't find anything in there. Does someone here perhaps know better?

---

### Post by sayakb on 2008-04-20
Windows 2000 or later comes equipped with USB and HID drivers. So almost all the USB flash devices as well and HIDs like USB mouses etc. get working as soon as you plug it in.

---

### Post by insane_alien on 2008-04-20
one thing i've noticed on windows, is that if you have a USB device that requires a driver(say a USB modem or webcam) plugged in and working to one port will require you to search for the driver again if you plug it into another USB port on the same computer. why is this? gets really annoying. 

no idea why it should care.

---

### Post by lpkizz on 2008-04-20
> **insane_alien said:**
> one thing i've noticed on windows, is that if you have a USB device that requires a driver(say a USB modem or webcam) plugged in and working to one port will require you to search for the driver again if you plug it into another USB port on the same computer. why is this? gets really annoying. 

no idea why it should care.

because windows is stupid and don't know better u should take it easy on the little girl not all are created great like Ubuntu

---

### Post by smoker on 2008-04-20
> **insane_alien said:**
> one thing i've noticed on windows, is that if you have a USB device that requires a driver(say a USB modem or webcam) plugged in and working to one port will require you to search for the driver again if you plug it into another USB port on the same computer. why is this? gets really annoying. 

no idea why it should care.

yes, seems to happen every time i install a usb wireless adapter - i install it on a handy front usb port, set everything up, all ok. unplug the device, drag out the pc and plug it in a rear usb port, and damn it, doesn't work!:confused:

i think the particular port used with an installed device must be registered somewhere and it won't use another port, tho why this can't be fixed i don't know!

---

### Post by lswest on 2008-04-20
usually XP downloads drivers it needs for USB sticks/devices if the drivers aren't already present, and then allocates that driver to the device in the certain USB port, so that if you move it, it re-installs the driver for the new USB port, thinking it's a new device.

---

### Post by insane_alien on 2008-04-20
> because windows is stupid and don't know better u should take it easy on the little girl not all are created great like Ubuntu

i was looking for something a little more technical and a lot less fanboyish.

at least the others were what i was looking for. thanks.

---

### Post by lswest on 2008-04-20
I'm pretty sure it writes the USB port into a registry entry correspondingly created when you install the drivers/software required for the device.  Therefore, if you move it, it "re-installs" and edits the registry entry.  

*EDIT* ah, you weren't talking about my post :P

---

### Post by insane_alien on 2008-04-20
yeah, i wrote the post then wheni submited it i got ninja posted by you two theni edited it to show who i was talking to.

---

### Post by 3rdalbum on 2008-04-21
> **Tuna-Fish said:**
> So I heard something rather unbelievable from a friend, namely that when you plug in a small usb device, like an usb memory stick, windows reads some driver code from the device, and executes it in kernel.

There are a very small number of devices that actually contain their own drivers. They do this by emulating a CD drive to begin with, where you can manually install the drivers for the device from the CD image. The real drivers will be able to tell the true nature of the device and dispense with the CD tomfoolery. Great idea, except that if you plug the device into a non-Windows system, you just get a freaking CD icon pop up on screen, and no correct functionality.

Windows doesn't need to run driver code from a USB memory stick, as the driver necessary is called "USB Mass Storage", and is built into every USB-enabled operating system.

As for executing drivers in-kernel, yes Windows does that, but it appears to be moving away from this.

---

### Post by Tuna-Fish on 2008-04-22
> **3rdalbum said:**
> Great idea, except that if you plug the device into a non-Windows system, you just get a freaking CD icon pop up on screen, and no correct functionality.
... Or except that all you need to do to take over any windows system ever built is to plug in an usb key with a specially crafted trojan in it. So much for security in public computers.

There are different degrees of physical access, and this one needs only the second easiest.

I gotta stop using library computers for logging into anything important, they might have keyloggers.

---

