---
title: "Internet Explorer for Ubuntu?"
date: 2006-03-27
forum: The Cafe
---

### Post by K.Mandla on 2006-03-27
Before you flame me, hear me out.

I'm finding out the hard way that Internet Explorer doesn't display Web pages built with CSS properly. As a result, I'm forced to insert some weirdo hacks into CSS files to get them to show up the same way they might appear in Firefox, Mozilla, etc., etc.

But I do most of this stuff on an Ubuntu machine, and so I don't have a way of double-checking the output in IE.

Short of building an entire Windows system just to use an inferior browser, does anyone know of a way to see if IE4.0, IE5.0, IE5.5 and IE6.0 are confused enough to show things the way I want?

Thanks in advance.

P.S.: Nothing would please me more than a little script that says, "You're using IE. Go get a proper browser", but the boss says that's a no-no. :(

---

### Post by BWF89 on 2006-03-27
It is possible because I've seen screenshots of it before.

---

### Post by lordofkhemenu on 2006-03-27
[quote=K.Mandla]Before you flame me, hear me out.

I'm finding out the hard way that Internet Explorer doesn't display Web pages built with CSS properly. As a result, I'm forced to insert some weirdo hacks into CSS files to get them to show up the same way they might appear in Firefox, Mozilla, etc., etc.

But I do most of this stuff on an Ubuntu machine, and so I don't have a way of double-checking the output in IE.

Short of building an entire Windows system just to use an inferior browser, does anyone know of a way to see if IE4.0, IE5.0, IE5.5 and IE6.0 are confused enough to show things the way I want?

Thanks in advance.

P.S.: Nothing would please me more than a little script that says, "You're using IE. Go get a proper browser", but the boss says that's a no-no. :([/quote] If IE 5.5 will suffice, checkout the WineHQ app database page for IE 5.5:
[http://appdb.winehq.com/appview.php?versionId=240]("http://appdb.winehq.com/appview.php?versionId=240")
IE6 is hopeless to install.
Haven't tried it myself, as I don't much care if IE can view my pages or not. When people complain about it, I tell them as much. And to use  Firefox. :)

---

### Post by mstlyevil on 2006-03-27
[QUOTE=K.Mandla]Before you flame me, hear me out.

I'm finding out the hard way that Internet Explorer doesn't display Web pages built with CSS properly. As a result, I'm forced to insert some weirdo hacks into CSS files to get them to show up the same way they might appear in Firefox, Mozilla, etc., etc.

But I do most of this stuff on an Ubuntu machine, and so I don't have a way of double-checking the output in IE.

Short of building an entire Windows system just to use an inferior browser, does anyone know of a way to see if IE4.0, IE5.0, IE5.5 and IE6.0 are confused enough to show things the way I want?

Thanks in advance.

P.S.: Nothing would please me more than a little script that says, "You're using IE. Go get a proper browser", but the boss says that's a no-no. :([/QUOTE]

You can install them using Wine. I personally have never done it but there are a number of people here that have done so.

---

### Post by IYY on 2006-03-27
From what I understand, installing IE is not too difficult. The difficult part is getting it to display these annoying "IE-only" sites that require ActiveX and whatnot. But I guess since you don't need that, you're set.

---

### Post by K.Mandla on 2006-03-27
Thanks. I'll see if I can get something going here. I don't know why it didn't dawn on me to build one of those under Wine, but I don't even use IE when I have to use Windows, so it kind of figures.

---

### Post by LinuxKid on 2006-03-27
is it possible to use the ie tab extension for firefox, or does that require you to have it installed?

---

### Post by dabear on 2006-03-27
LinuxKid: I tried once, but it didn't work. Maybe if you edit some parts of the plugin yourself, but I dunno if that works either

Thread starter:
IE runs pretty darn good under crossover and/or wine I must say. With cx it's just point, click,click and click to install it, much easier than with plain old wine :)
Just to show it is possible:

---

### Post by JimmyJazz on 2006-03-27
[http://jimmyjazz.homeip.net:808/ieinubuntu.png]("http://jimmyjazz.homeip.net:808/ieinubuntu.png")

heres a screen of me using IE with crossover, works perfectly (as good as IE can work at least).

---

### Post by Stealth on 2006-03-27
IE6 can work under Wine (or better yet in Crossover) but if you don't have Crossover, check out [this tutorial]("http://frankscorner.org/index.php?p=ie6") to see how you can install IE6 under Wine...

---

### Post by ticlo on 2006-03-27
This thing might help: [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by joaoeb on 2006-03-27
Run this 2 times (don't know why it fails in ter first run).

[http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

---

### Post by nanotube on 2006-03-27
i have found that ies4linux, as the previous poster mentioned, works wonderfully. there is even a tutorial on how to get it done, here: 
[http://ubuntuforums.org/showthread.php?t=132508](http://ubuntuforums.org/showthread.php?t=132508)
(and yes, i, too, had to run it twice, for some reason. :) ).

---

