---
title: "Lost my webcam with update Kernel  3.8.0-34-generic"
date: 2013-12-27
forum: System76 Support
---

### Post by Sigologo on 2013-12-27
Hello Everyone........
 Today update kernel to 3.8.0-34-generic on  my gazp8 (Ubuntu 12.04.3LTS), almost wonderfoul....
but my webcam is not recognized by hardware or software any idea?????


Thanks in Advanced

---

### Post by KlipperKyle on 2013-12-31
> **Sigologo said:**
> my webcam is not recognized by hardware or software any idea?????

Gazelle Pro 8 owner here. I know exactly what you are talking about.

The gazp8 has a secret camera switch on the keyboard. Hold <Fn> (between left <Ctrl> and <Ubuntu> keys) and press F10. (There is a blue outline of a camera on F10.) This key combination turns the webcam on and off.

The easiest way I have of telling whether the camera is on is to run "ls /dev/video*" in a terminal. An alternative is to check the output of lsusb.

Off:

```
kyle@wopr ~ $ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
kyle@wopr ~ :( $ 

```

On:

```
kyle@wopr ~ $ ls /dev/video*
/dev/video0
kyle@wopr ~ $ 

```

As far as I can tell, the <Fn> + F10 switch works like physically plugging/unplugging the camera (Someone please correct me here). If this is the case, it is a pretty good mechanism to keep prying eyes off of your webcam (**cough** NSA **cough**).

---

### Post by Sigologo on 2013-12-31
thanks a lot Klipperkyle....
Happy New Year 2014

---

