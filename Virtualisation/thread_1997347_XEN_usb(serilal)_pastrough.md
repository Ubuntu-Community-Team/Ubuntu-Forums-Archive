---
title: "XEN usb(serilal) pastrough"
date: 2012-06-05
forum: Virtualisation
---

### Post by elempe on 2012-06-05
Hello,

I have Ubunutu 11.10 with XEN installed, and several guest systems, but now I faced one problem, recently I had to connect two USB to serial adapters to this server, but I need one guest system (12.04) to access both adapters.
Devices:
Cygnal Integrated Products, Inc. CP210x Composite Device
Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

I have tried USBIP solution for unknown reason for one of adapters it complains on guest side about bad cable and looses /dev/ttyUSBx, I can't figure out what is the deal. (CP210x complains)
Message:
kernel: [35097.110097] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad? 
It worked before on physical host which unfortunately died.

So now my next bet is to pastrough serial port from host to  guest but I can't figure out is it even possible. 

Question - isit possible to pastrough serial port? 
For example: Dom0 has /dev/ttyUSB0 and I'd like to map it to DomU /dev/whatever

Maybe there aro other possibilities how to deal with my issue, because I have no preferable way, I only need to get it done.
 
Cheers!

---

### Post by levk on 2012-06-05
USB passthrough wasn't their finest code last time I tried it, most people who actually want USB passthrough do PCI passthrough of the controller.

However before you go there I suggest to make sure your USB dongle works.

---

### Post by elempe on 2012-06-06
Thanks for your answer.

About PCI pastrough it is possibility, but currently I see one major problem - can't find required modules even in Precise Pangolin newest kernel. 
I have to recompile kernel - it is possible and not so hard to do, but the problem is - in that way I loose possibility to follow Ubuntu updates.

---

