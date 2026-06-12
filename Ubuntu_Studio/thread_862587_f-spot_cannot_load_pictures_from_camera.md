---
title: "f-spot cannot load pictures from camera"
date: 2008-07-17
forum: Ubuntu Studio
---

### Post by cpetercarter on 2008-07-17
I have a Panasonic DMC-F27 camera. When I plug it in to my computer:

1 a screen icon ("2.1GB media") appears. I can click on the icon and view the contents on Nautilus. I can also view the contents in gThumb image viewer.

2 f-spot opens, and I get a box saying that a camera has been detected. F-spot asks me to identify which camera to import from (odd, I only have 1 camera) - the choices are a) Mass storage camera: /media/disk and b) Panasonic DMC LC1 usb:

3 When I click on either of these, there is a pause, f-spot greys out, and eventually a message appears saying "Error connecting to camera. Received error "unspecified error" while connecting to camera"

4 I click on OK to acknowledge the message. The screen icon for the camera disappears, so clearly f-spot's discovery of the error has led to the camera being dismounted. I can remount the camera by switching it off and then on again.

Any suggestions as to what I should do to get f-spot to import from the camera?

PS. I can also open images in the camera in the GIMP. This is a specific f-spot problem.

---

### Post by cpetercarter on 2008-07-18
I have re-installed f-spot. It imported pictures the first time I plugged in my camera, but reverted to the behaviour described above thereafter. I have now uninstalled f-spot and am using digikam instead. Digikam works fine. There is definitely a bug in f-spot.

---

