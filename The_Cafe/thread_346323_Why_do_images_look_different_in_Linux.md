---
title: "Why do images look different in Linux?"
date: 2007-01-25
forum: The Cafe
---

### Post by Rede on 2007-01-25
So I've been messing around with web development a lot lately, and I've run into a troublesome problem...

I go to school and I'm able to use both Windows and Linux in the classroom. I use Windows for Photoshop and go back to the Ubuntu machine for pretty much everything else. What I've noticed is that images look entirely different on a Windows machine than they do on my Linux boxes. 

I had just put together this website with a background (see attachment) that has a textured pattern to it but looks almost totally white when I look at it with the Ubuntu machine. However when I was working with it, and when I viewed it on the page, it has a very definite pattern (as intended) on the Windows box and if you highlight it on Ubuntu you can tell there is a pattern. Anybody have any idea why it appears so differently?

I'm posting this here because its more of a "Why?" thread than a "How do I fix this?" thread, though if there is a quick solution please don't hesitate to let me know. (If this doesn't belong here, sorry!)

---

### Post by Lord Illidan on 2007-01-25
24 bit/ 16 bit colour issues, maybe?

I looked at it, could see the pattern. greyish blue on white, right?

---

### Post by _simon_ on 2007-01-25
It doesn't look at all white to me, I see a textured image....

You sure you monitor settings are correct?

---

### Post by Lord Illidan on 2007-01-25
Graphics card drivers installed?

---

### Post by MkfIbK7a on 2007-01-25
im not sure it has anything to do with the os

probably your monitor is not calibrated

on the other hand it could have to do with the image being indexed and not using the correct pallete

otherwise maybe the color depth on one monitor is worse than the other

---

### Post by Rede on 2007-01-25
So I had a look and the brightness and contrast settings on the two identical monitors are exactly the same. However, when i turned down the brightness and contrast on the Linux one, I was able to make it appear the same or very similar. 

I'm not sure if its a driver thing, color depth, or what... but thanks for the tips!

---

### Post by tito2502 on 2007-01-25
Maybe the Windows monitor is dirty.

---

### Post by v8YKxgHe on 2007-01-25
> **tito2502 said:**
> Maybe the Windows monitor is dirty.

Perhaps he needs to get some Window cleaner on his monitor? :D

---

### Post by icarus.lnx on 2007-01-25
what video card do you have and what video drivers is it using? It might be a digital vibrance setting that needs to be toned down or up...

---

### Post by ekravche on 2007-01-25
had to adjust the monitor's contrast and brightness settings in order to see the image.

---

### Post by Crashmaxx on 2007-01-25
I'm on XP at work right now, and I just see white. Its not Linux, that's for sure.

---

### Post by Rede on 2007-01-25
I'm using an on-board Intel video card at school. I noticed the same thing at home with my nvidia video card, so I think its more of a case-by-case scenario related to the monitor and default color settings for the drivers than a problem with linux in particular.

---

### Post by Daveski on 2007-01-25
> **Rede said:**
> So I had a look and the brightness and contrast settings on the two identical monitors are exactly the same. However, when i turned down the brightness and contrast on the Linux one, I was able to make it appear the same or very similar. 

I'm not sure if its a driver thing, color depth, or what... but thanks for the tips!

A classic problem trying to reproduce colour images. Just go into a shop that sells TV's and see if any 2 of them match in hue, brightness, contrast etc. Most modern video cards will allow driver based gamma and/or contrast/brightness/saturation changes, and this is in addition to the monitors own settings, AND the fact that different monitors will have different biases and colour temperatures.

---

### Post by futz on 2007-01-25
Usually when you install Photoshop you run their color correction profile setup thing. That applies color correction settings to your video output on every bootup.

There's no corresponding color profile thing (that I know of) for Linux. So in Linux you're getting video card/monitor defaults instead of at least partly corrected color.

The only really accurate way to  set up a color profile is to use a monitor spider, but they're expensive and 99% of people just don't need their colors that accurate.

---

### Post by mips on 2007-01-26
> **futz said:**
> 
There's no corresponding color profile thing (that I know of) for Linux. So in Linux you're getting video card/monitor defaults instead of at least partly corrected color.

The only really accurate way to  set up a color profile is to use a monitor spider, but they're expensive and 99% of people just don't need their colors that accurate.

Colour profiling can be done in linux. Has been discussed here before and on dpreview. Do a bit of searching.

spiders/calibrators are expensive as you mentioned. I used a website with some colour charts to manually profile my video. I suppose it is not 100% but it is good enough for me.

---

