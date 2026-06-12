---
title: "no bluetooth on PAN-P4/Ubuntu 8.10"
date: 2009-04-01
forum: System76 Support
---

### Post by sds57 on 2009-04-01
bluetooth is not working.

Pangolin Performance (PAN-P4).
Ubuntu 8.10
system76-driver 2.3.0
# service bluetooth status
 * bluetooth is running.
# hcitool scan
Device is not available: No such device
# hcitool dev
Devices:

so, it appears that the kernel does not see the bluetooth device.
am I doing something wrong?

thanks!

---

### Post by Lee_Machine on 2009-04-02
The tool you are using looks for active devices. Once connected to a bluetooth device the devices MAC address will be shown when hcitool dev is ran. 

Along with which one its is. If it's the first once hci0 will be the device location.

On the pangoline press Fn-F12 and that will turn bluetooth on. Then the bluetooth icon will appear on the top panel. Right click on it and choose add new device. 

The bluetooth applet will lead you through the rest.

---

