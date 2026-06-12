---
title: "X / K / Ubuntu for an old 350Mhz laptop?"
date: 2006-12-11
forum: The Cafe
---

### Post by The Grum on 2006-12-11
A (computer savvy) friend is looking to try X/K/Ubuntu on his older laptop in place of XP. I dont have the full specs, but i know its around a 350Mhz system with 256Mb Ram. It will just be used for email and web browsing.

Has anyone had success with X/K/Ubuntu Edgy on a similar spec machine? Which one should I recommend? Will the Live CD work or would it be too much for the system? Should I give him Damn Small Linux instead :) ?

Any advice would be great. Thanks in advance.

---

### Post by kuja on 2006-12-11
They can all run on it, though, be sure to do a few speed tweaks to make it more bearable. (profile, prelink, at the least) I bet fluxbox would run well on it.

---

### Post by DigitalDuality on 2006-12-11
d

---

### Post by Stew2 on 2006-12-11
I would install the Xubuntu desktop in it. Otherwise it should run it fine, particularly for the uses you stated. I would probably use the Alternate install CD as most people seem to have less problems installing from it than the Live CD. My old 600X runs Ubuntu OK (a little slowly), it has 256 mb of ram as well. Unfortunately I could never get my Linksys wireless to work on it though so I had to leave Win2K on it. Hope this helps! :) 

Regards,
Stew2

---

### Post by The Grum on 2006-12-11
I guess I could start with Xubuntu Live, then Xubuntu alternate then Fluxbuntu (I didnt know that existed. Thanks, DigitalDuality!) if thats still not enough.

Thanks for the help.

---

### Post by ADT on 2006-12-11
Does it matter what version of ubuntu you install?
Say I installed the gnome version and then downloaded xfce and used it instead of the gnome window manager, wouldn't the operating system run the same as xbuntu does. ie using Ubuntu with xfce is the same as using Xubuntu.

---

### Post by K.Mandla on 2006-12-11
I'd start with Xubuntu, then move to an ultralight XFCE or Openbox (okay, okay ... or Fluxbox) setup. When it stops feeling sluggish, you'll have it just right. :)

---

### Post by PatrickMay16 on 2006-12-11
> **The Grum said:**
> A (computer savvy) friend is looking to try X/K/Ubuntu on his older laptop in place of XP. I dont have the full specs, but i know its around a 350Mhz system with 256Mb Ram. It will just be used for email and web browsing.

Has anyone had success with X/K/Ubuntu Edgy on a similar spec machine? Which one should I recommend? Will the Live CD work or would it be too much for the system? Should I give him Damn Small Linux instead :) ?

Any advice would be great. Thanks in advance.

That would run very well, if you'd do a "command line system" install with the alternate Dapper/Edgy CD, and then use aptitude/apt-get to install xserver-xorg, IceWM, and then install some light web browser like epiphany or Firefox 1.5. Turning off unused services will also help things along. (a tool in the repositories, sysv-rc-conf, is good for this)

Or if you want something easier, you could try Xubuntu.

I know this, because I myself have experience with using ubuntu on slower machines. Like my old Emachines, with a 733MHz processor and 185MB RAM.

Here is a screenshot.
[http://img179.imageshack.us/img179/9488/benisworldqwwert2yk9.png](http://img179.imageshack.us/img179/9488/benisworldqwwert2yk9.png)

So you see, with the right set up, Ubuntu will run very well on your friend's laptop.

---

