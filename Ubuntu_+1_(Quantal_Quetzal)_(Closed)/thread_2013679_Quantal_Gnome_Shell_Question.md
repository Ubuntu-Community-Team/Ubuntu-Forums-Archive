---
title: "Quantal Gnome Shell Question:"
date: 2012-07-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-07-01
i just did a clean install this morning and decided to give gnome shell a shot.so far so good but encountered a little problem,i want to bring the close button from the right to the left.i don't even know if this is possible in gnome shell,i don't remember if this can be done.i tried gconf but it won't do it,in unity it is but not in gnome shell.if any one has the experince please share it.thank you ;)

---

### Post by jfernyhough on 2012-07-01
You need to use dconf-editor rather than gconf-editor.

---

### Post by jbicha on 2012-07-01
That's how I have mine set. Because I go back and forth between Unity & GNOME Shell, it's nice to have the close button stay consistent.

Install dconf-tools
Run dconf-editor
Look for org.gnome.shell.overrides
Change button-layout to **close:**

---

### Post by kuvanito on 2012-07-01
jbicha i am having one on your name (Heineken) THANK YOU! ;)

---

### Post by Dlambert on 2012-07-02
Please mark thread as solved.

---

