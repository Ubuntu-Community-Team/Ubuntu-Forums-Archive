---
title: "Detailled info needed on patching wine"
date: 2008-12-23
forum: Wine
---

### Post by Alexpants on 2008-12-23
I'm still having problems with my spore install, after a length call to EA and a lot of googling I've found this patch:
[http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html](http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html)
Which has helped fix the issue for a lot of people. 
The only thing is I don't know how to apply this patch, I've searched the forums a bit but I don't know if I've used the wrong search terms but I can'nae find anything. 
How do I apply this? 
Thank you!

---

### Post by kostkon on 2008-12-23
> **Alexpants said:**
> I'm still having problems with my spore install, after a length call to EA and a lot of googling I've found this patch:
[http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html](http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html)
Which has helped fix the issue for a lot of people. 
The only thing is I don't know how to apply this patch, I've searched the forums a bit but I don't know if I've used the wrong search terms but I can'nae find anything. 
How do I apply this? 
Thank you!
Which version of Wine are you using? I assume that the latest versions of Wine has this patch already.

---

### Post by Alexpants on 2008-12-23
I'm using 1.1.10, sorry I should have stated that in the original post! 
Dang, I was hoping applying that would fix the issue but I guess I'm back to the drawing board :(

---

### Post by albinootje on 2008-12-23
> **Alexpants said:**
> I'm still having problems with my spore install, after a length call to EA and a lot of googling I've found this patch:
[http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html](http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html)
How do I apply this? 

First of all you need to install git-core which supplies git-diff, which can do diff --git :

$ dpkg -S $(which git-diff)
git-core: /usr/bin/git-diff

Then i assume you use git to fetch the wine-source, and then cd into the downloaded wine source code, and run the linked patch with sh.
Makes sense ?

Check this for more info! :
[http://wiki.winehq.org/GitWine](http://wiki.winehq.org/GitWine)

---

### Post by Alexpants on 2008-12-23
Oh wow, that's all greek to me! I'm gonna go check the link and report back when I've figured it out (or if I get stuck, haha!)
Thank you :)

---

