---
title: "Ubuntu studio software removal?"
date: 2014-01-13
forum: Ubuntu Studio
---

### Post by frank18 on 2014-01-13
Hi guys; i installed Ubuntu Studio 1310 and i like it  and i use it mostly for streaming videos on the web there  is lot's of audio  and video software that i don't use,can you tell me which software i can remove that will not affect  the video codecs  
and keep the software to be able to use the web. thanks.

---

### Post by carl4926 on 2014-01-13
I'd advise against it

---

### Post by su:bhatta on 2014-01-14
Ubuntu Studio is made up of meta packages. 

This result in dependency problems if you try to remove some of the softwares that you don't use.

E.G,  a simple removal or Ardour, which you may never use, leads to removal  of entire ubuntustudio-audio metapackage. Hence this is not advised

If you want to only stream videos on the web, you can give some other flavor of Ubuntu a try, 
 Xubuntu is the first that comes to mind, since it also has Xfce DE, just like Ubuntu Studio. You will get a same interface there.

---

### Post by Bucky Ball on 2014-01-14
Yes, I would work the other way too, as suggested. Start with something lighter and add what you need. If streaming vid from the web is what you want to do UStudio is like shooting a mosquito with an elephant gun; there's a ton you will never use and trying to get rid of things will be problematic.

---

### Post by frank18 on 2014-01-14
Thanks You all that gave me advice i will fallow your advice thanks.

---

### Post by frank18 on 2014-01-14
> **Bucky Ball said:**
> Yes, I would work the other way too, as suggested. Start with something lighter and add what you need. If streaming vid from the web is what you want to do UStudio is like shooting a mosquito with an elephant gun; there's a ton you will never use and trying to get rid of things will be problematic.

thanks bro: so you say that i have no advantage with Ubuntu studio 1310 over any of the other Ubuntu flavors   when it comes to live video streaming from the web,what about all the video codecs for various players out there.?

---

### Post by jejeman on 2014-01-14
You can install them on any Ubuntu/Linux.

---

### Post by Bucky Ball on 2014-01-14
> **jejeman said:**
> You can install them on any Ubuntu/Linux.

^^^
This. 

For example, not a codec, but I installed the low latency kernel last night for audio/visual work. I am running a minimal install of 14.04 with xfce4 as a desktop manager. One of the beauties of Ubuntu is it's highly customisable.

As suggested, you might want to go for a lightweight Xubuntu install and build it up from there (or even a minimal install if you're up to that). ;)

---

### Post by frank18 on 2014-01-15
Thanks guys i ended up installing Xubuntu 13.10 and i have to say that it's running great so far.

---

### Post by Bucky Ball on 2014-01-15
That's because Xubuntu rocks!!! ;)

If you consider this solved please mark it that way from the instructions in my signature and start a new thread for any further issue. ;)

---

### Post by zequence on 2014-01-16
There's absolutely no harm in removing the meta packages ubuntustudio-*, since that will not remove any of their dependencies.

A meta package in itself is emtpy, such as the package ubuntustudio-video. It doesn't contain anything. It just depends on a list of other packages.

If you upgrade to a newer release, one of the meta packages might have gotten new dependencies - usually new additions of applications that wasn't included before. So, upgrading to a newer release will mean that you don't get new additions to a meta package, if it is not installed. That is the only downside of not having it installed.

If you are only out to do video, then Ubuntu Studio is not essential. You might like to install ubuntustudio-menu though, if you like having things ordered in that way.

---

