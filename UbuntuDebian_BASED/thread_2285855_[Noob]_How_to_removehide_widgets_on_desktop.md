---
title: "[Noob] How to remove/hide widgets on desktop"
date: 2015-07-08
forum: Ubuntu/Debian BASED
---

### Post by Albin_Pettersson on 2015-07-08
Hi!

I just installed Jessbuntu and there is a bar that displays CPU/RAM/HDD info and it is ALWAYS on top, can i hide, remove this bar?

---

### Post by kerry_s on 2015-07-08
lol, never heard of it till now.

open a terminal & run "killall conky" if it disappears, then all you need do is remove conky from startup.

---

### Post by PaulW2U on 2015-07-08
*Thread moved to **Ubuntu/Debian BASED**.* as anyone answering will probably be wondering what JessBuntu is. :)

---

### Post by ajgreeny on 2015-07-08
Does always on top mean that it is over any open windows?

If that is the case you can probably change the config file of conky (and it is definitely conky in Jessbuntu) if you know what file is used; the default is a hidden file in your home called .conkyrc.
You can possibly find the config file used from the startup command in the autostart list, but you may decide it is not worth the bother.

Be warned; if you do keep conky, it is a great time-waster, writing and re-writing the config file to get the display looking how you want, but it is also utterly fascinating to deal with.  Here's my current conky display, just as an example

---

