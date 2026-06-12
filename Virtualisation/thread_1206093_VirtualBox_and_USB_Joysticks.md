---
title: "VirtualBox and USB Joysticks"
date: 2009-07-06
forum: Virtualisation
---

### Post by kurio99 on 2009-07-06
I have installed VirtualBox 3.0.0 on Ubuntu 9.0.4 Jaunty Jackalope.  The guest OS is Windows XP with Guest Additions installed.  The group, vboxusers, is set up with my ID added.  My USB memory key works fine from the Guest OS.

However, I cannot get any USB joysticks or gamepads to work with Virtualbox.  I tried the various solutions involving fstab, udev, and mountdevsubfs.  It would seem that if memory sticks work fine then the USB set up for VirtualBox is correct.  The problem seems to be unique to devices handled by joydev.  I tried blacklisting joydev but the error remains the same.  Any suggestions on how to resolve this problem?

I tried a joystick and gamepad and both reported the same type of error...

[INDENT]Failed to attach the USB device Logitech Attack 3 [0205] to the virtual machine Windows_XP.
Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {0a51994b-cbc6-4686-94eb-d4e4023280e2}
[/INDENT]The device status for the Attack 3 is reported by Virtualbox as ...[INDENT]Vendor ID: 046D
Product ID: C214
Revision: 0205
State: Held
[/INDENT]

---

### Post by transmition on 2009-07-06
Perhaps you have not installed drivers for the joysticks? I know that USB keys automatically install drivers when they are plugged in, perhaps the joysticks do not have this functionality and require a CD or something?

---

### Post by kurio99 on 2009-07-07
The joystick and gamepad works fine in Ubuntu with Wine and Linux native games.  No other drivers should be required there.

I installed the drivers to the guest Windows XP, though this error message appears to be from VirtualBox rather than the Guest operating system.

---

### Post by Murz on 2009-12-23
Maybe same problem described in bug [http://www.virtualbox.org/ticket/5175](http://www.virtualbox.org/ticket/5175)

---

### Post by Chrisco66 on 2009-12-23
I have the same problem.  When I run lsusb in terminal, it properly identifies my joystick and other usb hardware.  When I plug it in under Virtualbox, under xp pro, it does not show up in hardware manager.  There do not appear to be any faults in the usb controllers either (under windows).  I tried going through control panel to add it, no help.  If I go to vbox settings, usb, and add a filter, it also properly identifies the joystick.  I checked my group settings and my user name is listed under vboxusers.  I have not tried the other hardware because I dont need it to work under windows.  I only plan to use the guest for playing games.  With Virtualbox running xp, if I click on the usb icon on the bottom, it shows all the hardware attached to the host.  The problem is that they are all greyed out.  Same result if I use the menu at the top.  This may be off the subject a bit but, how do you see a list of hardware under 9.10?  I switched back from opensuse a few weeks ago.  Opensuse had a way of seeing hardware that I cant find in Ubuntu.  I would be curious to see if Gnome has anything to do with this problem.  If lsusb saw the hardware, shouldnt gnome see it too?  Could this be an ownership problem?  How can I tell if I "own" the joystick?  Im taking a break, my head hurts..

---

### Post by firesock on 2010-04-26
> **Chrisco66 said:**
> I have the same problem.  When I run lsusb in terminal, it properly identifies my joystick and other usb hardware.  When I plug it in under Virtualbox, under xp pro, it does not show up in hardware manager.  There do not appear to be any faults in the usb controllers either (under windows).  I tried going through control panel to add it, no help.  If I go to vbox settings, usb, and add a filter, it also properly identifies the joystick.  I checked my group settings and my user name is listed under vboxusers.  I have not tried the other hardware because I dont need it to work under windows.  I only plan to use the guest for playing games.  With Virtualbox running xp, if I click on the usb icon on the bottom, it shows all the hardware attached to the host.  The problem is that they are all greyed out.  Same result if I use the menu at the top.  This may be off the subject a bit but, how do you see a list of hardware under 9.10?  I switched back from opensuse a few weeks ago.  Opensuse had a way of seeing hardware that I cant find in Ubuntu.  I would be curious to see if Gnome has anything to do with this problem.  If lsusb saw the hardware, shouldnt gnome see it too?  Could this be an ownership problem?  How can I tell if I "own" the joystick?  Im taking a break, my head hurts..

Hi!! the same problem here with the same environment (ubuntu host, win xp VM,). The usb joystick appears gray on the VM, so I can't select this device.

Any idea?

---

### Post by seventeener on 2012-05-03
I had a similar problem. In my case the USB device is a TI eZ430 debug interface. The problem was fixed after I loaded the usbserial kernel module (see instructions [here]("http://forums.reprap.org/read.php?12,4546") or [here]("http://wiki.debian.org/usbserial")):
```
sudo modprobe usbserial vendor=0x0451 product=0xf432
```
Of course this will be different for other USB devices. But the general idea is that you can try loading a proper device driver in Debian/Ubuntu. It might solve the problem with VirtualBox.

---

