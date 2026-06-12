---
title: "JAMin not launching"
date: 2011-02-05
forum: Ubuntu Studio
---

### Post by leisuresuitgreg on 2011-02-05
Hi all,

JAMin is failing to launch after starting jack. Output below

```
greg@GregUb:~$ jamin
jamin 0.97.14
(C) 2003-2005 J. Depner, S. Harris, J. O'Quin, R. Parker and P. Shirkey
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.
Cannot lock down memory area (Cannot allocate memory)
Cannot find plugin 'foo_limiter.so'

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(jamin:2622): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Started OSC server thread at osc.udp://GregUb:4444/
Segmentation fault
```

Any ideas plaase?

Greg

---

### Post by Pablo_F on 2011-02-06
Hi, 

What are the outputs of 

**ulimit -r -l**

**free**

**du -a /dev/shm**

?

---

### Post by leisuresuitgreg on 2011-02-12
Hi Pablo,

Thanks for the follow up, but I decided to do a full rebuild, and switch to KXStudio (prefer KDE). Works fine now, and I can master again.

Cheers

---

