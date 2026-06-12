---
title: "Rhythmbox locks up between tracks (sometimes)"
date: 2016-03-06
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2016-03-06
I turned most plugins off, i added 3 (rhythmbox_hide, remember-the-rhythm, and tray icon)
after disabling the coverart lookup plugin it happed less frequently (maybe it was just a fluke)
it has alocked up about 4 times today, testing it live using yesterdays daily iso
```
ubuntu-mate@ubuntu-mate:~$ rhythmbox

(rhythmbox:11544): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:11544): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:11544): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:11544): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:11544): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:11544): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:11544): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed

(rhythmbox:11544): GStreamer-CRITICAL **: gst_tag_list_remove_tag: assertion 'gst_tag_list_is_writable (list)' failed
TypeError: <lambda>() takes 2 positional arguments but 4 were given
TypeError: <lambda>() takes 2 positional arguments but 4 were given

(rhythmbox:11544): GStreamer-CRITICAL **: gst_segment_to_stream_time: assertion 'segment->format == format' failed



```

---

### Post by tom-bellas3rd on 2016-03-06
I've noticed this on regular Ubuntu as well, it sometimes lags out a bit whilst picking the next song. Thought it was just me.

---

