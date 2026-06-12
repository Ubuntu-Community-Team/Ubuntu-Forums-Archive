---
title: "Galago UltraPro - Black Rectangles in Firefox in 13.10"
date: 2013-11-04
forum: System76 Support
---

### Post by kiki5769 on 2013-11-04
Hello!

I recently bought a Galago UltraPro and have been loving the hell out of it. However, ever since I upgraded to Ubuntu GNOME 13.10, I have been experiencing black rectangles popping up in Firefox. I imagine this has to do with something specific to this model, since my older Thinkpad exhibits no such behavior. These rectangles show up only in the websites themselves, and seem to appear/dissappear randomly as I scroll up and down within any given web page.

Has anyone around here encountered this problem or knows of a solution? It's not a dealbreaker, but it can be very distracting while browsing the web.

---

### Post by scoodlebop on 2013-11-04
I'm fairly certain it's a *Haswell graphics* issue. Other Haswell machines also have this. Intel has been...well, pretty lousy...with their drivers for both graphics and wireless this last year. I'm not exactly sure where the issue is -- kernel, mesa, whatever -- but you could try upgrading those packages to see if the blocks go away (obviously, do a backup, first, in case you bork your install and need to reinstall).

---

### Post by clarkaddison on 2013-11-05
Yeah I've been watching this one here [https://bugs.freedesktop.org/show_bug.cgi?id=68410](https://bugs.freedesktop.org/show_bug.cgi?id=68410)

---

