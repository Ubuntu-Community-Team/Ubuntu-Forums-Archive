---
title: "Switched from XP to Ubuntu."
date: 2007-10-31
forum: Testimonials &amp; Experiences
---

### Post by Lee05162004 on 2007-10-31
I recently switched from Windows XP to Ubuntu Linux and so far I like Ubuntu although there are a few problems I'm having that I'm trying to get worked out. The most important thing I am trying to get fixed is the ability to play DVDs. I have followed many, many different tutorials on how to get DVDs to work and none of them have worked but the problem is that I cannot download the required packages. I have not been able to find the same packages in a different location either. 

The second thing is that I have an ATI graphics card and I can't seem to get any of the eye candy to work. I do have the correct dirver installed for it and all the additional packages that are required as far as I know but it just doesn't work. This is not a big issue either but it's just something I would like to get to work eventually.

My most important issue I had which prevented me from switching over to Linux before was wireless support. I finally attempted to dual boot XP and Ubuntu and for some reason it failed so I just went with Ubuntu and I was able to update it via the ethernet port in my laptop and then after just a few more drivers and stuff I got the wireless to work. Once the wireless worked I decided I would stick with Ubuntu for good and I have no plans of switching. 

Overall I like Ubuntu so far, I have been able to find programs for everything I need or want to do and there's just a few things that are not major that I would also like to get worked out. I would like to be able to convert my iTunes music from Apple's format over to .mp3. That's about it for now. I'm sure I'll find ways to get everything working eventually.

---

### Post by lancest on 2007-10-31
For DVD playback try this:
sudo apt-get install libdvdread3 libxine1-ffmpeg   
(Copy and paste into command line for DVD playback in Totem Movie player)  It worked for me!
I think you will get the other things sorted out. Enjoy Ubuntu!

---

### Post by jayson.rowe on 2007-10-31
For DVD playback, add the Medibuntu repo and install libdvdcss2...other reccomended multimedia packages ubuntu-restricted-extras (if you're on Gutsy) and w32codecs (w64codecs if you're running AMD64)

---

### Post by armandh on 2007-10-31
all this is a regression from 7.04 where a few clicks and my home made dvds played

---

### Post by lyndaj70 on 2007-10-31
Try automatix2.  [www.getautomatix.com](www.getautomatix.com) 

Nice simple way to get your codecs and get started....

Good luck!

---

### Post by wolfen69 on 2007-11-02
getting codecs/flash/java  takes 1 click in ubuntu, it's more work to install automatix. no need for it.

---

### Post by Johnsie on 2007-11-02
I heard somewhere that ATI will be supporting Linux better soon. Let's hope this makes it easy for the Linux developers to support your card properly.

There are a few  tutorials about how to enable the eye candy on ATI cards but realistically speaking it should work out of the box. Hopefully that'll become more and more common as Ubuntu matures.

---

