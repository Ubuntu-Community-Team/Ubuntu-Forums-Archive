---
title: "Embedded camera support on serval performance?"
date: 2008-10-29
forum: System76 Support
---

### Post by andrewdied on 2008-10-29
Are the embedded camera and mics supported on the serval performace laptop (serp4)?  I'm on 8.04 ubuntu / xubuntu, and running the 2.2.6 system 76 driver.  I haven't tried any particular software with it before, so I'm not sure it works.  About as far as I've gotten is trying camorama, and it says it can't connect to /dev/video0.

---

### Post by steveneddy on 2008-10-29
I have a Serval Performance Type 1 and this was a link given by Thomas Aaron about the Microdia cams in early Servals.

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft](https://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

Still works great!

Basically after compiling, these simple steps should get you going.

> $ sudo modprobe videodev
 $ sudo modprobe compat-ioctl32
 then
 $ sudo insmod microdia.ko


---

### Post by thomasaaron on 2008-10-30
Hi andrewdied,

With the SerP4, the cam works fine. The internal mic works too, but it doesn't produce as good of a recording quality as an external mic.

Camorama won't work. It only works with V4L devices. The cam on the SerP4 is a V4L2 device.

Download cheese...

sudo apt-get install cheese

It will appear at System > Sound and Graphics > Cheese.

Best,
Tom

---

