---
title: "The Qt port of Firefox..."
date: 2008-10-15
forum: The Cafe
---

### Post by xeriouxi on 2008-10-15
Hi!

I read that Nokia and Mozilla are porting Firefox to Qt, but this was announced back in August. Does anyone know of any updated news on this project? All I've seen so far is one screenshot of it...

Whilst on the topic, are there any KDE users who are really looking forward to this? First VLC, now Firefox... I wonder what other projects might port themself over to Qt sometime in the future... =)

---

### Post by mips on 2008-10-16
It's going to take a bit of time. A kdemod forums member got it to compile and run on Arch. Apparently it is stable but looks like crap right now.

[http://kdemod.ath.cx/bbs/viewtopic.php?id=983](http://kdemod.ath.cx/bbs/viewtopic.php?id=983)
[http://img135.imageshack.us/my.php?image=firefoxqtxu9.jpg](http://img135.imageshack.us/my.php?image=firefoxqtxu9.jpg)  (Screenshot)
[http://browser.garage.maemo.org/news/10/](http://browser.garage.maemo.org/news/10/)

Best to read the thread.

I love the fact that so many apps are moving to qt4.

---

### Post by Canis familiaris on 2008-10-16
> **mips said:**
> 
i love the fact that so many apps are moving to qt4.
+1

---

### Post by Arathorn on 2008-10-16
Well, Firefox isn't moving. The QT port is just an unofficial side project. But the fewer GTK programs on my computer the better.

---

### Post by steeleyuk on 2008-10-16
Firefox isn't GTK, it just mimics it. It actually uses XUL for its interface. AFAIK.

---

### Post by Canis familiaris on 2008-10-16
> **steeleyuk said:**
> Firefox isn't GTK, it just mimics it AFAIK.

Yes.

---

### Post by GeneralZod on 2008-10-16
> **steeleyuk said:**
> Firefox isn't GTK, it just mimics it. It actually uses XUL for its interface. AFAIK.

Yes, and to be more clear: to the best of my understanding, Firefox indeed uses XUL for its interface, but XUL has many "back-ends" that map XUL interface elements to their "native" counterparts.  Backends exist for Windows's and Mac OS X's native widgets and for the GTK toolkit on X11.  The Qt4 "port" would simply be another backend for the XUL interface to optionally use.

"Mimicking" GTK isn't quite accurate as the X11 backend does indeed use actual GTK elements (rather than just pretending to), but most of the work is done inside XUL with GTK being responsible for the "last mile", as it were.

---

### Post by Erunno on 2008-10-27
> **GeneralZod said:**
> Yes, and to be more clear: to the best of my understanding, Firefox indeed uses XUL for its interface, but XUL has many "back-ends" that map XUL interface elements to their "native" counterparts.  Backends exist for Windows's and Mac OS X's native widgets and for the GTK toolkit on X11.  The Qt4 "port" would simply be another backend for the XUL interface to optionally use.

"Mimicking" GTK isn't quite accurate as the X11 backend does indeed use actual GTK elements (rather than just pretending to), but most of the work is done inside XUL with GTK being responsible for the "last mile", as it were.

Actually, Firefox uses Cairo for drawing both its XUL interface as well as the web content since Firefox 3 and Cairo in turn has backends for native platfom-specific technologies. So, for the sake of adding another abstraction layer, wouldn't it benefit more applications if a Qt backend were written for Cairo instead of porting XUL directly to Qt?

[/threadnecromancy]

EDIT: After a short sleep I think I'm confusing things. As far as I know Qt can already use Cairo as a paint device instead of Arthur.

---

