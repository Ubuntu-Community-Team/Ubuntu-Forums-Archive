---
title: "Vista Host Ubuntu 9.04 Guest and No Widescreen"
date: 2009-06-07
forum: Virtualisation
---

### Post by BuntuFreak on 2009-06-07
One of my computer runs Windows Vista Home Premium. I'm not ready to dual boot (or better yet just replace my OS) with Ubuntu yet.

So I installed Virtual Box for Windows and then proceeded to install Ubuntu 9.04 inside of the Virtual Box. Everything went great, except one thing. My monitor is 16:9, however my Ubuntu Window in Virtual Box will only run in two possible 4:3 resolutions - 800 x 600 and 640 x 480.

First, I need to up the resolution option to at least 1024 x 768. Why don't I get it?
Second, I really need to have a wide screen resolution. Why is one not even listed? Is it a matter of installing the right drivers inside of the Ubuntu installation on the Virtual Box VM? And if so, how?

Thanks in advance for any help.

---

### Post by BuntuFreak on 2009-06-07
I solved my problem using this good article.

[http://www.dreamincode.net/forums/showtopic76340.htm](http://www.dreamincode.net/forums/showtopic76340.htm)

Hope it helps someone else assuming they aren't as dense as me :D

---

### Post by iposner on 2009-06-15
(Didn't read the original post properly - d'oh! - user using VirtualBox and not MS Virtual PC. Well for anyone that is...)

If you read the MS Virtual PC 2007 documentation, you'll see that the video card emulated is an S3 Trio 64 -- so you need a driver either for this, or one which supports VESA 2.0

---

