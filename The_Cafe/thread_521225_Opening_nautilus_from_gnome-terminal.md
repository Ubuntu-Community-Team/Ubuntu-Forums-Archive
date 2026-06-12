---
title: "Opening nautilus from gnome-terminal"
date: 2007-08-09
forum: The Cafe
---

### Post by Basurero on 2007-08-09
Hi, I'm wondering if it would be very complicated to do exactly the opposite of the "nautilus-open-terminal", which opens a terminal window in the current directory from Nautilus. I mean, opening a Nautilus window from gnome-terminal, with the current directory visible ("pwd").
I usually work in a gnome-terminal window and sometimes I just want to open a "visual" view of the current dir (usually to make a zip file of several files to email them).
Currently I do
```
# nautilus . &
```
but a right-click-menu item would be nice ;-)
Thanks in advance,
Basurero.

---

### Post by thelinuxguy on 2007-08-09
Would an alias serve your purpose?
```

alias n='nautilus . &'

```
or something similar. Then you can just type n to get your view quickly.

---

### Post by Basurero on 2007-08-10
Of course! I use aliases all the time ('l', 'll', 'la', 'lh', etc). It just hadn't occurred to me to use it for a graphical app.
Thanks.

---

