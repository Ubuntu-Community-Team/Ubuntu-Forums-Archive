---
title: "Webcam help"
date: 2008-11-02
forum: Ubuntu Studio
---

### Post by Phreaker on 2008-11-02
Hello!My webcam doesn't seem to work with Ubuntu 8.10
lsusb says :
Bus 007 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam

EDIT: 
It works ,but when i test it with skype it crashes!

---

### Post by fredo31 on 2008-11-02
I have the same problem with a webcam Creative NX pro : this webcam was working perfectly with previous versions of Ubuntu and does not work with the latest 8.10

 lsusb 
Bus 003 Device 002: ID 041e:403a Creative Technology, Ltd WebCam NX Pro 2

---

### Post by Phreaker on 2008-11-02
So it's a skype bug. 
The only thing we can do is hope/wait for skype to fix it

---

### Post by Waklevören on 2009-02-03
Hi. I don't think this is a direct skype bug. I have the same camera, and it works just fine in Cheese, it crashes camorama and skype is able to show my picture, but it's all "wrong": My face is green and my walls are purple! :-k

---

### Post by Crafty Kisses on 2009-02-03
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this: There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work, post the results of this command:
```
lsusb
```

---

### Post by sadnub on 2009-02-10
> **Codename said:**
> Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this: There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work, post the results of this command:
```
lsusb
```
I am also having trouble getting a usb webcam working. The cam is a hue hd webcam and i tested it out in detects the microphone but not the video device. 

Bus 005 Device 002: ID 0c45:6282 Microdia Audio (Microphone)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any help would be greatly appreciated. =)

---

### Post by johnjohn2 on 2009-02-11
Muke,
it cannot be just a problem with Skype as it is also affecting camorama.

Search google for drivers relating to ubuntu for the camera of your choice.

---

### Post by reve99 on 2009-12-18
any body to reply on the question

---

