---
title: "A Nautilus plugin idea..."
date: 2008-03-07
forum: The Cafe
---

### Post by SZF2001 on 2008-03-07
I mean, if KDE can do it, why can't Nautilus see what pictures are being uploaded if you post one on a forum or something?

And I mean see them, as in a thumbnail. You get those normally if your just browsing around in the Nautilus File Manager, but when a website asks you to upload a picture you get no thumbnails, just a enormous list - then you have to go to Places -> Pictures to see what you want and... augh...

Or did I just miss something? I've been on Ubuntu since 5.04 (Breezy was it?) and I've just noticed that it's a pain in the butt.

---

### Post by mcduck on 2008-03-07
As I've understood the situation the problem is that while GTK has support for picture preview in the file selection dialog, it's up to programmers of every application to use that feature. And as Firefox developers don't use it, we get no picture preview in Firefox..

(Nautilus has nothing to do with this)

---

### Post by 23meg on 2008-03-07
Firefox 3 in Hardy has this feature.

---

### Post by bruce89 on 2008-03-07
> **23meg said:**
> Firefox 3 in Hardy has this feature.

Same goes for Epiphany.

GtkFileChoosers don't by default have a preview widget, so they have to be added manually. This is because some programs shouldn't preview certain types of file (such as GIMP not opening videos).

---

### Post by SZF2001 on 2008-03-07
> **23meg said:**
> Firefox 3 in Hardy has this feature.
That's actually awesome to know. Gives me a reason to upgrade, even if it is a small one...

---

