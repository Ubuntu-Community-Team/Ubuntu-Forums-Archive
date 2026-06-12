---
title: "Permissions for USB device from 'libusb' (Netbeans-C++)"
date: 2014-03-28
forum: Ubuntu Application Development
---

### Post by raffaele2 on 2014-03-28
Hi everybody,

I'm writing a C/C++ application in NetBeans based on libusb-1.0. 
I can get basic information form the USB device (like interface descritption...) bue I am not able to open the deivce. 
The function libusb_open gives me the error:
libusb:error [op_open] libusb couldn't open USB device /dev/bus/usb/002/003: Permission denied.
libusb:error [op_open] libusb requires write access to USB device nodes.


I understand that I need to change the permission  but I don't know how (I am very basic user). Thank you

R

---

### Post by squakie on 2014-03-29
What iis the USB device?  lsusb would help us.  Also, you may want to read up on using udev rules for "non-standard" USB devices.  I haven't done any of this in about 2 to 3 years now, and I also just used C not C++.

---

### Post by squakie on 2014-03-31
I don't know if you've looked at the udev rules information yet or not.  Usually in these cases the USB device is getting mounted with root-only write access.  To change that, you need to change the permissions each time the device is mounted.  You do that via a udev rule.  This is also why we need the output of lsusb while the device is plugged in, as we need the manufacturer id/product number - the 4 digit code followed by : followed by the next 4 digit code.  The first is the manufacturer id, the second, after the :, is the product id.

You can test this theory by simply running your app as root.

---

### Post by MonsterPipe on 2014-04-11
Hi [COLOR=#000000]raffaele2,

For something robust, Udev rule is your best really your best shot.

Example of UDEV rule:
```
[/COLOR]SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTR{idVendor}=="YOUR VENDOR ID", ATTR{manufacturer}=="Bla bla", MODE:="666"[COLOR=#000000]
```

But if you need to do a quick test, just type lsusb, see where is your device from the output; /dev/bus/usb/xxx/xxx and do a sudo chmod 777 on it. It will allows libusb to communicate with the device.[/COLOR]

---

