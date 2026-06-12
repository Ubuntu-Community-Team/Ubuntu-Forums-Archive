---
title: "Webcam trouble on panp5 running 9.04 64bit"
date: 2010-02-07
forum: System76 Support
---

### Post by davideps on 2010-02-07
Hi Folks,

My webcam is turned on (fn F10), but will not work with skype, gstreamer, Ekigo, or web-based tools like tokbox.com    It worked with all these a month ago.

Now, software that tries to access the camera either does nothing or freezes. A while ago I installed a new version of flash from Adobe. Hulu stopped working (and still does not work) but nothing else seemed to be affected. I've installed nothing besides system manager updates since then as far as I can remember. 

Any ideas?

-david

---

### Post by Trublue on 2010-02-07
Had same problems but with 32 bit Reinstalled old version 2.1.0.47 Now works as before [http://adria.fesb.hr/~mbareta/skype/](http://adria.fesb.hr/~mbareta/skype/)

---

### Post by thomasaaron on 2010-02-08
Please try booting from a live Ubuntu CD (9.10 - 64-bit). Once you're booted, run...

sudo apt-get install cheese

(Make sure the cam is on with Fn-F10.)

If the cam doesn't work from the live CD, you most likely have a hardware issue.

---

