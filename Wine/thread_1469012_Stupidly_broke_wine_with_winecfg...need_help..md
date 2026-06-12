---
title: "Stupidly broke wine with winecfg...need help."
date: 2010-05-01
forum: Wine
---

### Post by DOS4dinner on 2010-05-01
So I was stupid enough to tell winecfg to disable a system critical dll (Half-asleep, I thought disable meant "disable the over-ride", not disable it from being called...don't really know why it was in the over ride area anyway)

Anywho, I can't run regedit, winecfg, or use any wine program until I somehow undo that dll disabling (the dll in question I believe is comctl32, if I remember right). Is there some way to do it manually by editing some cfg file? 

Thanks in advance.

EDIT: Problem solved thanks to jkxx.

---

### Post by jkxx on 2010-05-02
Yup, should be easy enough to do. Go into your wine folder (usually $HOME/.wine/) and open the file user.reg with your favorite editor.

Search for [Software\\Wine\\DllOverrides] - you'll find it has an entry for the dll you configured earlier. Just delete the line with that entry (it will look like "comctl32=native,builtin" or similar) and save the file.

You should be able to launch wine fine after this.

---

### Post by DOS4dinner on 2010-05-02
Just what I needed. Thanks!

---

