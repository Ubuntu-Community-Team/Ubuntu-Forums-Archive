---
title: "[SOLVED] Commandline non-X image viewer?"
date: 2009-01-06
forum: Server Platforms
---

### Post by Madasi on 2009-01-06
I'm trying to see if anyone knows of a commandline image viewer that doesn't use X?

I used seejpeg many years ago on Slackware, but it isn't in the repositories, and doesn't appear to be under active development any longer.

I've got lanmap running on my Ubuntu server, and was looking for a way to view the outputted graphic file.

---

### Post by cariboo on 2009-01-06
Have a look a feh, to see if it what you need.feh is in the repositories.

Jim

---

### Post by sisco311 on 2009-01-06
try fbi

[HOWTO: Ubuntu CLI versions & Framebuffer Programs]("http://ubuntuforums.org/showthread.php?t=882596")

---

### Post by lswb on 2009-01-06
"fbi" is one that works if framebuffer is enabled. 

There is a viewer called zgv that will work if svgalib is installed. 

mplayer can even display video in a vt with either svgalib or framebuffer.

---

### Post by Madasi on 2009-01-09
Thanks, that HOWTO was exactly what I was looking for.

I had looked at feh before, but it requires X as far as I  could tell.

zgv works well, but seems to lock the box whenever I exit it, so I guess it is time to get the framebuffer operational and give fbi a shot. On the plus side, that will let me use links2 as well!

---

