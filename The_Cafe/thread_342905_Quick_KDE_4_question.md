---
title: "Quick KDE 4 question"
date: 2007-01-20
forum: The Cafe
---

### Post by darkhatter on 2007-01-20
Kde has the built in Mac OS X style menu, I believe its called deskbar. With kde 4 is that going to work with non kde apps?

P.S. new similies
:guitar: ):P :lolflag:

---

### Post by mostwanted on 2007-01-20
> **darkhatter said:**
> Kde has the built in Mac OS X style menu, I believe its called deskbar. With kde 4 is that going to work with non kde apps?

P.S. new similies
:guitar: ):P :lolflag:

No. It's a toolkit issue.

Gtk+ (what Gnome uses) is different from Qt (what KDE uses). I assume Qt has some way of defining the main menu bar of a program, which is how the Mac OS X menu style hack works. Gtk+ menu bars are just regular widgets with no special status.

---

### Post by darkhatter on 2007-01-20
:( .....thanks anyway

---

### Post by GeneralZod on 2007-01-20
> **darkhatter said:**
> :( .....thanks anyway

I'm sure one of the members of this forum wrote a patch that gives GTK the same capability, but I can't remember who it was :/

---

### Post by darkhatter on 2007-01-20
> **GeneralZod said:**
> I'm sure one of the members of this forum wrote a patch that gives GTK the same capability, but I can't remember who it was :/

if I applied that patch would all my gtk programs all work with that. and is there any patch for java apps, and the mozilla toolkit

---

### Post by banjobacon on 2007-01-20
Here's the thread for the GTK menu bar: [http://www.ubuntuforums.org/showthread.php?t=241868](http://www.ubuntuforums.org/showthread.php?t=241868)

I haven't been following the progress, but it's 30 pages long, so I guess there must be some people playing with it and installing it on their systems. I don't know if it's compatible with KDE at this point.

---

