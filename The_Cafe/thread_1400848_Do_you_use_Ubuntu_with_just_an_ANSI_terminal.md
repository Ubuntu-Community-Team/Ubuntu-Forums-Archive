---
title: "Do you use Ubuntu with just an ANSI terminal?"
date: 2010-02-07
forum: The Cafe
---

### Post by yester64 on 2010-02-07
Hi,

I wonder if someone actually uses Linux just without any GUI. Or with ANSI terminal like you used to have on workstations.
Currently I use Gnome, but I want to see if i can also have the same applications running with just a terminal or ANSI terminal.

---

### Post by koenn on 2010-02-07
GUI apps, the ones you typically run in gnome, need bitmapped video output. The won't output to a text terminal - and they'll refuse to run if that's all you have.

You need to either find alternative, text-based programs, or have at least an X-server running. Framebuffer might work too, in some cases. 

If you search the forums, you may find some old threads of people who experimented with such setups.

---

### Post by Alexandre Putt on 2010-02-07
I used to work with Sun OS using a remote connection in a terminal window (with putty). I also used Linux on a very old PC without GUI, as it would be too slow. 

You can do a lot, but it depends on your needs. Email (with pine), compilers, editors (vi, Emacs), LaTeX, R, octave all work fine.

---

