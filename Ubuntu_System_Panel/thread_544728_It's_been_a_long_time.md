---
title: "It's been a long time"
date: 2007-09-06
forum: Ubuntu System Panel
---

### Post by ayoli on 2007-09-06
hey,
I haven't use USP for a long time, actually since i 've started with feisty, just wanted to try other solutions and wait for big changes in  USP.
So here I m back now, and just want to know how USP goes.
This forum is a bit unclear, a sticky with versions/screenshots would be cool.
What is actual version ? and what featurews come with it ? how to install it (ie: is there a feisty deb ?)

---

### Post by delfick on 2007-09-06
hello

svn is the latest of everything (instructions found here [http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list))

unfortunately as far as development is concerned, that has slowed down quite considerably due to the time constraints experienced by Chanders and Malac (the two main devs of the project)

.....

---

### Post by ayoli on 2007-09-07
thanks delfick for these info I'll give a try to this USP-svn :)

---

### Post by Malac on 2007-09-08
Thanks for fielding this one delfick.
Hi ayoli, I have been thinking about making up a .deb file of the latest SVN as the beta development on this version (USP2) seems to have reached a point where no bugs are being reported and it is stable (on Edgy and Feisty at least).

I would like chanders okay as it's really chanders whose project it is. If there are no objections I could post one on this forum. Up until now I have been pointing everyone at the SVN install instructions as delfick says.

Hope this helps.

---

### Post by ayoli on 2007-09-08
hey Malac :)
It was really easy to install and I love the tab feature.
But, I have a bug to report : USP opens often behind other windows which is quite annoying for a "menu".
If that can help I m running feisty with compiz fusion on a HP laptop with an intel graphics chipset.

---

### Post by delfick on 2007-09-08
> Thanks for fielding this one delfick.

no probs :D

> **ayoli said:**
> hey Malac :)
It was really easy to install and I love the tab feature.
But, I have a bug to report : USP opens often behind other windows which is quite annoying for a "menu".
If that can help I m running feisty with compiz fusion on a HP laptop with an intel graphics chipset.

the problem is the window type of the usp........

for some reason you can't set it to be front with the window rules plugin

but if you change line 9 in /usr/share/usp/usp2.glade

to

```
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_MENU</property>
```

then it stays in front

only downside is that it then appears in the gnome panel as another app...

---

### Post by ayoli on 2007-09-09
> **delfick said:**
> no probs :D



the problem is the window type of the usp........

for some reason you can't set it to be front with the window rules plugin

but if you change line 9 in /usr/share/usp/usp2.glade

to

```
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_MENU</property>
```

then it stays in front

only downside is that it then appears in the gnome panel as another app...

I tried that, unfortunately, it freezes my panel and when I try to reload my panel by killing it or logout/login I got an erreor where gnome panel asks me if I want to remove this applet from my conf.

---

### Post by 4tro on 2007-09-10
this looks like plain old focus prevention acting up,
ccsm -> general options -> focus & raise behaviour
empty the field of "focus prevention windows"
that should fix it for now, let's hope a better solution can be found

---

