---
title: "driver development: usbhid is blocking custom device driver"
date: 2010-12-14
forum: Ubuntu Dev Link Forum
---

### Post by beetleskin on 2010-12-14
Hej!

I'm developing a custom usb device driver (Stereovision HMD). Unfortunately the Linux usbhid driver (resp. the correlating kernel module) kind of catches the device as soon as it is connected to dhe usb host controller. Thus my own driver (identifying via vendorID and productID) is blocked. I searched the internet for a way to prevent usbhid from catching the device and found a couple of solutions, but nothing worked so far, as I just didn't find the files proposed by that solutions (blacklisting vendorid and productid in some files, e.g. usbhid.conf...). I can't figure out a up-to-date solution.

I'm running Ubuntu, 2.6.32-25 Kernel.

I just can't imagine why the standard Linux driver for HID (usbhid) is associated to that device when there is a driver loaded (my driver kernel module), which provides the correct IDs!? Anyway, is there a solution for that problem? A kind of priority list? Can I override/overload usbhid? Or do I have to use blacklists? Best solution would be within my driver code, as I want to port my driver to other systems whithout hacking some kernel properties everytime...

every hint would be appreciated!

best regards

ps: my nasty workaround is a shell script that unloads the usbhid module, waits 20 seconds for me to plug the usb device and reloads the usbhid module. works. kind of :D

---

