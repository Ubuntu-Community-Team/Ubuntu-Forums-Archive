---
title: "Cannot access host USB, ubuntu 11.04, vbox 4.1"
date: 2011-08-19
forum: Virtualisation
---

### Post by kmeisthax on 2011-08-19
After adding myself to vboxusers, installing the extension pack, updating to Vbox 4.1, and rebooting, I get this error when trying to open settings:

Failed to access the USB subsystem.

Could not load the Host USB Proxy service: VERR_DISK_FULL

Additionally, there are no USB devices available. Despite the misleading error, this is not a disk space issue; running Vbox as root gives me access to all of the USB devices, and gives no error message. So how do I make it so that vboxusers members can access the USB stuff?

Also, here are my 10-vboxdrv.rules:

KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="root", MODE="0600"
SUBSYSTEM=="usb_device", ACTION=="add", RUN+="/usr/share/virtualbox/VBoxCreateUSBNode.sh $major $minor $attr{bDeviceClass}"
SUBSYSTEM=="usb", ACTION=="add", ENV{DEVTYPE}=="usb_device", RUN+="/usr/share/virtualbox/VBoxCreateUSBNode.sh $major $minor $attr{bDeviceClass}"
SUBSYSTEM=="usb_device", ACTION=="remove", RUN+="/usr/share/virtualbox/VBoxCreateUSBNode.sh --remove $major $minor"
SUBSYSTEM=="usb", ACTION=="remove", ENV{DEVTYPE}=="usb_device", RUN+="/usr/share/virtualbox/VBoxCreateUSBNode.sh --remove $major $minor"

---

### Post by dino99 on 2011-08-21
install the Extension Pack:

[http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack)

---

