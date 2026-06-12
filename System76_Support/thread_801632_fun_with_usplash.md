---
title: "fun with usplash"
date: 2008-05-20
forum: System76 Support
---

### Post by jeamer on 2008-05-20
Hey, I followed this:

[http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)

and dumbingly assumed that something written in 2005 (and thus probably for Dapper) would work on a nice install of 8.04. It didn't. Now I have no splash screen, just the nice run through all the text checks of the system as it loads. Of course, the method to revert back to the old usplash provided in the tutorial doesn't work as well. Anyone want to take a gander and explain why this wouldn't work in hardy? 

P.S. I have been dying to find out what version of Pangolin I have. I've read threads that say look at the bottom, but I see no semblance of anything that looks like "Panv4". In fact, there is a sticker that tells me my model is "Laptop" but I'm sure thats not helpful. I ordered my laptop about a month ago, if that helps. Also in the Sys76 driver it tells me my model is a Serp4.

---

### Post by thomasaaron on 2008-05-21
You have a PanV3.

---

### Post by MeURi on 2008-05-21
Hi jeamer

Try to install *startupmanager*, and see if it solves your problem (it is is in the Universe repository, [details here](http://packages.ubuntu.com/hardy/startupmanager))

I cannot tell why the method doesn't work in Hardy, especially since I'm on Windows, now, and I can't reboot into Ubuntu

Hope this helps

---

### Post by Vadi on 2008-05-21
Commands stolen off ubuntusatanic.org:

```
sudo update-alternatives --set usplash-artwork.so \
/usr/lib/usplash/usplash-theme-ubuntu.so

sudo update-initramfs -u
```

---

### Post by jeamer on 2008-05-21
tried the ubuntusatanic way to no avail, but startup manager solved my problems! thanks guys.

---

### Post by MeURi on 2008-05-23
Glad to hear :-)

---

