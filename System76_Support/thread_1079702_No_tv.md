---
title: "No tv"
date: 2009-02-24
forum: System76 Support
---

### Post by byebyebill1 on 2009-02-24
cant see desktop on my tv. tv sees connection, but no picture. works a-ok with my eepc 900. (810).tried all fn keys.

model gazp5 810 64

   please keep it simple, old newbie!


      glenn

---

### Post by thomasaaron on 2009-02-24
Have you *ever* been able to see the desktop on your tv?

Try going to a terminal and entering this command...

sudo nvidia-settings


...and detecting/enabling your tv from there. Does that work?

---

### Post by byebyebill1 on 2009-02-24
this is my first try. got into settings, but i dont know what to do? do i need to have tv plugged in first?


    tia, glenn

---

### Post by thomasaaron on 2009-02-24
Yes, plug in your tv.
Then run... sudo nvidia-settings
Then click "Detect Displays" and see if it is detected.
Then you should be able to Configure it (Clone mode, set resolution, etc...).

I've never tested one on a TV. But I would think that procedure should work fine.

---

### Post by byebyebill1 on 2009-02-24
fixed! once again, ur the man :-) never thought my g force 8400m gs 256 would do such a good job on my hdtv 46" lcd.
 thanks so much for your help.


      glenn

---

### Post by thomasaaron on 2009-02-24
Even a blind squirrel finds an acorn once in a while. :lolflag:

---

