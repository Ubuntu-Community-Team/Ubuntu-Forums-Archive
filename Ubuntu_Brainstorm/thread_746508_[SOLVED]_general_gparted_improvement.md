---
title: "[SOLVED] general gparted improvement"
date: 2008-04-05
forum: Ubuntu Brainstorm
---

### Post by Zyphrexi on 2008-04-05
when resizing or performing operations, it would be better if there were a progress bar that actually changes. Right now it just jumps back and forth, 

especially for long operations, I have no way of knowing whether it's still running or hiccuped somewhere and isn't moving, since there's not *nearly* enough output.

something like the hashes '#' you see when doing some console stuff, or percentage, maybe to two decimal places for the heavy stuff. Just so there is some indication that it's working, and working correctly, that little bar jumping around tells me absolutely nothing.

---

### Post by smartboyathome on 2008-04-05
This should be told to GParted, not Ubuntu.

---

### Post by bruce89 on 2008-04-05
I'm not sure if the actual programs doing the stuff can report progress. If so, implement it.

---

### Post by Zyphrexi on 2008-04-05
meh, prolly right. but since when does gnome listen to the people? =P

but really, doesn't ubuntu usually modify the sources?

honestly I don't know how that works. I'll bug the gparted people though.

---

### Post by smartboyathome on 2008-04-05
> **Zyphrexi said:**
> meh, prolly right. but since when does gnome listen to the people? =P

but really, doesn't ubuntu usually modify the sources?

honestly I don't know how that works. I'll bug the gparted people though.

Not normally. The exception is the kernel, which I think has a few patches applied to it.

---

### Post by bruce89 on 2008-04-06
> **Zyphrexi said:**
> meh, prolly right. but since when does gnome listen to the people? =P
When you bug them, not the Ubuntu people.

[http://bugzilla.gnome.org/show_bug.cgi?id=467925](http://bugzilla.gnome.org/show_bug.cgi?id=467925) is what you're after.

---

### Post by Zyphrexi on 2008-04-06
yeah funny thing was, I realized that gparted was just a front end to pre-existing commands, and wondered about progress output. Thanks for the link, it answered my query.

though here's what I'm thinking, it should really spit out the output of the commands it runs, unfortunately I'm not motivated enough to make my own FE. :P

---

