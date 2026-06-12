---
title: "WebcamStudio for GNU/Linux 0.15 is out!  Wanna look funny?"
date: 2008-09-27
forum: The Cafe
---

### Post by patrickballeux on 2008-09-27
Hi people,

WebcamStudio for GNU/Linux 0.15 is now available on sourceforge.net

[http://webcamstudio.wiki.sourceforge.net/](http://webcamstudio.wiki.sourceforge.net/)


This software will let you create a virtual webcam like ManyCam does for Windows users. There is a bunch of features and it is compatible with Flash site (using Flash 10)

I need more testers to validate the stability and make sure that is works well.

You do not need any webcam as you can simply broadcast your desktop, images or movies as a virtual webcam.

For those who have a webcam, try the new feature **Face**!  Now you can look like a viking, a spaceman, a gorilla using simple PNG files package in a Face file.  See the wiki for details...

The project tries to give a fun and easy solution for the non-geek user to be able to broadcast in their own style.


Read the wiki for installation, you'll need the vloopback module from the Flashcam project to broadcast in a virtual webcam. But without you can at least see the results in the preview display.

Thank you for your help!

---

### Post by blithen on 2008-09-27
I'm not really sure what it does but I will try it out once I get home.

---

### Post by binbash on 2008-09-28
works great thanks

---

### Post by patrickballeux on 2008-09-30
New Animations and new Faces have been added to the wiki pages of the project...

Documentation was updated also.


Have fun!

---

### Post by nolageek on 2008-12-29
I'm also getting the following error:

```
 java -jar /usr/lib/webcamstudio/WebcamStudio.jar
Error loading device: video1
Error loading device capacity video1
Pointer Size: 4
Error loading device: video2
Error loading device capacity video2

(WebcamStudio:8905): GStreamer-WARNING **: pad v4l2src-213237916:src returned caps which are not a real subset of its template caps


```

Using newest version of Linux Mint as well as loopback and Webcamstudio.

I added all users to video group, chmoded /dev/video* to 666 and 777 and still cant get it to run.

---

### Post by EnGorDiaz on 2008-12-30
i think this should be default with every ubuntu install this is great

---

### Post by OffHand on 2008-12-30
Works on a Dell XPS M1530 laptop with integrated webcam. Nice piece of software!

---

### Post by patrickballeux on 2009-01-11
> **nolageek said:**
> I'm also getting the following error:

```
 java -jar /usr/lib/webcamstudio/WebcamStudio.jar
Error loading device: video1
Error loading device capacity video1
Pointer Size: 4
Error loading device: video2
Error loading device capacity video2

(WebcamStudio:8905): GStreamer-WARNING **: pad v4l2src-213237916:src returned caps which are not a real subset of its template caps


```

Using newest version of Linux Mint as well as loopback and Webcamstudio.

I added all users to video group, chmoded /dev/video* to 666 and 777 and still cant get it to run.

Hi,

What is not working?  Your webcam of the vloopback device?  It seems as your V4L2 webcam is not properly configured.  Try different capture size, framerate, color format (RGB instead of YUV).


Let me know!
PS: You should post in the main thread for WebcamStudio: [http://ubuntuforums.org/showthread.php?t=943774](http://ubuntuforums.org/showthread.php?t=943774)

---

### Post by OffHand on 2009-01-11
0.39 crashes X/computer. o.38a worked fine. any ideas?

---

### Post by ctsdownloads on 2010-01-26
> **OffHand said:**
> 0.39 crashes X/computer. o.38a worked fine. any ideas?

Run it in a terminal, then paste the contents here so we can see what is happening. Crashing could mean a lot of things: Java crash, X, etc.

---

### Post by RabbitWho on 2010-01-26
Dell Inspiron 1545, works well with integrated web cam. I am particularly impressed by the night vision... If I ever need to make a video of myself during a power cut i'm all set now! but how do I make the face less hidieous?

---

### Post by juancarlospaco on 2010-01-26
***Why you dont fill a "Need-Packaging Bug" to get it included on next Ubuntu release repo's ???***

---

### Post by Elfy on 2010-01-26
Closed - year old - and webcam is at 0.53 now

---

