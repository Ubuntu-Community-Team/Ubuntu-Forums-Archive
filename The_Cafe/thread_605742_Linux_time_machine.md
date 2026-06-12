---
title: "Linux time machine"
date: 2007-11-07
forum: The Cafe
---

### Post by p_quarles on 2007-11-07
Just saw this on Slashdot; a python script that gives you a GUI front end to rsync that works much like the Mac OS X 10.5 Time Machine.
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by init1 on 2007-11-07
Interesting. I'll consider that.

---

### Post by p_quarles on 2007-11-07
Yeah, it's not terribly fancy, but I'm thinking it might be a good response to the numerous questions about automated backup tools. 

Also, after encountering a parsing error, I discovered in the project's discussion section that a small tweak is necessary for Gutsy 64-bit. Insert the following at line 648:
```
def show_prefs_dialog(self):
            prefs_gui(self)
```
Right before "def hide_window ...". Python is sensitive to indentations, so make sure the indentation in this addition matches that of the previous routine.

---

