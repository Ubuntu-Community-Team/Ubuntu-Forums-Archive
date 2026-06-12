---
title: "Error from u1sdtool: (u1sdtool:3105)"
date: 2011-11-09
forum: Ubuntu One (CLOSED)
---

### Post by sirajperson on 2011-11-09
I am getting this every time I run the u1sdtool:

```

u1sdtool 

(u1sdtool:3105): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:3105): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:3105): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(u1sdtool:3105): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Usage: u1sdtool [option]

```

Anyone have any idea what's going on here?

---

### Post by sirajperson on 2011-11-09
ok, I figured out what's going on.... or at least I figured out how to fix the error message :)
It looks from the error message that 11.10 doesn't come pre-installed with the correct gtk-engine. To install it we can run:
```

sudo apt-get install gtk2-engines-pixbuf

```

That takes care of that error message.

---

