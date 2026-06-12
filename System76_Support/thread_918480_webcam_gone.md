---
title: "webcam gone"
date: 2008-09-13
forum: System76 Support
---

### Post by eyecreate on 2008-09-13
I tried to follow this tutorial to get a new video capture device working, but it didn't work, even worse, it also made the serp4 webcam I have stop working too. How would I go about putting it all back to where it was?( the old v4l setup)

[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/em28xx_generique&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Deasycap%2Bubuntu%26hl%3Den%26sa%3DG%26pwst%3D1](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/em28xx_generique&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Deasycap%2Bubuntu%26hl%3Den%26sa%3DG%26pwst%3D1)

EDIT:I already tried reinstalling the system76 driver.

EDIT2:I tried reinstalling the driver without any changes..aka..direct from source. No good either.

EDIT3:I tried reinstalling my kernel from synaptic, tried restore from system76 driver. None have fixed it. I also want to note that it seems, A, that the webcam onboard uses the same driver I was patching, B, /dev/video0 does not exist anymore. I think there is a problem now with the webcam not being detected as a usable item. It shows up in lsusb just fine though.
Bus 003 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 2M UVC Webcam

EDIT4: okay, the web camera came back once i reinstalled the ubuntu modules, but I can't get my other video capture device to load.(the one i followed the tutorial for)

---

### Post by darkknight045 on 2008-09-14
Okay, I've been waiting for a fix to hopefully come down, but I think I may be one of the few that still has this problem.

My webcam is malfunctioning badly in Cheese.  I've tested it with Ekiga and Skype and the webcam is working just fine there.  What do I need to do to get a program like Cheese to work with me?

Right now the webcam is zoomed in quite a bit and its refresh rate is unbelievably slow coupled with poor lighting management.

Help?

---

### Post by thomasaaron on 2008-09-15
eyecreate,

Glad you got your webcam working again. However, we do not have a video-capture device to test with, so we need to shoot for some community support on this one. System76ers? Anybody using a video-capture device?

darkknight045,

That is just cheese in Hardy Heron. It definitely is not as slick as it was in Gutsy. I'd report it here...
[https://launchpad.net/cheese](https://launchpad.net/cheese)

---

