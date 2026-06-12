---
title: "4K and 8K Super HD Resolution Support in Ubuntu"
date: 2013-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by King Dude on 2013-06-07
If you have been following the news, you'd have known that various TV and computer monitor manufacturers have unveiled 4K and 8K super HD resolutions, which is almost 4-8 times more definition than 1080p. So the question is, when do you think support will arrive for those kind of resolutions in Ubuntu?

---

### Post by SeijiSensei on 2013-06-07
That will be up to the graphics card manufacturers.  I see that [ATI has a 4K card for about $1K]("http://www.engadget.com/2013/04/24/amd-details-radeon-hd-7990/") now.  If they write Linux-compatible drivers for it, then it will be available to users.

Of course, with 4K displays still in the [multi-thousands of dollars]("http://www.theverge.com/2013/6/4/4394294/asus-4k-monitor-price-release-date-and-retina-compatibility"), I doubt these technologies will be in many homes for quite a while.

---

### Post by King Dude on 2013-06-07
True, but it's always good to be ahead of the game.

---

### Post by 3rdalbum on 2013-06-08
I wonder if Xorg would collapse under the strain of trying to throw 33 megapixels onto a screen, 30 times per second.

---

### Post by MadmanRB on 2013-06-08
Well X mat not be a factor once weyland and Mir take hold

---

### Post by sandyd on 2013-06-10
Its already possible with Windows, - I tried it by mistake, and later for fun on a 4K screen which was part of a main stage display. Havent tried it with Ubuntu though, and I dont have access to that screen right now.

---

### Post by King Dude on 2013-06-11
> **sandyd said:**
> Its already possible with Windows, - I tried it by mistake, and later for fun on a 4K screen which was part of a main stage display. Havent tried it with Ubuntu though, and I dont have access to that screen right now.
If you could try it with Ubuntu when you get the chance it would be great.

---

### Post by Cheesemill on 2013-06-12
The support is already here. The Nvidia Quadro K5000 supports 4K TV and works with the current Linux Nvidia driver so buy the right kit and it will work without any problems.

You're talking about a £2,000 graphics card and £20,000 for a TV though.

---

### Post by sandyd on 2013-06-14
Managed to get some time tonight to test it out. I can't really take a picture because I kind of 'borrowed' the screen that was on a working stage.

Specs (I doubt it matters anyways):
CPU: E3-1290 v2 
RAM: 16GB
Graphics: Nvidia Quadro K5000 + Nvidia Tesla K20????

The Nvidia Quadro was originally setup to create design/simulations and realtime 3D rendering, and was setup to use Nvidia Maximus with a Tesla K20. When I first started it up, it didn't show the K20, so I personally dont even know if its being used at all. Im not bored enough to detatch it. Required a bit of struggling, but patched it into the display with a displayport cable.

Xorg managed to open FF and play TSwift's VEVO channel at 1080p (was blury, but then again, 1080p without deinterlacing + full screen on a resolution thats around 4 times as high *winces*). I played a direct copy of Oz the Great on there (full blu-ray data), and that played too without issues. Wesnoth decided to struggle a bit, but thats probably because it wasnt meant to be displayed on 4K. I havent tried any Steam games because downloads take forever over a 4G connection.

---

### Post by Dmole on 2013-08-26
Anyone try Ubuntu with this $700 USD 4K monitor?:
[http://gdgt.com/seiki/se39uy04/specs/](http://gdgt.com/seiki/se39uy04/specs/)

---

### Post by codingman on 2013-08-27
@sandyd Do you notice any difference between that screen and a standard 1080P display (using Windows)? Just wondering if tech is moving forward, or backward...

---

