---
title: "GUI Video capture application for webcams"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by cmpunk on 2008-07-21
I just got my integrated webcam to work with Skype, and now I need a good GUI video capture application. The only applications that I can find, only take pictures.

Can someone help me?

---

### Post by warp99 on 2008-07-21
Cheese captures video and stills plus you can add effects:

[http://arstechnica.com/journals/linux.ars/2007/08/21/cheese-brings-photoboth-functionality-to-linux](http://arstechnica.com/journals/linux.ars/2007/08/21/cheese-brings-photoboth-functionality-to-linux)

I believe Cheese is in the main repositories.

---

### Post by cmpunk on 2008-07-21
Cheese doesn't work with my webcam, every time I open it, Cheese freezes.
I want something differnet

---

### Post by Stochastic on 2008-07-21
can you explain a bit more: what webcam do you have?  what drivers does it use?  If you run cheese from the command line what errors pop up?

Cheese should work with any webcam that runs on Linux, but you may need to manually install the driver.

There are other capture programs out there if my memory serves correct, but Cheese is what I use, so I can't recall any others off the top of my head.

---

### Post by cmpunk on 2008-07-21
I have a 0c45:624f Microdia built-in webcam and when i first installed ubuntu, it wouldnt work, but after alot of searching, i finally found the driver for it and now it works with Skype and i heard somewhere that my webcam doesnt work with cheese and i tried that and it didnt work and now im looking for a different video capture application.

---

### Post by warp99 on 2008-07-21
Luvcview is a small program for testing that will capture videos to .avi format. It should work with your particular webcam since it uses v4l2. The version in the repositories is older, but you can build the current version from the subversion library here:

[http://www.quickcamteam.net/software/linux/v4l2-software/luvcview](http://www.quickcamteam.net/software/linux/v4l2-software/luvcview)

It compiles in about 30 seconds since it's a small app, about 40K.

---

