---
title: "Nautilus fails to launch"
date: 2016-04-01
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2016-04-01
Just performed my daily apt update, upgrade and discovered that Nautilus failed to launch, however Caja works.
> (nautilus:12021): GLib-GIO-CRITICAL **:  g_dbus_interface_skeleton_unexport: assertion  'interface_->priv->connections != NULL' failed
(nautilus:12021):  GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion  'interface_->priv->connections != NULL' failed
Could not register the application: Timeout was reached
(nautilus:12021): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
(nautilus:12021): GLib-GObject-WARNING **: invalid (NULL) pointer instance
(nautilus:12021): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

caja launched 

gksudo nautilus worked perfectly

gksudo caja produced errors

> [INDENT] pfeiffep@Dell-1749:~$ gksudo caja
Initializing caja-main-menu extension
Initializing caja-open-terminal extension

 --- Hash table keys for warning below:
--> l2054
--> inode/directory
--> root
sys:1:  PyGIWarning: Caja was imported without specifying a version first. Use  gi.require_version('Caja', '2.0') before import to ensure that the right  version gets loaded.
** Message: Initializing gksu extension...
sys:1:  Warning: /build/glib2.0-VLj5wM/glib2.0-2.48.0/./gobject/gsignal.c:2635:  instance '0x55ebaabe1c40' has no handler with id '2864'
sys:1:  Warning: /build/glib2.0-VLj5wM/glib2.0-2.48.0/./gobject/gsignal.c:2635:  instance '0x55ebaaa95880' has no handler with id '2928'
sys:1:  Warning: /build/glib2.0-VLj5wM/glib2.0-2.48.0/./gobject/gsignal.c:2635:  instance '0x55ebaaa77220' has no handler with id '2935'
sys:1: Warning: Source ID 61 was not found when attempting to remove it
sys:1: Warning: Source ID 62 was not found when attempting to remove it

 (caja:7689): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)
 (caja:7689): Eel-WARNING **: "caja-directory.c: directories" hash table still has 1 element at quit time
 [/INDENT]

---

### Post by pfeiffep on 2016-04-02
I learned from the ubuntu-mate community how to solve this ........

Clean apt cache ```
sudo apt clean && sudo apt update
```
purge and re-install nautilus ```
sudo apt purge nautilus && sudo apt install nautilus
```

---

