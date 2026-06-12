---
title: "Windows title bar not clickable after de-maximize."
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by amikot on 2013-03-20
All windows that i maximize, after demaximisation has the same problem with title bar. 
Titlebar are visible but cant be clicked, if i click in that place i click next layer elements (desktop icons, backgrount windows).

I have to use ALT key to move windows back maximize (moving top), and than i can use buttons on the title bar.

That problem started on ubuntu 12.10 with compiz 9.9.2, and now i see its in last beta of ubuntu 13.04

Does anyone knows what is solution to my problem ?

---

### Post by dilodicus on 2013-03-25
Bump, Also having the same issue with the latest build of 13.04

Hopefully this is just a beta bug and will be squashed before release.

---

### Post by Frogs Hair on 2013-03-25
I installed 13.04 earlier and don't see this . Post on this thread for 13.04 problems until it is released. [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)
 Check the window actions in the tweak tool just in case and file or check for an existing bug report.

---

### Post by cariboo on 2013-03-26
Moved to U+1

---

### Post by dino99 on 2013-03-26
it should be an issue with compiz:
> compiz --replace ccp &

---

### Post by spier on 2013-03-26
> **Frogs Hair said:**
> I installed 13.04 earlier and don't see this . 

Same problem as OP since RR install, but I was in a long run. 
Just rebooted and it is working now.

---

### Post by VinDSL on 2013-03-26
I was having this problem, the other day.

It was easily reproducible:
[LIST]
[*]open a terminal window
[*]drag it to the top of the display, and release it
[*]maximize it
[*]minimize it
[/LIST]
After doing this, the min/max/close buttons disappeared, plus I couldn't move the window by grabbing the title bar, nor could I resize the window by grabbing a frame.  It's as if the terminal window lost its focus, by maximizing and minimizing it.

Supposedly, this problem was introduced during a recent Compiz upgrade.

Haven't tried Unity in a couple of days, so I don't know if its been fixed, or not.

---

### Post by philinux on 2013-03-26
Today's updates should have fixed this.

> compiz (1:0.9.9~daily13.03.25-0ubuntu1) raring; urgency=low

  [ Michael Terry ]
  * [regression] Unmaximized windows can't be closed, minimized, moved
    (LP: #1158161)

  [ MC Return ]
  * Multimonitor: Grid plugin: Wrong calculation of top left mouse-grid-
    resize corner coordinates (LP: #1139835)

  [ Ubuntu daily release ]
  * Automatic snapshot from revision 3639

---

### Post by stinkeye on 2013-03-26
Fixed here with latest compiz update.

---

### Post by Cavsfan on 2013-03-26
I had been having this problem for quite a while. It appears to be fixed with today's updates as stinkeye and philinux said.
But, I'm not holding my breath as I thought it was fixed before.

---

### Post by VinDSL on 2013-03-26
Whoa!  That's interesting!

Title bar problem is fixed, but Unity is blitzed (on my install).

I have 2 launchers. Moving the window around rips, tears & smears the display... background (wallpaper) cannot be set, and so forth,and so on.

Alrighty then.  Back to GS, before I go blind...  :)

---

### Post by mc4man on 2013-03-26
> **VinDSL said:**
> Whoa!  That's interesting!

Title bar problem is fixed, but Unity is blitzed (on my install).

I have 2 launchers. Moving the window around rips, tears & smears the display... background (wallpaper) cannot be set, and so forth,and so on.

Alrighty then.  Back to GS, before I go blind...  :)
At this point, if fully using the gnome 3 ppa, then very little use logging into a unity session.
Will be interesting on how gnome 3/4 is handled in the future

---

### Post by VinDSL on 2013-03-26
> **mc4man said:**
> At this point, if fully using the gnome 3 ppa, then very little use logging into a unity session [...]
Yep!

It's war_of_the_worlds now :D

---

### Post by Cavsfan on 2013-03-27
Windows title bar still not working here. I did not install the gnome 3 ppa.

---

### Post by philinux on 2013-03-27
> **VinDSL said:**
> Whoa!  That's interesting!

Title bar problem is fixed, but Unity is blitzed (on my install).

I have 2 launchers. Moving the window around rips, tears & smears the display... background (wallpaper) cannot be set, and so forth,and so on.

Alrighty then.  Back to GS, before I go blind...  :)

For testing purposes try resetting unity. See if that fixes it.

```
dconf reset -f /org/compiz/
then 
setsid unity
```

---

### Post by VinDSL on 2013-03-27
> **philinux said:**
> For testing purposes try resetting unity. See if that fixes it.

```
dconf reset -f /org/compiz/
then 
setsid unity
```
Aye!  It's all good fun...

Got nothing to loose, at this point.

```
vindsl@Zuul:~$ dconf reset -f /org/compiz/
vindsl@Zuul:~$ setsid unity
vindsl@Zuul:~$ unity-panel-service: no process found
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell

** (compiz:16051): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (compiz:16051): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
WARN  2013-03-27 20:16:55 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:16:55 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:16:56 unity.libindicator <unknown>:0 Desktop file '/home/vindsl/.local/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-03-27 20:16:56 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/ubuntu-tweak.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-03-27 20:16:56 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:16:56 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:16:57 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
ERROR 2013-03-27 20:16:57 unity.glib.dbus.server GLibDBusServer.cpp:518 DBus name lost 'com.canonical.Unity'
WARN  2013-03-27 20:16:57 unity.glib.dbus.proxy GLibDBusProxy.cpp:377 Calling method "CanHibernate" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:16:57 unity.session.gnome GnomeSessionManager.cpp:334 logind CanHibernate call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-03-27 20:16:57 unity.glib.dbus.proxy GLibDBusProxy.cpp:377 Calling method "CanSuspend" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:16:57 unity.session.gnome GnomeSessionManager.cpp:334 logind CanSuspend call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct

```

Okay, here goes nothing...

BRB  ;)

---

### Post by VinDSL on 2013-03-27
Second attempt...

```
vindsl@Zuul:~$ dconf reset -f /org/compiz/
vindsl@Zuul:~$ setsid unity
vindsl@Zuul:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Another window manager is already running on screen: 0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

vindsl@Zuul:~$ 

```

Gonna go to Plan B...

BRB

---

### Post by VinDSL on 2013-03-27
> **Cavsfan said:**
> Windows title bar still not working here. I did not install the gnome 3 ppa.
Worked for about 30 seconds here.  LoL!  :D

Heh!  It's a start...

---

### Post by VinDSL on 2013-03-27
Strike 3...

```
vindsl@Zuul:~$ unity --replace &
[2] 4719
vindsl@Zuul:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell

** (compiz:4723): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (compiz:4723): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
WARN  2013-03-27 20:38:17 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.libindicator <unknown>:0 Desktop file '/home/vindsl/.local/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-03-27 20:38:18 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/ubuntu-tweak.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
ERROR 2013-03-27 20:38:19 unity.glib.dbus.server GLibDBusServer.cpp:518 DBus name lost 'com.canonical.Unity'
WARN  2013-03-27 20:38:19 unity.glib.dbus.proxy GLibDBusProxy.cpp:377 Calling method "CanHibernate" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:38:19 unity.session.gnome GnomeSessionManager.cpp:334 logind CanHibernate call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-03-27 20:38:19 unity.glib.dbus.proxy GLibDBusProxy.cpp:377 Calling method "CanSuspend" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:38:19 unity.session.gnome GnomeSessionManager.cpp:334 logind CanSuspend call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed


```

Thanks, for the idea, but no joy tonight!

Okay, back to GS...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-27-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-mar-2013-1.png")[/INDENT]

---

### Post by Xanza on 2013-04-07
I'm getting this in Xubuntu 13.04 aswell. Can't click on the titlebar

---

### Post by Cavsfan on 2013-04-10
By golly, I do believe this is fixed now! :D

---

### Post by Cavsfan on 2013-04-10
Ooops spoke too soon. :o

---

### Post by VinDSL on 2013-04-10
> **Cavsfan said:**
> Ooops spoke too soon. :o
Yep!

Just had it happen in Gnote...  :(

---

### Post by QDR06VV9 on 2013-04-10
> **VinDSL said:**
> Strike 3...

```
vindsl@Zuul:~$ unity --replace &
[2] 4719
vindsl@Zuul:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell

** (compiz:4723): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (compiz:4723): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
WARN  2013-03-27 20:38:17 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.libindicator <unknown>:0 Desktop file '/home/vindsl/.local/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-03-27 20:38:18 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/ubuntu-tweak.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2013-03-27 20:38:18 unity.glib.dbus.server GLibDBusServer.cpp:573 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
ERROR 2013-03-27 20:38:19 unity.glib.dbus.server GLibDBusServer.cpp:518 DBus name lost 'com.canonical.Unity'
WARN  2013-03-27 20:38:19 unity.glib.dbus.proxy GLibDBusProxy.cpp:377 Calling method "CanHibernate" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:38:19 unity.session.gnome GnomeSessionManager.cpp:334 logind CanHibernate call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-03-27 20:38:19 unity.glib.dbus.proxy GLibDBusProxy.cpp:377 Calling method "CanSuspend" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:38:19 unity.session.gnome GnomeSessionManager.cpp:334 logind CanSuspend call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
ERROR 2013-03-27 20:38:59 unity.glib-gio <unknown>:0 g_dbus_connection_call_internal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed


```

Thanks, for the idea, but no joy tonight!

Okay, back to GS...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-27-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-mar-2013-1.png")[/INDENT]

VinDSL is that really Gnome shell or Fallback? Havent tried gnome shell with raring yet.. Unity Works Very Well for me..

---

### Post by VinDSL on 2013-04-10
> **runrickus said:**
> VinDSL is that really Gnome shell or Fallback?
Yes, that's really Gnome-Shell...

The dock is "Plank" with "ACYL" icons, and "Conky" is on the right-side. ;)

```
indsl@Zuul:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.8.0.1+git20130410.86c92c37-0ubuntu1~13.04~ricotz0
  Candidate: 3.8.0.1+git20130410.86c92c37-0ubuntu1~13.04~ricotz0

```

---

### Post by QDR06VV9 on 2013-04-10
> **VinDSL said:**
> Yes, that's really Gnome-Shell...

The dock is "Plank" with "ACYL" icons, and "Conky" is on the right-side. ;)

```
indsl@Zuul:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.8.0.1+git20130410.86c92c37-0ubuntu1~13.04~ricotz0
  Candidate: 3.8.0.1+git20130410.86c92c37-0ubuntu1~13.04~ricotz0

```

Ok You got me curious now gona have to give gnome shell a whirl!
Your well known for  your Conky!! Yours is the only one I have trouble with..LOL

---

### Post by screaminj3sus on 2013-04-11
Thank god compiz will be gone when unity-next comes, compiz has become nothing but a regression machine and should have been ditched long ago.

---

### Post by pqwoerituytrueiwoq on 2013-04-11
> **screaminj3sus said:**
> Thank god compiz will be gone when unity-next comes, compiz has become nothing but a regression machine and should have been ditched long ago.it was perfectly fine 3 years ago in 10.04, lol

---

### Post by VinDSL on 2013-04-11
> **screaminj3sus said:**
> Thank god compiz will be gone [...]

> **pqwoerituytrueiwoq said:**
> it was perfectly fine 3 years ago [...]
Um... er... but...

"The Cube" is soooo sexy!  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-11-apr-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-apr-2013-1.png")[/INDENT]


It's Compiz's one saving grace, IMO...

---

### Post by Cavsfan on 2013-04-11
> **VinDSL said:**
> Yep!

Just had it happen in Gnote...  :(

I had a bunch of windows open, closed them, opened them back and no problem so I posted it was fixed. Then I had Firefox open and clicked maximize then close and poof - title bar unclickable. :(

Yeah, the cube is what it is all about and Cairo Dock oh and of course your Conky which is gorgeous! I hope I can keep up with your changes!

[[img]http://ompldr.org/taTJkNg[/img]](http://ompldr.org/vaTJkNg/Screenshot 13-04-11.png)

---

### Post by Adelard on 2013-04-19
It might not be an orthodox solution but Gnome tweak tool did solve the problem here. By letting the system managing the desktop (don't know if that's clear but first option in "desktop"), I could find back my desktop picture and could minimize/close windows as well. Hope this helps.
[IMG]http://ompldr.org/vaTVrNw/Capture%20du%202013-04-19%2020:36:19.png[/IMG]

---

### Post by screaminj3sus on 2013-04-20
> **Adelard said:**
> It might not be an orthodox solution but Gnome tweak tool did solve the problem here. By letting the system managing the desktop (don't know if that's clear but first option in "desktop"), I could find back my desktop picture and could minimize/close windows as well. Hope this helps.
[IMG]http://ompldr.org/vaTVrNw/Capture%20du%202013-04-19%2020:36:19.png[/IMG]

Yeah I saw the same behavior here, compiz gets totally b0rked and unusable if you don't have nautilus managing the desktop. For some reason on the daily iso's when you run them live nautilus managing the desktop is disabled, but when I installed the system it had it enabled by default.

---

### Post by mc4man on 2013-04-20
> **screaminj3sus said:**
> Yeah I saw the same behavior here, compiz gets totally b0rked and unusable if you don't have nautilus managing the desktop. For some reason on the daily iso's when you run them live nautilus managing the desktop is disabled, but when I installed the system it had it enabled by default.
Decided to file a bug on the recent live images, (last tested was from thurs, the 18th) not having nautilus handling the desktop which makes the live session semi-worthless unless adjusted.
Nothing yet (was mentioned it *may* be intentional.
If they continue this on the 13.04 release then I don't think even the inmates are running the asylum... 
(I would be surprised if this is the release state of affairs

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1170483](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1170483)

---

### Post by VinDSL on 2013-04-20
> **mc4man said:**
> If they continue this on the 13.04 release then I don't think even the inmates are running the asylum... 
Bwahahahaha, funboy3!

Haven't thought about [that song]("http://youtu.be/I51GR5cevjA") in years!  :D

Good one...

---

### Post by aactive on 2013-04-22
I have the same problem any window's titlebar not clickable and if i tried to click it bring the below window

---

### Post by Cavsfan on 2013-04-25
I was surprised to see this still is broke on the final release. I installed the tweak tool and "Have file manager handle the desktop" was on default.
We shall see. I click on the top right X button to close one thing and Firefox got closed.

Naw. still not fixed.

---

### Post by NoBugs! on 2013-05-09
Same problem here, after enabling grid plugin, either maximizing shows the top bar AND titlebar,

or it shows only the bar at the top of the screen, then de-maximizing makes the titlebar disappear completely.

Where has this bug been reported on launchpad, I'd like to keep an eye on it.

---

### Post by Cavsfan on 2013-05-11
Not sure if this is the exact bug that goes with this problem but, it is very annoying and it is still alive in Raring after final release and it is also present in Saucy as well.

[https://bugs.launchpad.net/ubuntu/+bug/1171451](https://bugs.launchpad.net/ubuntu/+bug/1171451)

I open several windows and click the x at the top to close one of them and it closes the wrong one like Firefox. Thankfully one can use the history to get back to where they were but really?
This is a major pain in the neck and on a final release? There are only 8 people on that bug, there should be one for every person who installed Raring. That would get it fixed.

Or is there another bug besides the one above that we should all be marking that we are being affected by it?

---

### Post by mc4man on 2013-05-11
> **Cavsfan said:**
> Not sure if this is the exact bug that goes with this problem but, it is very annoying and it is still alive in Raring after final release and it is also present in Saucy as well.

[https://bugs.launchpad.net/ubuntu/+bug/1171451](https://bugs.launchpad.net/ubuntu/+bug/1171451)

I open several windows and click the x at the top to close one of them and it closes the wrong one like Firefox. Thankfully one can use the history to get back to where they were but really?
This is a major pain in the neck and on a final release? There are only 8 people on that bug, there should be one for every person who installed Raring. That would get it fixed.

Or is there another bug besides the one above that we should all be marking that we are being affected by it?

That bug is unrelated - it's a by-product of nautilus not handling the desktop in a live session

---

### Post by Cavsfan on 2013-05-12
> **mc4man said:**
> That bug is unrelated - it's a by-product of nautilus not handling the desktop in a live session

Oh thanks! Could someone please point out the correct bug. I tried to search for it but came up with the wrong one (above).

What I have is this: I open 4 windows let's just say. I maximize 3 of them and leave the forth unmaximized.

I click on the x to close one of the maximized windows that has the focus, the one on top and it closes one of the others behind the one on top.
Is that what everyone else's system is doing?

It sure is annoying.

EDIT: Or am I wrong about this? I just tested 4 windows and they all closed as expected. 
EDIT2: Nope it did it again with just firefox maximised. Guess it just takes a while before the top buttons to not work.

---

### Post by mc4man on 2013-05-12
May be this bug, I'm not that affected but does happen to a maxed vlc at times
[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

---

### Post by Cavsfan on 2013-05-13
> **mc4man said:**
> May be this bug, I'm not that affected but does happen to a maxed vlc at times
[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

Thank you for that! I would suggest everyone with this problem report that that bug applies to them.

---

### Post by rockyit86 on 2013-05-22
> **Cavsfan said:**
> I had been having this problem for quite a while. It appears to be fixed with today's updates as stinkeye and philinux said.
But, I'm not holding my breath as I thought it was fixed before.

I have the same problem, tried to reset the unity and compiz with no success,
after windows spread, all the title bars are visible again, and i have updated the compiz to the current version

Do you have any possible solution?

---

### Post by Cavsfan on 2013-05-22
> **mc4man said:**
> May be this bug, I'm not that affected but does happen to a maxed vlc at times
[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

> **rockyit86 said:**
> I have the same problem, tried to reset the unity and compiz with no success,
after windows spread, all the title bars are visible again, and i have updated the compiz to the current version

Do you have any possible solution?

The only thing we can do is sign onto that bug in mc4man's post. 
My Raring does this all day and it trickled over into Saucy as it does it as well. The only solution in gnome fallback is 
to click on the window in the bar at the bottom of the screen and click on close, unmaximize, etc. 
You cannot click on the three buttons at the top of the window.

I thought this was just a gnome classic thing but, since you say it happens in Unity as well, I am surprised this has not gotten more attention and been fixed.

---

### Post by Cavsfan on 2013-05-24
I thought maybe that new kernal in Raring 3.8.0-22-generic might have fixed this problem. It seemed to but, then when I opened several windows it did the same thing. :(

---

### Post by Cavsfan on 2013-05-31
I upgraded Linux Mint 14 Nadia to 15 Olivia. 14 is based on Quantal while 15 is based on Raring and it has this exact same problem.
I would click on the x at the top to close a window and another window would close that I did not want to close. The whole bar became unclickable as well.

I am not specifically bringing up Mint but, I just think that this 6 month release schedule might not be the way to go if things are not ever going to get fixed.
Gedit still opens 2 windows also.

And I am not meaning to complain too badly as these OSs are still free but, some things are getting annoying. :(

---

### Post by cariboo on 2013-05-31
Could your gedit problem have something to do with /usr/share/applications/gedit.desktop? My looks like this:

```
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.8.2
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit/gedit-bugreport
Actions=Window;Document;
Keywords=Text;Editor;Plaintext;Write;
X-Ubuntu-Gettext-Domain=gedit

[Desktop Action Window]
Name=Open a New Window
Exec=gedit --new-window
OnlyShowIn=Unity;

[Desktop Action Document]
Name=Open a New Document
Exec=gedit --new-document
OnlyShowIn=Unity;
```

or could possibly have 2 one in /usr/share/applications and another in ~/.local/share/applications?

---

### Post by Cavsfan on 2013-06-01
> **cariboo907 said:**
> Could your gedit problem have something to do with /usr/share/applications/gedit.desktop? My looks like this:

```
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.8.2
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit/gedit-bugreport
Actions=Window;Document;
Keywords=Text;Editor;Plaintext;Write;
X-Ubuntu-Gettext-Domain=gedit

[Desktop Action Window]
Name=Open a New Window
Exec=gedit --new-window
OnlyShowIn=Unity;

[Desktop Action Document]
Name=Open a New Document
Exec=gedit --new-document
OnlyShowIn=Unity;
```

or could possibly have 2 one in /usr/share/applications and another in ~/.local/share/applications?

My /usr/share/applications/gedit.desktop is identical to yours with the exception of this line **X-GNOME-Bugzilla-Version=3.6.2** where yours says 3.8.2.
I have the gedit icon in **/usr/share/applications** but do not have anything in** ~/.local/share/applications**.

Does this shed any light on my problem?
Thanks **cariboo907**!

---

### Post by Cavsfan on 2013-06-01
This is weird! The gedit opening two tabs thing with **gksudo gedit filename** is happening now even on Precise Pangolin 12.04 LTS. That has never happened that I noticed.

---

### Post by Bezukhov on 2013-06-12
Same (very minor) problem here. I am using Gnome Classic and if I need to max, minimize or close a window I have to right click on the tab on the bottom taskbar. And it is an intermittent problem as well.

---

### Post by aactive on 2013-06-21
Same for me  I've to hightlight first the window that I need to close,minimize or maximize.
My session is cairo dock with compiz WM.

---

### Post by zesterer on 2013-07-09
This NEEDS to get fixed! So annoying!

---

### Post by titi4u on 2013-07-09
> **zesterer said:**
> This NEEDS to get fixed! So annoying!

Yes I totally agree with you !

---

### Post by DevilPenguin on 2013-07-09
Same going on here. It can get frustrating. It's been a year and it has not been fixed yet

---

### Post by Cavsfan on 2013-07-10
There appears to be a fix on it's way. Have you all marked this bug applies to you?

[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

In the bottom of that bug is listed a fix for the problem [https://code.launchpad.net/~mar-kolya/compiz/fix-for-1158267/+merge/167596](https://code.launchpad.net/~mar-kolya/compiz/fix-for-1158267/+merge/167596)

But, although it is a pain I think I'll hold out for a permanent fix which should be out shortly as the bug is marked critical.

---

### Post by mc4man on 2013-07-10
> **Cavsfan said:**
> There appears to be a fix on it's way. Have you all marked this bug applies to you?

[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

In the bottom of that bug is listed a fix for the problem [https://code.launchpad.net/~mar-kolya/compiz/fix-for-1158267/+merge/167596](https://code.launchpad.net/~mar-kolya/compiz/fix-for-1158267/+merge/167596)

But, although it is a pain I think I'll hold out for a permanent fix which should be out shortly as the bug is marked critical.

We'll see how quick 
The small  proposed fix has not been merged (staus - needs fixing), what's come out of that bug & a couple of similar *was* the intention to redo the deco plugin. That itself depended on creating some tests first which was done in a recent large commit to compiz trunk
Unfortunately that commit (which was reviewed, **somehow accepted** & merged), has created an even worse problem - shrinking windows.
(- unmaxed windows will shrink on each re-opening by the size of the frame extents - for ex. with light-themes 29px vertically, 2 px horizontally. This would go on till the window reaches it's min. size  
So I'd think that needs to be fixed before you see any 'fixed' compiz packages

[lpbug]1198000[/lpbug]

---

### Post by Cavsfan on 2013-07-10
> **Cavsfan said:**
> There appears to be a fix on it's way. Have you all marked this bug applies to you?

[https://bugs.launchpad.net/compiz/+bug/1158267](https://bugs.launchpad.net/compiz/+bug/1158267)

In the bottom of that bug is listed a fix for the problem [https://code.launchpad.net/~mar-kolya/compiz/fix-for-1158267/+merge/167596](https://code.launchpad.net/~mar-kolya/compiz/fix-for-1158267/+merge/167596)

But, although it is a pain I think I'll hold out for a permanent fix which should be out shortly as the bug is marked critical.

[QUOTE=mc4man;12725941]We'll see how quick 
The small  proposed fix has not been merged (staus - needs fixing), what's come out of that bug & a couple of similar *was* the intention to redo the deco plugin. That itself depended on creating some tests first which was done in a recent large commit to compiz trunk
Unfortunately that commit (which was reviewed, **somehow accepted** & merged), has created an even worse problem - shrinking windows.
(- unmaxed windows will shrink on each re-opening by the size of the frame extents - for ex. with light-themes 29px vertically, 2 px horizontally. This would go on till the window reaches it's min. size  
So I'd think that needs to be fixed before you see any 'fixed' compiz packages

[lpbug]1198000[/lpbug][/QUOTE]

Ouch! Plus this bug affects Ubuntu 12.10, 13.04, 13.10 as well as Mint 15 and I would have to assume Mint 14 as well. The only version unaffected are LTS versions Precise 12.04 and Mint 13.
So, one would think this would have been on the front burner a long time ago.

---

### Post by Cavsfan on 2013-07-12
I was incorrect about 12.10. It is not affected by this bug. Although you may have to click the close button more than once on a fully maximized window. It will close unlike all of the other versions I mentioned.

---

### Post by mc4man on 2013-07-12
There is now a fix for the shrinking windows so while not yet merged (small jenkins issue), there should be a newer compiz soon. After that maybe something concerning this bug.

Though in a default unity session have found very hard to duplicate, only once & a rare while with vlc. Seems more likely to occur in gnome panel style sessions & or other ubuntu variants

---

### Post by Cavsfan on 2013-07-12
> **mc4man said:**
> There is now a fix for the shrinking windows so while not yet merged (small jenkins issue), there should be a newer compiz soon. After that maybe something concerning this bug.

Though in a default unity session have found very hard to duplicate, only once & a rare while with vlc. Seems more likely to occur in gnome panel style sessions & or other ubuntu variants

I would agree that it is a gnome issue as I seldom get into Unity and have the problem with every single open maximized windows. 
Once maximizied, it can only be minimized or closed by right clicking on the application in the bottom panel and selecting the opion there.

Myself, I haven't been in Unity long enough to see if it does it there. A bug fix for this will be **_greatly_** appreciated by many people.

---

### Post by Cavsfan on 2013-07-14
Did today's updates fix this problem? It doesn't seem to be broken any more. I have never been able to maximize a windows and then minimize it, but I can now just like it is supposed to work. ;)

Also I believe gedit opening two tabs with **gksudo gedit *filename*** seems to be fixed as well. I tried that several tlimes as well. It's a good day. I need to check some of my other distros.

:guitar:

Nope Raring is still the same but, I am sure it will get this update soon.

---

### Post by mc4man on 2013-07-14
> **Cavsfan said:**
> Did today's updates fix this problem? It doesn't seem to be broken any more. I have never been able to maximize a windows and then minimize it, but I can now just like it is supposed to work. ;)

Also I believe gedit opening two tabs with **gksudo gedit *filename*** seems to be fixed as well. I tried that several tlimes as well. It's a good day. I need to check some of my other distros.

:guitar:

Nope Raring is still the same but, I am sure it will get this update soon.
Nothing has changed as far as compiz, otherwise don't know as rarely could make it happen anyway.

As far as gedit - that 2 tab deal went away in gedit 3.7+ so no longer an issue in 13.10, would still exist in prior releases that use an older gedit.
(gksu is no longer default installed, users would need to do so as no alt. like pkexec has been implemented yet. It's possible that on amd64 gksu will yet again install with wrong default mode, su vs. sudo

Here i've just gone ahead & switched nautilus & gedit over to pkexec, gdebi is much more complicated so that's up to the dev to switch or not.

---

### Post by Cavsfan on 2013-07-14
> **mc4man said:**
> Nothing has changed as far as compiz, otherwise don't know as rarely could make it happen anyway.

As far as gedit - that 2 tab deal went away in gedit 3.7+ so no longer an issue in 13.10, would still exist in prior releases that use an older gedit.
(gksu is no longer default installed, users would need to do so as no alt. like pkexec has been implemented yet. It's possible that on amd64 gksu will yet again install with wrong default mode, su vs. sudo

Here i've just gone ahead & switched nautilus & gedit over to pkexec, gdebi is much more complicated so that's up to the dev to switch or not.

It definitely only happens in Gnome Fallback/Flashback.
Yes, SPM just messed up so it must still not be fixed. I seen grub, gedit and I thought I saw compiz in the updates but, compiz must have just been my imagination.
Do you think they will put gedit 3.7+ in 13.04 and 12.10 as that is a major pain?

I know **apt-cache policy *file-name*** will tell you what is installed, what is installable and the package it came from but, is there a way to tell a file's installation date?

---

### Post by mc4man on 2013-07-14
> **Cavsfan said:**
> 
Do you think they will put gedit 3.7+ in 13.04 and 12.10 as that is a major pain?

Never in the  Ubuntu repos for those releases

---

### Post by Cavsfan on 2013-07-14
> **mc4man said:**
> Never in the  Ubuntu repos for those releases

Thanks! I think I'll do what it takes to get the newer version into those.

---

### Post by mc4man on 2013-07-14
> **Cavsfan said:**
> Thanks! I think I'll do what it takes to get the newer version into those.

Well the gnome3 ppa would have the 3.8 gedit for raring, after that you're on your own (maybe I remember you don't like ppa's ??
Myself just use, as mentioned, pkexec, which isn't affected,  have gedit packages for 12.04, 13.04 & something a bit more for 13.10 (intergrated the geditas nautilus python extension & extended it's mimetypes

(someone recently emailed me asking if  I'd put the precise & raring  builds in a standalone ppa so will do so.

---

### Post by Cavsfan on 2013-07-15
> **mc4man said:**
> Well the gnome3 ppa would have the 3.8 gedit for raring, after that you're on your own (maybe I remember you don't like ppa's ??
Myself just use, as mentioned, pkexec, which isn't affected,  have gedit packages for 12.04, 13.04 & something a bit more for 13.10 (intergrated the geditas nautilus python extension & extended it's mimetypes

(someone recently emailed me asking if  I'd put the precise & raring  builds in a standalone ppa so will do so.

I changed my mind and decided to just leave it alone. 
I had already added this workaround someone mentioned on the bug to .bashrc:

```
# gksudo gedit opening 2 tabs fix
gksudo ()
{
 if [ "$1" = "gedit" ]
 then
  shift
  gksudo gksudo gedit "$@"
 else
  command gksudo "$@"
 fi
} 
```

---

### Post by Cavsfan on 2013-08-06
I'm pretty sure the recent compiz updates fixed the windows bar not being clickable.
I made terminal maximized and could close it with the x on the top. :)

Does any one agree and can confirm this?

---

### Post by Cavsfan on 2013-08-06
Spoke too soon. I can confirm that it is *_**not**_* fixed.

---

### Post by muktupavels on 2013-09-21
Seems that now this bug is fixed. :)

---

### Post by Cavsfan on 2013-09-23
> **albertsmuktupavels said:**
> Seems that now this bug is fixed. :)

I hope so. It's still broke in Raring, but I guess that is another story. Still checking things out right now.

---

### Post by Cavsfan on 2013-09-24
So, far so good. I haven't seen it lately. :D

---

### Post by Cavsfan on 2013-09-30
This is indeed fixed in Saucy and Raring. :D

This thread should be marked solved.

---

