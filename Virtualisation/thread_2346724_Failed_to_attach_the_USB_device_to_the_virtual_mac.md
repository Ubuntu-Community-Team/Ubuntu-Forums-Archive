---
title: "Failed to attach the USB device to the virtual machine"
date: 2016-12-17
forum: Virtualisation
---

### Post by oygle on 2016-12-17
Plugged in a usb on host, then added a setting for that usb in the VirtualBox. Then started the guest (Win 8.1) and got this msg:

> Failed to attach the USB device SanDisk Ultra [0100] to the virtual machine Laptop-VM.

Failed to create a proxy device for the USB device. (Error: VERR_PDM_NO_USB_PORTS).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

The mega thread here on usb is over 7 years old, so have searched and read through various posts on different sites. There seems to be some related bug; not sure if it is relevant in this scenario - [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1515791](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1515791)

There is this post, but didn't want to go modifying that side of things - [https://ubuntuforums.org/showthread.php?t=2339215](https://ubuntuforums.org/showthread.php?t=2339215)

---

### Post by C.S.Cameron on 2016-12-17
I was also having problems with VBox and USB in 16.04.
Had to install Guest Additions and add myself to VBox Users Group.

See [http://askubuntu.com/questions/377778/how-to-add-users-to-vboxusers](http://askubuntu.com/questions/377778/how-to-add-users-to-vboxusers)

---

### Post by oygle on 2016-12-17
Thanks - had already installed guest additions and also have 'vboxusers' as one of my groups.  :(

---

### Post by oygle on 2016-12-17
From [http://superuser.com/questions/461406/windows-virtualbox-failed-to-attach-usb-device-to-linux-guest](http://superuser.com/questions/461406/windows-virtualbox-failed-to-attach-usb-device-to-linux-guest)

> It looks like VBox has some problems with USB3 hubs, and so, plugging my USB key into an USB2 slot did everything.

This laptop has usb2 and usb3 hubs, so I switched hubs, and now no error message.  :)   Win 8.1 is also saying the usb is attached, however I can't see it in the File Explorer.

---

### Post by oygle on 2016-12-17
Seems it is a driver problem ..

[ATTACH=CONFIG]272751[/ATTACH]

---

