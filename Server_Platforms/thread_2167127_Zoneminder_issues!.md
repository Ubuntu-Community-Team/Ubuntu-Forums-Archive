---
title: "Zoneminder issues!"
date: 2013-08-12
forum: Server Platforms
---

### Post by apatheticrory on 2013-08-12
Hi,

i am trying to set up a simple webcam monitoring system. i have 12.04 set up as a headless server, i have installed Zoneminder and plugged in the usb cam, i get this.....

1719.061254 uvcvideo: failed to set uvc probe controll: -32 (exp. 26).

can someone help? i have to be honest - i'm not the most experienced with ubuntu server. 

i have tried dmesg and i get UFW block and failed to set uvc commit control with resume error 5?! 

would massively appreciate any help....

thanks, guys

---

### Post by tgalati4 on 2013-08-12
Find another linux computer (preferably with a desktop OS installed) and plug the camera in and see if it works with any of the video utilities:  cheese, xawtv, qcam.  You need to make sure the camera works with standard linux drivers.  Once you have established this, then you can troubleshoot zoneminder.  Make sure you are running the uvc modules:

```
lsmod | grep video
```

tgalati4@Mint14-Extensa ~ $ lsmod | grep video
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
video                  19391  2 i915,acer_wmi

---

