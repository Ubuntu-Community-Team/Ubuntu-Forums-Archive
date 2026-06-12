---
title: "Segmentation Fault"
date: 2011-05-16
forum: Server Platforms
---

### Post by thoufiq on 2011-05-16
Hi All,
         I have installed sun-java6 and eciipse-ide in my  ubuntu server 10.10. My java is running fine but while running eclipse, i  got segmentation error. I had googlled lots of times but the answers  are not good to resolve the error. Can anyone suggest me to resolve this  error. Below i have pasted the result...

[B][COLOR=Red]sam-osm@dhcppc4:usr/local/opt/eclipse$ sudo ./eclipse

(eclipse:2960): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(eclipse:2960): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE' (instance) failed

(eclipse:2960): Gtk-CRITICAL **: IA__gtk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960):  Gtk-WARNING **: Screen for GtkWindow not set; you must always set a  screen for a GtkWindow before using the window

(eclipse:2960): Gtk-WARNING **: Screen for GtkWindow not set; you must  always set a screen for a GtkWindow before using the window

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_display_get_pointer: assertion 'GDK_IS_DISPLAY (display)' failed

(eclipse:2960): Gtk-WARNING **: Screen for GtkWindow not set; you must  always set a screen for a GtkWindow before using the window

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_n_monitors: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gtk-WARNING **: Screen for GtkWindow not set; you must  always set a screen for a GtkWindow before using the window

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_monitors_geometry: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_default_colormap: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_colormap_get_visual: assertion 'GDK_IS_COLORMAP (colormap)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_default_colormap: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_root_window: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_screen_get_root_window: assertion 'GDK_IS_SCREEN (screen)' failed

(eclipse:2960): Gdk-CRITICAL **: IA__gdk_window_new: assertion 'GDK_IS_WINDOW (parent)' failed
Segmentation fault[/COLOR][/B]    

Anyone suggest me to overcome this error.

Thanks

---

### Post by thoufiq on 2011-05-17
Any one help me......

---

### Post by GDR! on 2011-05-17
Did you try without sudo?

---

### Post by thoufiq on 2011-05-17
> **GDR! said:**
> Did you try without sudo?


Hai GDR
                  I had already tried without sudo but the same error is coming...



Thanks

---

