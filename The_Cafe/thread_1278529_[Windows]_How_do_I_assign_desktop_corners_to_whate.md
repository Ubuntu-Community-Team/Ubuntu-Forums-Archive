---
title: "[Windows] How do I assign desktop corners to *whatever*"
date: 2009-09-29
forum: The Cafe
---

### Post by raul_ on 2009-09-29
Hello there.
I've been trying to do a very simple thing:
assign my top left corner of the desktop to the key combination ctrl+alt+tab (to "emulate" the show windows of Compiz and Kwin)

It seems it's impossible!! 
There are programs to assign my corners to everything BUT a key combination, programs that do alt+tab but react to the whole edge of the screen and do autoscrolling (stupid idea), I even found an application that could do Alt+tab, but that only changes the window, I want the dialog to stay open!

So, my question is: is there anyway to assign a key combination to a corner? Or is there anyway to write something similar to a bash script that runs the given key combination (because I think I can assign corners to files/programs, so that would be a work around)

Thanks :)

---

### Post by tom66 on 2009-09-29
The open source way would be to write your own program to do what you want. Python supports Win32, maybe it supports Alt-Tab (or creating a key combination) and cursor position.

---

### Post by raul_ on 2009-09-29
> **tom66 said:**
> The open source way would be to write your own program to do what you want. Python supports Win32, maybe it supports Alt-Tab (or creating a key combination) and cursor position.

I totally forgot about python. It has to be possible to call keyboard events.
Thanks! I'll try doing it :)

---

### Post by raul_ on 2009-09-29
Actually, 2 lines in VB will do the trick:

```
set WshShell = WScript.CreateObject("WScript.Shell")
WshShell.SendKeys "+(^%{TAB})"
```

Thanks for the suggestion ;)

EDIT: I forgot to say that I'm using a (free) program called Hot Corners to assign my top left corner to the script I created

---

