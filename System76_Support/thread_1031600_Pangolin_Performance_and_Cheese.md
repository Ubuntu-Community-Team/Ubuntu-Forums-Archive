---
title: "Pangolin Performance and Cheese"
date: 2009-01-05
forum: System76 Support
---

### Post by kougaru on 2009-01-05
I'm having a problem with the built-in webcam. It seems to work, but only on very small resolutions. If it's set to anything higher then the lowest setting in cheese, all I get is a white screen. Does anyone else have this problem?

It used to work with the higher resolutions in Hardy.

I have a panp4n running Intrepid.

---

### Post by thomasaaron on 2009-01-05
Cheese was broken in Intrepid.

I believe the fix for this ended up being compiling the latest uvcvideo source code.

This should be fixed by an updated System76 driver in the very near future.

Perhaps someone who has done it can provide instructions. In the meantime, if you don't want to compile the code, the camera should still work fine with Ekiga and Skype.

---

### Post by Lee_Machine on 2009-01-05
Follow the instructions on this thread.

[http://ubuntuforums.org/showthread.php?p=6313095](http://ubuntuforums.org/showthread.php?p=6313095)

and then the install instructions are here 

[http://www.soccio.it/michelinux/2008/10/25/webcam-cheese-gstreamer-and-uvcvideo-problems-in-intrepid/en/](http://www.soccio.it/michelinux/2008/10/25/webcam-cheese-gstreamer-and-uvcvideo-problems-in-intrepid/en/)

Also make sure to do this:

go to command line and type sudo gstreamer-properties 

then in the Video tab for plugin make sure V4L2 is selected along with UVC camera in device. About that also make sure for output is X11 and NV17 is selected. Otherwise the output video will be all choppy.

Do the same thing with out running as sudo to make sure they both match each other.

gstreamer-properties is also where you would select the system wide sound.

---

