---
title: "Virtualbox most usb devices work, 1 doesn't"
date: 2010-08-30
forum: Virtualisation
---

### Post by kg4ojl on 2010-08-30
A friend of mine is trying to get away from windows, but needs to run windows vista in Virtualbox. It runs ok, but 1 device a epson stylus photo 1400 (usb 2.0) printer is grayed out and is unavailable if you move the mouse over it. All the others usb devices are selectable but that one.

host: Ubuntu 10.04
guest: Windows Vista in virtualbox 3.2.6

Thank,
David.

---

### Post by kg4ojl on 2010-08-30
Oh, one other thing. The printer works great in ubuntu. no problems.

---

### Post by fjgaude on 2010-08-30
Did the Epson printer disk get loaded into the Windows VM?

---

### Post by kg4ojl on 2010-08-30
I didn't get that far. I can't switch control of the printer from Ubuntu to windows, so windows would never know the device is there. All of the others usb devices are able to change control to windows but the printer. Even an hp usb printer will work.

---

### Post by fjgaude on 2010-08-30
Well, without the printer driver being loaded into Windows it's not there. HP is a special situation with Linux, I think, but Epson is not.

---

### Post by kg4ojl on 2010-08-30
Yeah, but usually in windows driver or no driver when you plug a usb device in windows it will prompt for a driver or say that it could not install the hardware. My problem is no different than the printer being plugged in at all, as far as windows running inside of virtualbox is concerned. The printer is there under usb devices in virtualbox, but it is greyed out. others usb devices are not.

---

### Post by fjgaude on 2010-09-02
I don't use VBox anymore but maybe you are limited to how many USBs it will handle. Try de-selecting one and see if the printer is clear.

VMware Player sees all the USB devices but is limited to using four at a time. I wonder if something like that might apply to VBox?

---

### Post by smilingfrog on 2010-09-08
The problem is most likely due to group permissions. You should add the user to the lp group to give vbox access to the printer functions.

[http://ubuntu.ubuntuforums.org/showthread.php?t=1299512&page=4](http://ubuntu.ubuntuforums.org/showthread.php?t=1299512&page=4)

Good luck
:)G

---

