---
title: "Webcam with VB"
date: 2008-08-24
forum: Virtualisation
---

### Post by FLCL on 2008-08-24
I have installed the drivers, and software for the camera, but the only problem is it is not working. It's plugged into the USB, but it will not work for some reason. USB is enabled for it, as previously when it wasn't i couldnt even install the software because it couldnt detect any working USB ports. 
As well, my usb mouse works just fine. 
Can anyone help me out with this please?:(

---

### Post by Crafty Kisses on 2008-08-24
Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If that doesn't work post results of > lsusb

---

