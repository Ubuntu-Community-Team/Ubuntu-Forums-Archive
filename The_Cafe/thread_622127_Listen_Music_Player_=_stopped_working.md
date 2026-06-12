---
title: "Listen Music Player = stopped working"
date: 2007-11-24
forum: The Cafe
---

### Post by jack handy on 2007-11-24
hey, 

i've been using Listen for a while now, but last night i went to start it up and it didnt get past the "Starting Listen" phase.  i tried reinstalling and still no dice. 

anyone have any idea what i could do to get it back?

edit:   this is what i get when i try to launch it through a terminal window:

```

/usr/lib/listen/stock.py:135: GtkWarning: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
  try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
/usr/lib/listen/stock.py:135: Warning: g_object_ref: assertion `G_IS_OBJECT (object)' failed
  try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 218, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 119, in __init__
    stock.stock_init()
  File "/usr/lib/listen/stock.py", line 135, in stock_init
    try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
TypeError: pixbuf should be a GdkPixbuf

```

---

### Post by jack handy on 2007-11-24
the genius that i am figured out that it was because of my icons.  somehow incompatible.  :lolflag::guitar::popcorn:

---

