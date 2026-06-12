---
title: "capture image from webcam with jmf"
date: 2009-06-10
forum: Ubuntu Dev Link Forum
---

### Post by dvsnow on 2009-06-10
Hi, everybody
please help me,
I have a program that capture image from webcam using jmf.
my problem is : i can't display image from webcam, see the attach file
Can you tell me how to resolve this problem.
Thanks a lot.

---

### Post by hellocatfood on 2009-06-10
What program are you using?

Have you tried Cheese?
```
sudo apt-get install cheese
```

---

### Post by dvsnow on 2009-06-10
thanks for your reply.
I write a program follow the link :
[http://forums.sun.com/thread.jspa?threadID=247253&forumID=28](http://forums.sun.com/thread.jspa?threadID=247253&forumID=28)
cheese run ok with my webcam.

---

### Post by hellocatfood on 2009-06-10
I'm glad cheese works for you! I'm afraid I can't help wit hteh coding though. Why not start a new sourceforge project and look on other design/coding forums

---

### Post by Karthick.Mohanraj on 2009-08-08
Me too got the exact problem.
I tried in JMSTUDIO, It also shows the grids and lines when I try to capture.
But my web cam is working fine with cheese.

I doubt the video capturing format in JMSTUDIO,
I am getting RGB and YUV as options.

Is there some thing to do with the bit rate and frame rate??

can any one help on this please???

---

### Post by skullmunky on 2009-08-10
Take a look at these Processing libraries:

[http://www.processing.org/reference/libraries/](http://www.processing.org/reference/libraries/)

Look at:

GSVideo - a Java wrapper for GStreamer. 

jmcvideo - JMC is a newer Java media framework, part of something called JavaFX, which supposedly doesn't suck as bad as JMF.  

OpenCV - a java wrapper for the OpenCV computer vision library

---

### Post by Karthick.Mohanraj on 2009-08-10
Thankyou skullmunky...

---

