---
title: "Reduce tty Count"
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by ghindo on 2008-05-16
As best as I can figure out, Ubuntu currently comes configured to launch 6 tty windows at login.  This seems a bit excessive, as most users will never use *one*, let alone *six*.  If Ubuntu devs could trim the default tty count down to one or two, that would mean fewer processes running, a lighter system, and more simplicity.

Is there any reason this would be a bad idea?

---

### Post by smartboyathome on 2008-05-16
I can think of one. One TTY can report X problems, one report kernel problems (indeed, this is how mine is set up), and one for updating/upgrading/installing (so it doesn't tie up X).

---

### Post by CrazyGuy123 on 2008-05-16
How much memory do we use/waste having 6 tty's with a login prompt on each?

Do we waste the memory even before the Alt+Fx shortcut is pressed?

Does starting the tty's delay the boot process?

Since memory may be shared between tty's, you'll probably get the most accurate measure looking at total memory consumption after a clean boot with the tty's both enabled and disabled.

I suggest if the total cost is more than 1MB per tty or 0.1s on boot time we should consider slimming down.

---

