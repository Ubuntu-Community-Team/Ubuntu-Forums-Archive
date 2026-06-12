---
title: "logitec quickcam pro for notebooks and 64-bit Ubuntu"
date: 2008-07-23
forum: Ubuntu Studio
---

### Post by dlmoak on 2008-07-23
I am trying get a Logitech quickcam to work with some software for capturing a video, not for use with an instant messaging system.

lsusb shows:
Bus 005 Device 003: ID 046d:0991 Logitech, Inc. 

lsmod shows:
Module                  Size  Used by
uvcvideo               62084  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
snd_usb_audio         100384  1 
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_usb_lib            21120  1 snd_usb_audio

cheese worked once and now shows a black screen.

luvcview worked once and now reports:
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 5.
 Init v4L2 failed !! exit fatal 

xawtv -c /dev/video0  reports the following.
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-19-generic)
xinerama 0: 1680x1050+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYMENU(id=134217738;index=0;name="60 Hz";reserved=1894869472): Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x7fff7ccf10f4 [PAL_G,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_L,?ATSC_8_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
Segmentation fault

Any suggestions?  Is the problem related to me running 64-bit 8.04?

---

### Post by dlmoak on 2008-07-24
I now have video capture with luvcview, but no audio.  Not sure why the video is now working, but would love to have audio as well.

---

### Post by warp99 on 2008-07-24
The uvcvideo module is a little temperamental with certain versions of the the Logictech Quickcam:

[http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities](http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities)

When this occurs close Cheese, open a terminal, and issue the following command:

```
sudo modprobe uvcvideo
```

Cheese should start to work again. On my Kubuntu 64-bit install Cheese uses the high-resolution mode while Luvcview does not. Luvcview does not record audio. 

You could always capture the sound with another program, then merge the video with the audio using mencoder or ffmpeg on the CLI or use one of the GUI frontends for those tools.

---

### Post by dlmoak on 2008-07-24
thanks, I'll check it out when I'm home from work. do you know of a good program to record video and audio simultaneously?

---

