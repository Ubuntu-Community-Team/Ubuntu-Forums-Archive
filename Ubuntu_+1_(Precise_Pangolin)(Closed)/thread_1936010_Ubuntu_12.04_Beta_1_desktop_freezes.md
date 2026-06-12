---
title: "Ubuntu 12.04 Beta 1 desktop freezes"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by _sAm_ on 2012-03-05
Hi

I want to report a problem with Ubuntu 12.04 Beta 1, but don't know how to do it.

I just did a _clean_ install of Ubuntu 12.04 Beta1, and after using it for some minutes the screen just freezes (and I cant use the keyboard nor the mouse). I looks like it happens when I have many tabs open I Firefox, but it can also happen when I use other programs (like Liferea). I have not installed the proprietary AMD graphic driver. 

This also happened a lot when I tried out the Ubuntu 12.04 Alpha 2. I installed the xbunut-desktop during the Alpha test, and it worked fine, so it must be something with the Unity stuff. This have never happens before on my pc (I have used previous versions of Ubuntu on the same hardware).

I don't know the package name to report, perhaps someone here can advice me. 

Some of my hardware:
Intel Core 2 Quad
AMD Radeon HD 5870


Thanks for any help

---

### Post by 2F4U on 2012-03-05
Here is how to report a problem in Ubuntu

[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

You could also report it in this forum thread:

[http://ubuntuforums.org/showthread.php?t=1888420](http://ubuntuforums.org/showthread.php?t=1888420)

---

### Post by dino99 on 2012-03-05
your logs might tell you about the issue(s) you get (xsession-errors & /var/log/)

otherwise: ubuntu-bug linux

---

### Post by _sAm_ on 2012-03-06
Thank you all for your help, I have now reported the bug on launchpad (Bug #947443). 

Have a nice day :-)

---

### Post by linux6994 on 2012-03-06
I have seen the freezing problem also, not necessarily with many things open but when sitting idle. I just switched from pae to generic kernel to give it a whirl.

---

