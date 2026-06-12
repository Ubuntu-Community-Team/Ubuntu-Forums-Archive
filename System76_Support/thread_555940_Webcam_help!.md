---
title: "Webcam help!"
date: 2007-09-20
forum: System76 Support
---

### Post by bmannering on 2007-09-20
Hello  I have just received my daru2 and am very happy with it. But I cannot seem to get the webcam working. Supposely it works in cheese and ekiga from what i have read but I cant get it recognized. Any help or a point to a guide will be very much appreciated. Thanks

---

### Post by thomasaaron on 2007-09-21
1. Go to Applications > Internet > Ekiga
2. Go to Edit > Preferences > Devices > Video Devices
3. If the Input Device drop-down menu does not say: USB 2.0 Camera, 
close Ekiga, press the P2 button above the keyboard and restart Ekiga, 
repeating 1 & 2 above.
4. Set the Video Plugin drop-down menu to V4L2
5. Click the Close button.
6. Click the camera icon on the left side of the Ekiga GUI to start the 
camera.
7. Smile
8. Go to Call > Save current picture to take a snapshot.
9. Go to your home directory to find the picture.

---

### Post by bmannering on 2007-09-21
Wow. Thanks a ton it works great now. Not that I need it but the cheese program seems to some what find my webcam but it escapes within 5 or 6 sec after opening the program. I am not to sure what to do.

---

### Post by thomasaaron on 2007-09-21
I've never used it.
I'll try to compile it and write a tutorial on it next week.

Best,
Tom

---

### Post by bmannering on 2007-09-21
thank you very much

---

### Post by bmannering on 2007-09-21
Well once again I always forget about compiz so i got cheese working.
Default output plugin to X window system (x11/Xshm/Xv)
Device Intel(R) Textured Video
Default Input
Plugin Video for Linux 2 (v4l2)
Device USB 2.0 Camera
and make sure your compiz fusion is off.

---

