---
title: "Left side gap"
date: 2007-04-05
forum: Ubuntu System Panel
---

### Post by phin on 2007-04-05
Wondering if there would be a way to remove the gap between the left border and, say, the applications menu.

right now there is about a 10px gap, that i would like to be able to remove, so the favorite items are more butted up.

the applications seem to butt up just fine, though.

---

### Post by Malac on 2007-04-05
> **phin said:**
> Wondering if there would be a way to remove the gap between the left border and, say, the applications menu.

right now there is about a 10px gap, that i would like to be able to remove, so the favorite items are more butted up.

the applications seem to butt up just fine, though.
Try opening applications.py in gedit and replace any occurence of :
```
MakeAButton( self.width-10,
```with :
```
MakeAButton( self.width,
```or any offset you like. See if that sorts it.

---

