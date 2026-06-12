---
title: "Current RAM usage of all main ubuntu derivatives"
date: 2014-11-21
forum: Ubuntu, Linux and OS Chat
---

### Post by user1397 on 2014-11-21
So, I was interested to see for myself what the current RAM usage is of all of the main flavors of ubuntu (including ubuntu itself) for version 14.10.

I am not claiming these stats to be definitive or anything, and I actually just installed each using Virtualbox (I didn't feel like manually installing each one to a different partition on my hard drive).

The way I measured RAM usage was: I installed each from the live images into Virtualbox, booted them all the way up, opened a terminal and typed ```
free -m
``` and looked at the "-/+ buffers/cache:" row under the "used" column.

Here are the stats (*buntu 14.10):

Ubuntu (Unity): 461 MB
Ubuntu Gnome: 545 MB
Kubuntu: 348 MB
Kubuntu Plasma 5 Preview: 507 MB
Xubuntu: 255 MB
Ubuntu Mate: 270 MB
Lubuntu: 187 MB

I was surprised by the low usage of kde 4 (kubuntu) and ubuntu mate.  Anyway I thought this was a fun little exercise and for anyone interested in some current stats of ubuntu.

---

### Post by ibjsb4 on 2014-11-21
Seems the only way is up :)

[http://mylinuxexplore.blogspot.com/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.com/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html)

---

### Post by mikodo on 2014-11-21
My two distro's on disk.

Xubuntu 12.04 103 MB and for fun,

Ubuntu 10.04   159 MB with compiz running.

---

### Post by sammiev on 2014-11-21
Unity shows the highest usage using htop for me out of all the ubuntu derivatives.

---

### Post by mcduck on 2014-11-22
> **ubuntuman001 said:**
> 
I was surprised by the low usage of kde 4 (kubuntu) and ubuntu mate.  Anyway I thought this was a fun little exercise and for anyone interested in some current stats of ubuntu.

I think that's how it's traditionally been, KDE using less memory but more CPU compared to Gnome.

I'm more surprised about LXDE using that much, considering my Openbox setup (with Tint2 & Compton) uses 38MB. I suppose the additional session management stuff etc. has it's cost...

---

### Post by philinux on 2014-11-22
Moved to U, L and OS chat.

---

### Post by Dragonbite on 2014-11-22
> **ubuntuman001 said:**
> 
Here are the stats (*buntu 14.10):

Ubuntu (Unity): 461 MB
Ubuntu Gnome: 545 MB
Kubuntu: 348 MB
Kubuntu Plasma 5 Preview: 507 MB
Xubuntu: 255 MB
Ubuntu Mate: 270 MB
Lubuntu: 187 MB

I was surprised by the low usage of kde 4 (kubuntu) and ubuntu mate.  Anyway I thought this was a fun little exercise and for anyone interested in some current stats of ubuntu.

That is very interesting, how Gnome is so much more than Unity, and even that KDE Plasma 5 Preview!

When I was looking around a while ago, all of the reports has Unity slightly higher than Gnome and KDE higher than that!  Maybe they were working on an older version of Unity or something, but I can see Unity working slightly quicker.

One question I have is how fast does the Gnome Activities panel show (and be usable) compared to Unity's Dash?

---

### Post by mcduck on 2014-11-23
I suppose that's the interesting thing, using more RAM or CPU doesn't automatically make things slower, in fact it could very well mean things are *more* responsive due to the DE keeping more stuff in the memory... It all depends if the resources are used for right things or if they are just used inefficiently.

---

### Post by user1397 on 2014-11-27
> **ibjsb4 said:**
> Seems the only way is up :)

[http://mylinuxexplore.blogspot.com/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.com/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html)Seems so :/

> **mikodo said:**
> My two distro's on disk.

Xubuntu 12.04 103 MB and for fun,

Ubuntu 10.04   159 MB with compiz running.Yea each year it seems that OS's require more and more ram.

> **sammiev said:**
> Unity shows the highest usage using htop for me out of all the ubuntu derivatives.Like I said, my findings are in no way conclusive, and stats could differ wildly with different setups. 

> **mcduck said:**
> I think that's how it's traditionally been, KDE using less memory but more CPU compared to Gnome.

I'm more surprised about LXDE using that much, considering my Openbox setup (with Tint2 & Compton) uses 38MB. I suppose the additional session management stuff etc. has it's cost...Yea not sure about lxde, but I'm more surprised at how much gnome was using.

> **Dragonbite said:**
> That is very interesting, how Gnome is so much more than Unity, and even that KDE Plasma 5 Preview!

When I was looking around a while ago, all of the reports has Unity slightly higher than Gnome and KDE higher than that!  Maybe they were working on an older version of Unity or something, but I can see Unity working slightly quicker.

One question I have is how fast does the Gnome Activities panel show (and be usable) compared to Unity's Dash?Yea it's always good to see when those reports are from.  I also thought unity would take up more than gnome, and kde would be the biggest one.  I'm very surprised at how much gnome uses.

I don't know for sure how to answer your question about the activities panel, they seemed largely similar to me.

> **mcduck said:**
> I suppose that's the interesting thing, using more RAM or CPU doesn't automatically make things slower, in fact it could very well mean things are *more* responsive due to the DE keeping more stuff in the memory... It all depends if the resources are used for right things or if they are just used inefficiently.This is probably the most important response in this thread...I guess ram usage doesn't mean much in the end if you think about it this way :P

---

### Post by grahammechanical on 2014-11-27
RAM is there to be used.

I noticed when using Utopic Unicorn that when I shut down Chromium the amount of memory being used dropped as shown by System Load Indicator. If I then switched to an already loaded Libreoffice with 2 or 3 documents opened, there was a noticeable slow response to mouse selection of text and the display of typed characters. It was as if Libreoffice had given up some memory and then needed to get it back. Whereas, if I switch between Libreoffice and Chromium there is no delay effect. 

 I see the same effect in Vivid Vervet. By the way, the Machine only has 1 GB of RAM and Swap is hardly used at all. So, it is not down to not having enough RAM. I see the system making good use of what is available to it.

Any efficiencies gained through improvements to the kernel will be available to all distributions using Linux.  

Regards.

---

