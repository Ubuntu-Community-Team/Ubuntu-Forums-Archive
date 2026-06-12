---
title: "Problem in GIMP"
date: 2013-02-01
forum: Ubuntu Development Version
---

### Post by fantab on 2013-02-01
Anybody else is having problems with images in GIMP 2.8 like those in the screenshot below?

I suspect it be a bug in python 2.7.3.10 as reported [**HERE**]("https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/962639"), but I could be wrong... 

Please confirm and post any solutions or workarounds.

Thanks...

**EDIT**: When I use terminal to open an image I get:

```
$ gimp ~/Pictures/23.jpg

(gimp:4196): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed
While parsing XMP metadata:
Error: No XMP packet found

(gimp:4196): GLib-GObject-WARNING **: invalid cast from `GimpView' to `GtkImage'

(gimp:4196): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed
```

But I guess it has nothing to do with the broken image...

---

### Post by jfernyhough on 2013-02-01
I also have that issue. I assumed it was due to fglrx being fglrx. I'll have a play with the GIMP settings and see if there's a hardware acceleration option.

What graphics hardware do you have?

---

### Post by fantab on 2013-02-01
I have an Intel DG45ID board with on board GMA X4500HD... I had no issues in any previous versions of either Ubuntu or any other distro.

---

