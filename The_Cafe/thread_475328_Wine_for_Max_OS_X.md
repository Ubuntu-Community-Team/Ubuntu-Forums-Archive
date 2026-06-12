---
title: "Wine for Max OS X"
date: 2007-06-16
forum: The Cafe
---

### Post by bigdidz on 2007-06-16
I know that the new mac OS X is a Unix based operation system, so I have 2 questions for you:
-  Why do the softwares made for mac OS X don't work on Linux?
- Why there is no wine for OS X programs ( and would it be faster?)

---

### Post by tehkain on 2007-06-16
> **bigdidz said:**
> I know that the new mac OS X is a Unix based operation system, so I have 2 questions for you:
-  Why do the softwares made for mac OS X don't work on Linux?
- Why there is no wine for OS X programs ( and would it be faster?)

1. Because of the Mac gui components. Cocoa(right?) and aqua are closed and are hard to duplicate
2. Because of the above plus APIs. Windows is far easier to replicate.

---

### Post by johntelthorst on 2007-06-16
If the program is low level enough it will work on both Linux and Mac OS X.  OS X has many layers however and the BSD Unix base is near the bottom.  OS X using Aqua and Cocoa and other software layers that might not be compatible.  This link might help.  [http://www.creativepro.com/img/story/100302_fg2.jpg]("http://www.creativepro.com/img/story/100302_fg2.jpg")

The Darwin base at the bottom of that diagram is the unix part of the system.  OS X is not all open source, only some parts of it.  So if an app is written for aqua then it won't work in linux.  You might also want to wait for a reply from someone who really knows what they're talking about, but in general I think what I'm telling you is true.  There is wine for OS X users, it's called Darwine ([http://darwine.sourceforge.net/]("http://darwine.sourceforge.net/")).

Edit:  I guess I misunderstood you; I don't know why there isn't a wine-like program for running OS X apps.

---

### Post by patrick295767 on 2007-06-16
Look the website of cider (it s for mac os)

[http://www.joystiq.com/2006/08/04/cider-promises-windows-games-in-mac-os-x/](http://www.joystiq.com/2006/08/04/cider-promises-windows-games-in-mac-os-x/)

---

### Post by ssam on 2007-06-16
no.

although it is technically possible, nobody has done it, and it would be a vast amount of work for somebody to start.

In someways it might be easier, mac os x has an open source unix kernel and bsd system utilities. In other ways it might be more difficult (have a look at this [diagram]("http://ubuntuforums.org/showthread.php?t=428148#post2565589")).

there is is also far less demand for running mac os x programs on linux. there are only a few mac os x programs that don't have a windows or linux version. where as there are a lot of windows programs that dont have a linux version. why make a mac-os-x-wine to run mac photoshop when you can run windows photoshop in wine. it would be hard to find many programmers who wanted to make a mac-os-x-wine.

wine was started in 1993, and is still not complete. so even with a good team of programmers, a mac-os-x-wine would take many years to make.

---

### Post by machoo02 on 2007-06-16
> **patrick295767 said:**
> Look the website of cider (it s for mac os)

[http://www.joystiq.com/2006/08/04/cider-promises-windows-games-in-mac-os-x/](http://www.joystiq.com/2006/08/04/cider-promises-windows-games-in-mac-os-x/)

This in not for running OS X applications in Linux...this is basically Wine ported to OS X, similar to what [CodeWeavers has done with Crossover Mac]("http://www.codeweavers.com/products/cxmac/").

---

### Post by cogitordi on 2008-06-27
Found this thread and just thought I'd update the information.

Install X11 and MacPorts on an Intel Mac and you can use Wine. 

OS X Tiger is stable. The latest Leopard update breaks X11 (so you have to install a fixed X11 manually).

---

### Post by ThunderMoon99 on 2012-12-16
I heard a collage student was working on something like it but it is not currently available to the public

---

### Post by deadflowr on 2012-12-16
super duper old thread.

---

### Post by lisati on 2012-12-16
From the Forum [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"):
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed

---

