---
title: "Using gstreamer in Ubuntu (Windows 10 bash)"
date: 2017-01-22
forum: Windows
---

### Post by dhlee20 on 2017-01-22
I'm trying to stream a video from the Pi Camera attached on my Raspberry Pi 3 (Raspbian, not Ubuntu mate) and view from my Windows laptop by using the 'Bash on Ubuntu' function in the Windows Anniversary update.

I installed gstreamer 1.0 and other plugins in both devices, and those programs were installed to both devices just fine!

```

apt-get install gstreamer1.0
apt-get install gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-plugins-base gstreamer1.0-plugins-bad gstreamer1.0-plugins-good

```

And I followed this tutorial to enter the streaming script to the Raspberry Pi and the receiving script to my laptop.

[http://blog.tkjelectronics.dk/2013/06/how-to-stream-video-and-audio-from-a-raspberry-pi-with-no-latency/](http://blog.tkjelectronics.dk/2013/06/how-to-stream-video-and-audio-from-a-raspberry-pi-with-no-latency/)

So, I entered these codes:

```

raspivid -t999999-w1080-h720-fps25-hf-b2000000-o - | \
gst-launch-1.0-v fdsrc ! h264parse ! rtph264pay config-interval=1pt=96 \
! gdppay ! tcpserversink host=serverIp port=5000

```
Streaming script - Raspberry Pi
```

gst-launch-1.0-v tcpclientsrc host=serverIp port=5000 \
! gdpdepay ! rtph264depay ! avdec_h264 ! videoconvert ! autovideosink sync=false

```
Receiving script - my laptop

And now I'm facing this error...

```

root@FELIXPC:~# gst-launch-1.0 -v tcpclientsrc host=192.168.0.12 port=5000 \
> ! gdpdepay ! rtph264depay ! avdec_h264 ! videoconvert ! autovideosink sync=false
libdc1394 error: Failed to initialize libdc1394
Setting pipeline to PAUSED ...
libEGL warning: DRI2: xcb_connect failed
libEGL warning: DRI2: xcb_connect failed
libEGL warning: GLX: failed to load GLX
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstXvImageSink:autovideosink0-actual-sink-xvimage: Could not initialise Xv output
Additional debug info:
xvimagesink.c(1765): gst_xvimagesink_open (): /GstXvImageSink:autovideosink0-actual-sink-xvimage:
Could not open display (null)
Setting pipeline to NULL ...
Freeing pipeline ...
root@FELIXPC:~#

```

What's the problem and how should I solve it? The tutorial says that I should try in Terminal - Mac. Is the bash function in Windows 10 not working with the Raspberry Pi?
Make sure that I entered the IP address in the 'serverIp' location.

---

### Post by howefield on 2017-01-22
Thread moved to the "*Windows*" forum.

---

