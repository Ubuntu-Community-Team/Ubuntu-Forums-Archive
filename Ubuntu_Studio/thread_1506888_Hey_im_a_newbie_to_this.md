---
title: "Hey im a newbie to this"
date: 2010-06-10
forum: Ubuntu Studio
---

### Post by dothdew88 on 2010-06-10
Hello, as the title states im a newbie to Ubuntu Studio. I have played around with normal Ubuntu in the past and loved it. However I seem to be having some problems finding where to find what I installed on my hard drive during the initial installation. I was supposed to have installed a 3D editing software. Its not on here. There actually isnt really any type of editing software at all on here. How do I get the "studio" part of this thing?
Any advice or guidance would be very much appreciated!

---

### Post by Breambutt on 2010-06-10
Copypasta this into terminal:

```
sudo apt-get install ubuntustudio-graphics
```

It's a 370MB download and unpacks 828MB more, so you might as well look around for what you actually might use and need since you already got this far without. Of course curiosity is a good thing for creative people.

[http://packages.ubuntu.com/lucid/ubuntustudio-graphics](http://packages.ubuntu.com/lucid/ubuntustudio-graphics)

There's a list of contents and you can install a selected few with *sudo apt-get install [package name]*. Audio suite and other default Ubuntu Studio stuff in the side panel on the right.

You'll find them in Main Menu under Sound & Video, new sub-folders Audio Production and Video Production. Graphics stuff obviously goes into Graphics.

Don't forget you can get the regular Ubuntu Add Software (or what's it called) thingie with *sudo apt-get install software-center*, it's just not installed by default.

Sorry it turned out like a "for dummies" guide, didn't first notice you'd been fiddling around with regular Ubuntu. ;( I think Studio is most useful for people who use realtime effects or need low latency for whatever reason, which visual artists usually don't (unless I'm mistaken). Well, at least you have a better looking desktop theme now.

---

### Post by dothdew88 on 2010-06-11
Thank you so much! That nailed it for me thanks again!

---

