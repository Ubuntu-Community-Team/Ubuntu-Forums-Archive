---
title: "Dir-File-Tree System Manager &amp; gzip"
date: 2015-03-16
forum: Ubuntu Dev Link Forum
---

### Post by oli7 on 2015-03-16
Hi, all:

when run lixdfmgr ( a light-weight GUI system management tool based on Dir-File-Tree Browser) on a terminal and call gnome-open to un-zip a zipped package, always get messages as following:

(file-roller:3877): Gtk-CRITICAL **: IA__gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(file-roller:3877): Gtk-CRITICAL **: gtk_box_pack: assertion `child->parent == NULL' failed

(file-roller:3877): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkFrame, but as a GtkBin subclass a GtkFrame can only contain one widget at a time; it already contains a widget of type GtkHBox

Is it caused by this lixdfmgr or file-roller?

yours
Li
[https://sites.google.com/site/firebirdarchitect/Home/other_prgs/lixdfmgr](https://sites.google.com/site/firebirdarchitect/Home/other_prgs/lixdfmgr)

---

