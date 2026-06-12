---
title: "System76 laptop (serp7) webcam problem with kernel update"
date: 2014-08-04
forum: System76 Support
---

### Post by gregory-holst on 2014-08-04
The webcam on my System76 laptop (serp7) worked fine with Ubuntu 12.04 but after upgrading to 13.10 and later to 14.04, the webcam has stopped working.  I don't even have a /dev/video0 directory.  If I use a USB webcam, it works fine.  I've attached my dmesg, lsusb, and lsmod outputs.  I know it worked before and it's not because I didn't press Fn+F10.  Nothing in the output of dmesg, lsusb, or lsmod changes after pressing Fn+F10.  Was support for this webcam depricated in the kernel update?  How would I find out what chipset my camera is if it's not showing up in any of the outputs?

Thanks.

---

### Post by MoebusNet on 2014-08-05
My SerP7 running 12.04.4 has the same issue. I haven't noticed until now because I rarely use my webcam. Cheese doesn't activate my webcam, but using ```
 gstreamer-properties 
``` , selecting video tab and cicking the "Test" button activates the webcam.

I wonder what's going on? The webcam formerly worked fine!

UPDATE: After trying out some older kernels which complained about missing GLX, Cheese is now working for me with the current kernel in 12.04.4. I don't know what cause it to stop or start working again...

---

### Post by MoebusNet on 2014-08-05
If it will help, I've booted my serp7 from Ubuntu 14.04.1 Live-USB. Cheese is working and the webcam is working. You may want to try booting from Live-media just to make sure this isn't a hardware problem. Hope this helps!

---

### Post by gregory-holst on 2014-08-05
Thanks for the help!  When I try

```
gstreamer-properties
```

with the "video for linux (v4l2)" or the "custom" inputs, it replies with: 

> Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

and

> Custom: Cannot identify device '/dev/video0'.

so I think it's a more fundamental driver or hardware problem since it's not even recognizing the device in any of the logs (lsusb, dmesg) even though I toggle Fn+F10 and recheck them.  I'll post again after I've tested the live image (it's downloading now).

---

### Post by isantop on 2014-08-06
Try this procedure to ensure that the webcam is turned on:

Close any applications that can use the webcam, including Skype (if applicable) or browsers. Open Cheese, or a similar Webcam booth application, and see if you get video. If not, close it, press Fn+F10, then open Cheese again and see if it now works.

---

### Post by gregory-holst on 2014-08-08
Well, the live boot image to 12.04 didn't work either.  I guess it was a hardware problem.  Thanks for all you're help!  (and I tried cheese before and after pressing Fn+F10 and it made no difference.  /dev/video0 was still missing and nothing showed up with lsusb)

---

