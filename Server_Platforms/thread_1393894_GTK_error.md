---
title: "GTK error"
date: 2010-01-29
forum: Server Platforms
---

### Post by MethodsMan on 2010-01-29
Greetings all,
I have a ubuntu LTS server running and we are trying to plot some things with matplotlib in python.  Anytime I try this or say 'import gtk' I get a:

```
/usr/lib/python2.5/site-packages/matplotlib/backends/backend_gtk.py:40: GtkWarning: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed
  cursors.MOVE          : gdk.Cursor(gdk.FLEUR),

```

I am running this as strictly a command line machine for speed.  At first I thought since I was logged in through SSH that could be the issue so I went to the terminal and still get the same error.  Any help would be greatly appreciated as I would like to get this machine producing the graphics as quickly as I can.
-JL

---

