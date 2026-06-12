---
title: "webcam no longer working"
date: 2009-04-06
forum: System76 Support
---

### Post by Brian_Newbie on 2009-04-06
I have a panp4n 64 bit intrepid laptop and before I downloaded cheese my webcam was working. My aMSN and Gyache improved (for yahoo instant messenging) both recognized the built in webcam. 

After I downloaded Cheese through synaptic package manager both aMSN and GYachE improved no longer detect a working webcam. These IM clients show my webcam not as the internal cam but as "v4l2 usb2.0 camera 1." 

I downloaded the system76 driver but my cam is still detected as a usb2.0 cam and with no video. 

When I ran the gstreamer command I got the following output.

brian@ubuntu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
brian@ubuntu:~$ 

Clicking on the video tab I noticed it's set to "v4l" under "default input" and "autodetect" under "default output" and I get only the coloured bars and no video of myself.

How do I get the webcam working again for aMSN, GYachE and if possible, Cheese?  

Could this be why

---

### Post by Guille Damke on 2009-04-06
Hi Brian,
I also have a panp4n and my webcam is not working. I would like to know if it is working under Ekiga: When I try to adjust webcam brightness/contrast, Ekiga's window turns completely to grey and stops working until I disable the camera by pressing Fn+F10. Does it happen in yours?
Is your webcam listed if you type "lsusb" in a terminal? (Mine is listed as "Bus 008 Device 005: ID 0402:5606 ALi Corp.") and it is activated/deactivated with Fn+F10. 
I would appreciate if you answer these questions.

---

### Post by Brian_Newbie on 2009-04-06
I have not yet set up Ekiga. Will do so soon. I noticed something different from when my webcam was working. When I type the lsusb command I get the following output:

brian@ubuntu:~$ lsusb
Bus 008 Device 002: ID 0402:5606 ALi Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brian@ubuntu:~$ 

When my camera is off the first line that includes the "ALi Corp. is not there.

However, I remember when my cam was working the first line did not read "ALi Corp" but rather "Acer...." and my webcam then showed up as a Bison cam not a v4l2 usb2.0 cam.

Maybe this has something to do with it. It seems like my system and aMSN, GyachE and Cheese are detecting the wrong cam or something?

---

### Post by thomasaaron on 2009-04-06
Try running this command from a terminal...

echo options uvcvideo quirks=2 | sudo tee -a /etc/modprobe.d/uvc 

See if that fixes it... and don't forget Fn-F10 to toggle the cam on.

---

### Post by Brian_Newbie on 2009-04-06
Hi Thomas

I ran that command and it did not fix it. I played around with gstreamer-properties settings and none of them seem to work.

I'm not sure how it went from recognizing the bison webcam to detecting a usb2.0 cam.

I'll reply later as I'm off to work. If you have any other suggestions just post them here and I'll try them later on.

Thanks for your assistance

Brian

---

### Post by thomasaaron on 2009-04-06
OK, first go to...
/etc/modprobe.d/uvc

...and delete the line created by the command...
options uvcvideo quirks=2

I'm not exactly sure why it is detecting the cam differently, but I doubt that is the problem. It is a v4l2 webcam and should work with v4l2 applications.

Make sure you're not running two applications that need the camera at the same time. If there is an icon for them in the upper panel, then close it via that icon. You may have some software conflicting.

---

### Post by indoo on 2009-05-20
*bump*

I have the exact same problem. Was there ever any solution found?

---

### Post by flukeairwalker on 2009-05-21
My solution? I bought an external webcam. Logitech and Creative webcams use the UVC driver, which is standard for Linux. Try it out when everything else fails. I spent a month trying to fix it before ThomasAaron told me it might be a hardware problem. Rather than lose my computer for some time by sending it back for a fix, I just bought a new webcam. It works great now!

---

### Post by thomasaaron on 2009-05-21
indoo,

If you have a System76 machine and still need help with this, contact me at support(at)system76(dot)com. I can't tell when you posted.

---

