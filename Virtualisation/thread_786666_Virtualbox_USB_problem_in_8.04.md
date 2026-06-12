---
title: "Virtualbox USB problem in 8.04"
date: 2008-05-08
forum: Virtualisation
---

### Post by aks2008 on 2008-05-08
Error message I get on attaching my USB bluetooth dongle is

"Not permitted to open the USB device, check usbfs options."

I am using ubuntu hardy host and windows XP guest and virtual box version 1.5.6-28266

40-permissions.rules file seems to different in hardy
It reads

# USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
MODE="0660", GROUP="dialout"
LABEL="usb_serial_end"

Any advice what should I do?

---

### Post by OldTimeTech on 2008-05-08
Check out this thread:USB problem with VirtualBox...it has your answer ;)

---

