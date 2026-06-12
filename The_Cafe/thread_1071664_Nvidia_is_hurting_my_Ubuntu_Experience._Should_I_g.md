---
title: "Nvidia is hurting my Ubuntu Experience. Should I go ATI?"
date: 2009-02-16
forum: The Cafe
---

### Post by Morty007 on 2009-02-16
I'm in a bind.

Nvidia is ruining my Ubuntu experience with all of their driver problems. I have laggy scrolling and laggy tab switching in firefox.

[**[SIZE="5"]This thread[/SIZE]**]("http://www.nvnews.net/vbulletin/showthread.php?p=1933510")  has people who have spent hundreds of hours messing with the bios, disabling this, enabling that etc. 


 Many people are having graphical corruptions with the 180 drivers, which I tried and the tab switching was fine, as well as the scrolling. But I then got this about once an hour.
 
[[img]http://xs536.xs.to/xs536/09060/img_0911301.jpg[/img]](http://xs.to)

 I'm using the 177 driver but tab switching and scrolling are very choppy. It's putting a big crimp in my enjoyment of Ubuntu to say the least.

At this point I'm thinking if I should shell out some bucks for an ATI card and have the best buy geek squad install it. I called them and they claimed that there are linux people there, but I'm scared they will screw something up.

What is your opinion? Wait indefinitely for nvidia to get their act together or go ATI?

---

### Post by cardinals_fan on 2009-02-16
Bah, that's not so bad.  The latest NVIDIA drivers on my machine provide me with a one-pixel thin line.  That's it.  This isn't a new issue; I've reported it for every version since 171.  They ignore me.

Then I realized that I don't use 3D apps.  So I switched to Xvesa, and my computing life has been happier every since.

---

### Post by Coreigh on 2009-02-16
Is there not a more stable driver available? I use the nVidia driver from the repo's (installed with apt, not custom installed) and it works very well. I am not sure how to identify the version number. I use compiz and everything.

It would be a lot cheaper to use an older stable driver than to go buy a new video card. Even then if you use the "bleeding-edge" new drivers it probably won't be any more stable than what you have now.

---

### Post by Skripka on 2009-02-16
I'm using 180.11 with my GTX260, and am happy as a clam.  Try upgrading drivers-it is free, I had several hanging issues with 177.80.

---

### Post by BuffaloX on 2009-02-16
My wifes Nvidea burned out recently, and we bought an ATI 4830.
She had serious problems with the drivers in repository,
But the latest drivers work very well both the open source and proprietary.

If you need real time kernel ATI works with that too, Nvidea didn't as of 1 week ago, could have been fixed in the meantime.

I hope you get it to work using the latest Nvidia driver, but if you must buy a new card, it seems ATI is the better choice right now.

---

### Post by Morty007 on 2009-02-16
> **cardinals_fan said:**
> Bah, that's not so bad.  The latest NVIDIA drivers on my machine provide me with a one-pixel thin line.  That's it.  This isn't a new issue; I've reported it for every version since 171.  They ignore me.

Then I realized that I don't use 3D apps.  So I switched to Xvesa, and my computing life has been happier every since.
 
Actually, that is my better screen. My original one was a nice 100% lime green screen. But they're both bad!

---

### Post by Morty007 on 2009-02-16
> **Skripka said:**
> I'm using 180.11 with my GTX260, and am happy as a clam.  Try upgrading drivers-it is free, I had several hanging issues with 177.80.

My desktop has a 8800GTS and it's smooth as can be. But people's laptops are a different story.

---

### Post by Grant A. on 2009-02-16
If you don't use any 3D apps, just go with the vesa drivers. I have heard that 3D apps work fine in vesa with opengl, but I'm not sure about that.

---

### Post by Crafty Kisses on 2009-02-16
I have NVIDIA GeForce 9800GTX and it works great with the 177 driver. It's possible the card is overheating or something. ATI is kind off a toss up with Linux, but if you don't want to buy NVIDIA products, then I guess ATI would be your second best option. Personally I'd always go with NVIDIA just because they have great Linux support.

---

### Post by shazbut on 2009-02-16
IMO the screen shot looks more like a hardware fault than drivers, I had a GF4Ti4200 that did that occaisionally, but got worse until it even did it during POST.  It was a cheap xpertvision card, so most likely bad capacitors or memory.  I had no trouble with nvidia drivers with any of the other cards I've got (GF4MX440, GF3Ti200, 6600GT).  Having said that, I did go for an ATI HD4670 for my next purchase since I was after low power (no extra power connector).  The fglrx drivers still need some sorting out (I had to manually install catalyst 8.12, since the card is too new for hardy or intrepid).  Full window dragging is jerky in metacity, but nice and smooth in compiz, however video flickers in compiz but not in metacity.  Lucky I've got fusion-icon installed.

---

### Post by Morty007 on 2009-02-17
> **shazbut said:**
> IMO the screen shot looks more like a hardware fault than drivers, I had a GF4Ti4200 that did that occaisionally, but got worse until it even did it during POST.  It was a cheap xpertvision card, so most likely bad capacitors or memory.  I had no trouble with nvidia drivers with any of the other cards I've got (GF4MX440, GF3Ti200, 6600GT).  Having said that, I did go for an ATI HD4670 for my next purchase since I was after low power (no extra power connector).  The fglrx drivers still need some sorting out (I had to manually install catalyst 8.12, since the card is too new for hardy or intrepid).  Full window dragging is jerky in metacity, but nice and smooth in compiz, however video flickers in compiz but not in metacity.  Lucky I've got fusion-icon installed.

I can't really believe it's hardware, everything is fine with 177 drivers except some lag which many others are reporting. As soon as 180.xx is in there, there are immediate screen problems.

---

### Post by Morty007 on 2009-02-17
> **Codename said:**
>  Personally I'd always go with NVIDIA just because they have great Linux support.

There's about a thousand people on the nvidia linux forum who would disagree with that comment. Just read that link. LOTS of disappointed people who are threatening with going ATI.

---

### Post by Rumbl3 on 2009-02-17
177 and 180 have worked flawless for me. 

I see a lot of threads saying this and that don't work. Starting to think i'm either lucky and have just the right hardware or maybe things are not that bad.

either way my 9600gt works like a charm on both them drivers.

now back when i first ever tried linux on SuSe i had ati card, wasn't horrible but didn't work great either. Then i got a 3850 radeon tried SuSe again then (everyone always told me it was linux for new people) and it didn't work very well tried ubuntu still didn't work well. 

Switched to a 9600gt when they came i'll never go back to ati till they get there drivers straight on linux and windows.

---

