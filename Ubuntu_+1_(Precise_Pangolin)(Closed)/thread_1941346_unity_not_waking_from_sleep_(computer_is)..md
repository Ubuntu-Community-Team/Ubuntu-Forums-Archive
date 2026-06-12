---
title: "unity not waking from sleep (computer is)."
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-03-15
I have been getting this on and off since I installed beta 1.

Laptop goes into sleep mode normally (either from system menu or closing the lid).
When resuming, the laptop makes all the right noises, the hard drive kicks in etc, the screen comes on but everything is black and I just get a mouse pointer.
Everything seems to be back except the desktop itself.

This isn't every time, it happens around 1 in 4 sleeps.

Anyone else suffer this?  Not really sure what to file a bug against.  I would say the only app in common is chromium, which is always running and I can't remember if the problem has happened without any apps running.

Intel core i3 and intel GFX.

---

### Post by 2F4U on 2012-03-15
The file /var/log/pm-suspend.log holds the log information about each suspend / resume attempt. I would suggest that you look into this file after a failed attempt and see if it gives any hints on why the attempt failed.

---

### Post by x-shaney-x on 2012-03-15
Only lines that suggest any problems at all are these: ```
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.
```

Things is, those lines appear with every suspend, even the ones that do resume as normal so doesn't appear to be a factor.

Something I forgot to mention:

The password dialogue DOES appear as normal, it is the transition from password box to desktop that seems to be going wrong.

---

### Post by 2F4U on 2012-03-15
Ah, then you might want to look into .xsession-errors in your home directory, since it could be the desktop that crashes.

---

### Post by Lazy123 on 2012-04-09
I have exactly the same problem and reported the bug to Launchpad: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/977135](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/977135)

.xsession-errors:
```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
** Message: applet now removed from the notification area
Initializing decor options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing gnomecompat options...done
Initializing vpswitch options...done
Initializing resize options...done
Initializing snap options...done
Initializing grid options...done
Initializing move options...done
I/O warning : failed to load external entity "/home/eero/.compiz/session/10c2ce62b4fd20d96a133396959190322500000019610039"
Initializing session options...done
Initializing wall options...done
Initializing animation options...done
** Message: using fallback from indicator to GtkStatusIcon

(nm-applet:2053): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing fade options...done
Initializing ezoom options...done
Initializing scale options...done
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Initializing unityshell options...done

(cryptkeeper:2063): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Setting Update "launcher_hide_mode"
** Message: moving back from GtkStatusIcon to indicator

(bluetooth-applet:2060): GLib-CRITICAL **: g_variant_iter_loop: assertion `g_variant_is_of_type (GVSI(iter)->value, G_VARIANT_TYPE_ARRAY)' failed

(bluetooth-applet:2060): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

** (zeitgeist-datahub:2450): WARNING **: zeitgeist-datahub.vala:224: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

** (gnome-screensaver:2451): WARNING **: screensaver already running in this session

** (nautilus:2054): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:2054): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

(totem:2618): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'


(totem:2668): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'


(totem:2689): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'


(totem:2717): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'

compiz (decor) - Warn: failed to bind pixmap to texture

(totem:2741): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'


(gnome-settings-daemon:2029): color-plugin-WARNING **: Done switch to new account, reload devices

(gnome-settings-daemon:2029): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

** Message: PID 2053 (we are 2053) sent signal 15, shutting down...

(deja-dup-monitor:2705): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.35 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2705): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.36 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts
** Message: PID 3996 (we are 2053) sent signal 15, shutting down...

(nm-applet:2053): Gdk-WARNING **: nm-applet: Fatal IO error 4 (Interrupted system call) on X server :0.


```

---

