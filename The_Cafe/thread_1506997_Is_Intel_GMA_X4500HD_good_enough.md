---
title: "Is Intel GMA X4500HD good enough?"
date: 2010-06-11
forum: The Cafe
---

### Post by Borjs85 on 2010-06-11
(First of all sorry for my english)

Hi guys,

I'm going to buy a laptop this weekend, but I don't want to spend a lot of money.

I want it to run smoothly KDE desktop effects and compiz, to play HD online contents and to play high definition movies (1080p).

I've found an HP laptop with an i3 330m and this graphic card for 490€. 

How good is the support for this card?

---

### Post by Sam Fallow on 2010-06-11
Hi, (your English is fine)

I have a 4500MHD gpu and it runs okay. Next time I would look for a nvidia card as that has more support, but as I say, no problems for me running 10.04 64-bit.

Also you might want to do some research on sound issues with hp laptops (I suffered with my previous laptop) and make sure your choice is not affected.

Good luck with your purchase.

Sam.

---

### Post by Miguel on 2010-06-11
If the processor is a core i3, there is no way the GPU is an X4500. Core i[3,5,7] come with the X5500 on-die. This one is roughly twice as fast as the X4500. 

In my experience (T400), the X4500 is more than decent in windows as long as you don't game (HL2 is certainly feasible, though). In linux, things change. 2D accel is fine, compiz is certainly more than usable and Kwin's effects are passable (but not great, mind you). 3D, however, is horrible compared to windows. Nevertheless, it's good enough to play world of goo at 1280x800. I haven't tried to play OpenArena, though.

EDIT: The 3D performance has improved very noticeably since Jaunty.

---

### Post by madjr on 2010-06-11
> **Borjs85 said:**
> (First of all sorry for my english)

Hi guys,

I'm going to buy a laptop this weekend, but I don't want to spend a lot of money.

I want it to run smoothly KDE desktop effects and compiz, to play HD online contents and to play high definition movies (1080p).

I've found an HP laptop with an i3 330m and this graphic card for 490&#8364;. 

How good is the support for this card?

yeap, good enough

you have a link to the laptop?

---

### Post by Borjs85 on 2010-06-11
Thanks to all you three!

I haven’t any link. I’m at work and I can’t look for it. But if I remember well, it was an HP G-62 110S.

I’m asking for this card because, despite other stores specs, I’ve found one that said that this was the one build in, and I prefer to consider the worst case

---

### Post by 3rdalbum on 2010-06-11
If you want to play 1080p videos, you are best off going with an Nvidia graphics solution. I don't think Intel has video decode acceleration yet on Linux, whereas Nvidia's is quite mature and well-supported.

Without video decode acceleration, on a laptop CPU... you'd need to turn off Compiz, and it probably still won't be fluent. It'll eat your battery life too.

---

### Post by Miguel on 2010-06-11
> **3rdalbum said:**
> If you want to play 1080p videos, you are best off going with an Nvidia graphics solution. I don't think Intel has video decode acceleration yet on Linux, whereas Nvidia's is quite mature and well-supported.

Without video decode acceleration, on a laptop CPU... you'd need to turn off Compiz, and it probably still won't be fluent. It'll eat your battery life too.

I'll have to agree with 3rdalbum. While 720p is fine, apparently 1080p is out of bounds for an X4500 in linux.

---

### Post by Linuxforall on 2010-06-11
I would look for a laptop with nvidia to be on the safe side, vdpau works fine, so does all effects etc.

---

### Post by cascade9 on 2010-06-11
> **3rdalbum said:**
> If you want to play 1080p videos, you are best off going with an Nvidia graphics solution. I don't think Intel has video decode acceleration yet on Linux, whereas Nvidia's is quite mature and well-supported.

Without video decode acceleration, on a laptop CPU... you'd need to turn off Compiz, and it probably still won't be fluent. It'll eat your battery life too.

+1. 

> **Miguel said:**
> I'll have to agree with 3rdalbum. While 720p is fine, apparently 1080p is out of bounds for an X4500 in linux.

Even with a X4500, 1080p should be playable....given enough CPU power (probably in the order of 2.5Ghz+ dualcore). Its going to eat a lot more power, and create a lot more heat than VDPAU (or XBVA...if thats working, no idea if it does work well yet).

---

