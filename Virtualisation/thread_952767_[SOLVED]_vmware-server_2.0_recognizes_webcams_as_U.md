---
title: "[SOLVED] vmware-server 2.0 recognizes webcams as USB audio only"
date: 2008-10-19
forum: Virtualisation
---

### Post by scotty64 on 2008-10-19
When I connect a USB webcam (Logitech Quickcam or Philips SPC900) to my computer VMWare server only presents them as audio devices to the virtual machines. They show up as "Philips Audio Device", or "Logitech Audio Device", but no camera or video device. Only the "Laptop integrated Webcam" shows up. I have no other application using the cameras.

---

### Post by scotty64 on 2008-10-23
The problem was caused by the user not having sufficient permissions to usbfs. Here is how to solve it:

1. Create a group, e.g. vmware

2. Make your user a member of this group and login again to update your credentials.

3. Modify the USB devices section in /etc/udev/rules.d/40-basic-permissions.rules as here:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vmware"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vmware"

4. Restart udev with sudo /etc/init.d/udev restart

The cameras are still listed as "xx Audio Device", but they will be recognized as the proper devices withing the Guest OS.

---

