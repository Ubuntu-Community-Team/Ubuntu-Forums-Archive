---
title: "Wacom Bamboo in 12.04 not working"
date: 2012-06-28
forum: Ubuntu Studio
---

### Post by themuseman on 2012-06-28
[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]  I installed Ubuntu Studio 12.04 several weeks ago ... gradually working through the bumps to get everything working. Now I can focus on my Wacom pen and tablet, which is not working. [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] I get no indication that it is being recognized in Inkscape or Mypaint. Here are my system details:

Ubuntu Studio 64, kernel 3.2.0-23-lowlatency
Wacom Bamboo Create pen and tablet, CTH-670

Where do I start to get the tablet and pen working? Your help is greatly appreciated.

themuseman

---

### Post by Favux on 2012-06-28
Hi themuseman,

Support for your third generation BambooPT isn't available until the 3.3 kernel.  So you need to backport the 3.3 third gen support by using a recent input-wacom to get a wacom.ko that supports your model.  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

Either compile it as in part I. or use Lekenstyn's PPA.

---

### Post by themuseman on 2012-06-28
Favux - thanks for the reply,

I'm technically experienced, but still getting my feet wet in Ubuntu/Linux, so I hope I don't try your patience.

[SIZE=2]I'm [/SIZE][SIZE=2]  guessing the later drivers, the input-wacom-0.13.0's wacom.ko, would be better, so I think that's the route I want to try. Do I need to do just Part I, or both Part I and Part II?

themuseman
[/SIZE]

---

### Post by Favux on 2012-06-28
Yes, input-wacom-0.13.0 should be good.

The Precise default xf86-input-wacom-0.14.0 should be fine.  But it shouldn't hurt anything to update.

---

### Post by themuseman on 2012-06-29
Favux,

When I do uname -r, here's what is returned:

~$ uname -r
3.2.0-23-lowlatency

1. Does this indicate that the kernel is rt? (Is rt and low latency the same when referring to the kernel?)

2. One other question is this: I am running the 64 bit version of Ubuntu. Does that matter for this update?

themuseman

---

### Post by Favux on 2012-06-29
No, 32 or 64-bit shouldn't have any effect.  The instructions are the same.
> ~$ uname -r
3.2.0-23-lowlatency

1. Does this indicate that the kernel is rt? (Is rt and low latency the same when referring to the kernel?)
Good question.  It looks like for the headers line you want to use:
```
sudo apt-get install linux-headers-lowlatency
```
Looks like Studio's new equivalent to the rt (real time) kernel.

---

### Post by themuseman on 2012-07-02
I installed the  input-wacom-0.13.0 driver. The pen and tablet seem to be working. I will do more testing, but I'm optimistic.

Thanks,

themuseman

---

