---
title: "Serval Performance SER-P3 and camorama error"
date: 2008-01-22
forum: System76 Support
---

### Post by jdmelton on 2008-01-22
I am new to webcams...this is my first.

I am trying to get my webcam working. I have a Serval Performance SER-P3. All updates installed for Ubuntu 7.10.

I installed camorama with the package manager, no errors noted. I have rebooted since the install.

The output of lsusb:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 147e:2016  
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Some of what I see from lsmod:

uvcvideo               48644  0 
ipv6                  273892  26 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
i2c_core               26112  1 nvidia

usbcore               138632  5 hci_usb,uvcvideo,ehci_hcd,uhci_hcd

When I start camorama, I get an error message in a dialog box:

Could not connect to video device (/dev/video0).
Please check connection.

There is a /dev/video0, and the hardware information shows a USB 2.0 Camera on controller 2.

What steps should I take to troubleshoot the device?

---

### Post by thomasaaron on 2008-01-23
I think it is because camorama does not support v4L2.

Try using "Cheese." It is in the repositories.

---

### Post by asmiller-ke6seh on 2008-01-23
> **thomasaaron said:**
> I think it is because camorama does not support v4L2.

Try using "Cheese." It is in the repositories.

Did you notice the line in his listing:

> Bus 006 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd

Who has created a device driver for this device? I haven't been able to find one. If there is one, I would assume that System76 would have made this available to us through the System76 driver.

thomasaaron, have your R&D guys found a driver for this webcam, yet ... it seems to be the same company that makes the webcam in MY Serval.

---

### Post by jdmelton on 2008-01-23
OK. I uninstalled camorama and installed cheese.

The camera came up. I took a picture. :)

So far, so good. The next question is the camera is 2 M pixel, but cheese comes up in 640x480. No manual entry for cheese. How can I change the resolution, or where do I go for more information?

Thanks for the help so far!

---

### Post by thomasaaron on 2008-01-24
The camera is an Integrated 2.0 Megapixel Camera (Chicony CNF6212).
I don't think you can change the resolutin in Cheese.



__________________________

asmiller, they don't have a driver for it yet.

---

### Post by asmiller-ke6seh on 2008-01-24
To answer my own question, after some additional research ...

It seems that the webcam in the Serp3 is a UVC driver-compatible

Now to get back home and lookup the output on lsusb on my Serp2 to see if the bus ID is the same {04f2:b018} - in which case, I may have a solution for the webcam, afterall.

---

