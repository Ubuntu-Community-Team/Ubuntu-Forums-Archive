---
title: "Webcam App"
date: 2008-08-08
forum: The Cafe
---

### Post by esaym on 2008-08-08
I am looking for an app that will take an image from my built in laptop webcam and copy it to the hard drive every 5 minutes.  Does such a thing exist?  I want to write a program that will then take that image on my hard drive and upload it to my web page.

---

### Post by fiddledd on 2008-08-08
You might want to look at [this](http://www.zoneminder.com/), it will save you programming anything.

---

### Post by esaym on 2008-08-08
Ah, well zoneminder is for security and cctv cameras right?  This is just a cheap acer aspire one laptop that has a built in webcam.  

I know in the ruby language it has an ssh class.  It is very easy to call that and have it take a file and upload it how ever many times that it wants.  I just got to get something to take a picture with the webcam every so often...

---

### Post by esaym on 2008-08-18
It was a piece of cake

I used uvccapture for the snapshots and ruby to upload it to the server: [http://www.aspireoneuser.com/forum/viewtopic.php?f=13&t=1408](http://www.aspireoneuser.com/forum/viewtopic.php?f=13&t=1408)

---

