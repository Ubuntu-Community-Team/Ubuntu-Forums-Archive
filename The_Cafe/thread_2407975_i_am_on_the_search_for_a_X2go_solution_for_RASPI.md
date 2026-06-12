---
title: "i am on the search for a X2go solution for RASPI"
date: 2018-12-11
forum: The Cafe
---

### Post by dilbert_one on 2018-12-11
hello dear experts


i am on the search for a X2go solution for RASPI


i have had a quick lookup here at 

[http://wiki.x2go.org/doku.php/wiki:repositories:debian](http://wiki.x2go.org/doku.php/wiki:repositories:debian)

 and

[https://wiki.x2go.org/doku.php/wiki:development:build-server](https://wiki.x2go.org/doku.php/wiki:development:build-server)

well i am not very sure if i can run the x2goserver packages on a ARM
Guess that they are only available for intel platforms. No ARM packages.
I don't know if it's possible to build your own.

Does anybody know some more - do the X2Go rund very slow on arm

---

### Post by TheFu on 2018-12-12
One of you linked pages says:
>  you can build X2Go components for the ARM(el) architecture. This uses qemu soft emulation and will be quite slow and it will also create quite a CPU load.

Currently, only ARM(el) builds (and of course i386, amd64) are supported.

We normally do only build the stable X2Go code base for ARM(el). 

The raspberry pi platforms are engineered to be cheap and fast enough for student projects.  If you need an ARM-based desktop, there are slightly more expensive ARM-based systems like the Pine64 and PinePro64.  There are other options from Odroid as well.  [https://www.phoronix.com/scan.php?page=article&item=odroid-xu4-arm&num=1](https://www.phoronix.com/scan.php?page=article&item=odroid-xu4-arm&num=1)

If the systems involved are on the same subnet, you can use X11 forwarding directly to run GUI X11 programs on the remote system and have the window displayed on your local X-server. No need for x2go. This X11 technique has been working for 40+ yrs.

---

