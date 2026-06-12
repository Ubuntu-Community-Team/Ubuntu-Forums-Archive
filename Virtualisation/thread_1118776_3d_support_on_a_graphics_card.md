---
title: "3d support on a graphics card"
date: 2009-04-07
forum: Virtualisation
---

### Post by JokerStud on 2009-04-07
I installed vmware and followed the instructions on this guide: 
[http://ubuntuforums.org/showthread.php?t=372928](http://ubuntuforums.org/showthread.php?t=372928)

My problem is that my graphics card is neither ati or nvidia but:

Intel Corporation 82945G/GZ Integrated Graphics Controller

Is it possible to enable 3d support?

---

### Post by 00arthuryu on 2009-04-08
there is no 3D hardware acceleration with anything within virtualbox, regardless of graphic card

---

### Post by linuxuser21 on 2009-04-08
> **00arthuryu said:**
> there is no 3D hardware acceleration with anything within virtualbox, regardless of graphic card

Yes it does, that's one of the reasons it is so popular.  It started to at about version 2.1.0.

---

### Post by binbash on 2009-04-09
virtual box 2.2.0 has opengl 2.0 support for linux guests.

---

### Post by Son of William on 2009-04-10
Your chipset (Intel 82945G) is very old and limited.  See this [thread]("http://ubuntuforums.org/archive/index.php/t-1100761.html") which indicates you can't even get 3d support out of it for Ubuntu even if you are not installing to a vm.

---

### Post by drewsus on 2009-10-10
not true, my parents desktop has that gfx card and compiz works. I just dont rem how I didnt (which sucks cuz Im reinstalling it now....)

---

