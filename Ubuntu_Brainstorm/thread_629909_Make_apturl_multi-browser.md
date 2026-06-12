---
title: "Make apturl multi-browser"
date: 2007-12-02
forum: Ubuntu Brainstorm
---

### Post by smartboyathome on 2007-12-02
Right now, apturl only works with Firefox 2. I propose that Apturl be ported to FF3, and eventually to other web browsers.

This extention does a great deal for helping people install stuff, since it allows you to install stuff from the repos without having to tell them where synaptic is, and having to confuse them.

---

### Post by DizzyTech on 2007-12-02
You're absolutely right.  I propose that FF3 and Epiphany be placed on priority, with Konqueror next in line.  Ubufox would also be nice in Epiphany.

---

### Post by smartboyathome on 2007-12-02
I was thinking more along the lines of FF3 first, then Opera (since it IS the second-most used browser and also cross platform), then Epiphany and Konqueror. But your way works too. I think it is a plugin and not an addon, too, so if I can find the file, I might be able to get it to work with FF3.

---

### Post by CarpKing on 2007-12-04
Doesn't it already work in Epiphany?  I guess I've never actually installed something that way, but I've clicked an apt link and had it ask for my password to install something.  Of course that might only work in Epiphany with Gecko, in which case it should be ported to work with Webkit too.

---

### Post by maybeway36 on 2007-12-04
No clue how Opera would work, seeing as it's closed-source. Konqueror would be pretty easy to implement, though, with KIO and adept-batch.

---

### Post by smartboyathome on 2007-12-04
> **CarpKing said:**
> Doesn't it already work in Epiphany?  I guess I've never actually installed something that way, but I've clicked an apt link and had it ask for my password to install something.  Of course that might only work in Epiphany with Gecko, in which case it should be ported to work with Webkit too.

I don't know why it would, since it doesn't work with FF3. Maybe it is only installed on Gecko 1.9.

Also, I thought this was a plugin, maybe I was wrong.

---

### Post by DizzyTech on 2007-12-04
While I'm not in Ubuntu right now (I just got my new laptop and am defragging Vista), I believe the apturl package for Firefox just tweaks the handler settings to launch a plugin.

In the case of Ubufox, it just seems to be an integrated wrapper for Synaptic (or Add/Remove).

---

### Post by smartboyathome on 2007-12-04
Ok, so technically it "can" be done for Opera, but it wouldn't be redistributable?

---

### Post by smartboyathome on 2008-01-21
By the way, thanks to Rui Pais, we now can use apturl with Opera and FF3. Would it be possible to impliment these during the install of the program?

btw, here is the link to the howto: [http://cafelinux.org/forum/index.php/topic,972.0.html](http://cafelinux.org/forum/index.php/topic,972.0.html)

---

