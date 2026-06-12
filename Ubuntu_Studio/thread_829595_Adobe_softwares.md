---
title: "Adobe softwares"
date: 2008-06-14
forum: Ubuntu Studio
---

### Post by sayian_z on 2008-06-14
can I install adobe softwares on ubuntu? and how

---

### Post by tamoneya on 2008-06-14
recently wine has made a lot of improvements.  They have CS2 working under wine and it shouldnt be far from CS3.

[www.winehq.com](www.winehq.com)

---

### Post by FakeOutdoorsman on 2008-06-15
I currently use Photoshop CS 2 in a virtualized Windows install using VirtualBox.  It is much more stable then Wine ever was for me, but I haven't used Wine for almost a year.

---

### Post by Ralphie on 2008-06-15
Every photoshop from CS2 and below run well in wine.

If your system is good enough, you can install VirtualBox, install windows xp there, and then run any Adobe application that you want.

But like I said, you should have a quick computer, because you are basically running windows and ubuntu at the same time using the virtualbox method.

---

### Post by rylleman on 2008-06-16
Photoshop CS2 and below runs ok in wine (starting a few versions ago), some operations even runs faster than in native windows (as I noticed it anyway). There are however some bugs left, especially if you're running some graphics compositor. Most of the bugs however are minor and affects only the appearance of the app.
I use Photoshop running in wine for production purposes and I think it's fully workable.
When it comes to After effects, Premiere and other more craving softwares they run less ok in Virtualbox (not at all in wine).
They don't have a lot of bugs running but they need so much computer power if you want to work with larger images, more complex comps etc. so they become very sluggish to run.
Premiere, in my findings, starts to seriously bug out if you have more than a a few hundred pieces of images, shots or audio and breaks the network connection, refuses to find material etc.
Flash do run well in virtualbox. I haven't found any major issues when using it.

Also, both wine and virtualbox are only 32-bit, which mean you can only assign about 3gigs of memory to them.

So my advise would be to run Photoshop in wine if you like but dual boot into windows xp if you need to edit/comp. video.

---

