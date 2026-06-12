---
title: "Webcam Help Please :)"
date: 2009-03-09
forum: Ubuntu Studio
---

### Post by Irunongames on 2009-03-09
I put my webcams usb in the usb port and then I open cheese and it doesn't show it. What should I do?

---

### Post by kayosiii on 2009-03-11
What model of webcam

---

### Post by Crafty Kisses on 2009-03-11
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the following command:
```
lsusb
```

---

