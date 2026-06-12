---
title: "Now that was a serious lockup"
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-16
could not even ssd into the system
no ctrl+alt+sysrc+[R-E-I-S-U-B]
no ctrl+alt+f1
was playing supertuxkart on my laptop (all effects enabled except pixel shaders, intel gpu does not like that one)
```
~$ cat .xsession-errors.old | egrep -v "gmusicbrowser|Music|weather-Message"
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.

(polkit-gnome-authentication-agent-1:1768): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:1768): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
ERROR:root:Could not find any typelib for Unity
libpager-Message: Setting the pager rows returned false. Maybe the setting is not applied.
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:1917): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1917): LIBDBUSMENU-GLIB-WARNING **: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/sound/menu
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_get_double: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(xfce4-indicator-plugin:1917): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion `g_variant_type_check (type)' failed

(xfce4-indicator-plugin:1917): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed
GStreamer::Interfaces perl module not found -> visuals not available
These commands were not found : mpg123, flac123, mpg321
 => these file types won't be played by the 123 output : mp3
*** unhandled exception in callback:
*** unhandled exception in callback:
*** unhandled exception in callback:

(process:2057): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed

(update-notifier:1781): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(process:3170): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Error: No running window found

(process:3188): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(wrapper:1918): weather-WARNING **: Download of weather data failed with HTTP Status Code 2, Reason phrase: Cannot resolve hostname (api.yr.no)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(process:2161): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart'
```

---

