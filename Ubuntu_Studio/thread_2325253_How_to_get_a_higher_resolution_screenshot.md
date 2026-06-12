---
title: "How to get a higher resolution screenshot"
date: 2016-05-20
forum: Ubuntu Studio
---

### Post by Nosphky on 2016-05-20
I've been using xfce4-screenshooter to get images of events on screen but this only produces a 72 dpi image.  I know this has been a standard for over 30 years for images used on internet for on-screen displays but with higher resolution screens these days, is it possible to get a higher resolution image ?  Publishers seem to want at least 300 dpi for printing in paper books.

---

### Post by jejeman on 2016-05-20
DPI is not important. You can not make bigger image than it is displayed. Your screen size is the restricting factor. Make the shots on the biggest screen (pixel wise) you can get.

I don't know what you are screenshotting, maybe you can zoom in a little, and then make multiple shots and put them together in GIMP. You can set DPI in GIMP if it is important.

---

### Post by vasa1 on 2016-05-20
> **Nosphky said:**
> I've been using xfce4-screenshooter to get images of events on screen but this only produces a 72 dpi image.  I know this has been a standard for over 30 years for images used on internet for on-screen displays but with higher resolution screens these days, is it possible to get a higher resolution image ?  Publishers seem to want at least 300 dpi for printing in paper books.
I don't know about dpi, but scrot (in the software center) allows you to change the "quality" of screenshots. From *man scrot*```
       -q, --quality NUM
            Image quality (1-100) high value means high size, low compression. Default: 75. (Effect differs depending on file format chosen).

```

---

### Post by Nosphky on 2016-05-21
Thankyou jejeman and vasa1 for your help.  
  
I captured my shot as near full screen as I could get and then scaled it down in Gimp at higher dpi. I got an acceptable image but, naturally, much smaller since Gimp didn't 'fabricate' additional pixels.

From the maximum resolution  setting on my screen and its dimensions, I had estimated roughly I  should be able to get 90 dpi but I was only getting 72dpi from  xfce4-screenshot which does not appear to have any 'quality' settings.

I'll do some trials with multiple shots in Gimp as well as trying scrot.
Again, thank you both.

---

### Post by Nosphky on 2016-05-21
I've made a load of trials to compare xfce4-screenshooter against scrot on single images changed from 72 to 300 dpi in Gimp as well as combining multiple images in Gimp, flattening them to a single layer before changing resolution to 300 dpi.

From printed outputs, I couldn't see any differences (but then maybe my printer is not the greatest).

Scrot is easy to use and powerful but its raw output at high quality (-q 100) gives a file of around 5 MB compared with xfce4-screenshooter around 60 kB.  However, once passed thro Gimp and exported as a png with compression level of 9, the scrot file was around  5 -10% smaller.

My conclusion is that for my use, xfce4-screenshooter  remains the fastest method and I shall stick with that until someone complains about quality.  I am glad that I've discovered scrot - I shall find some use for it elsewhere.

---

