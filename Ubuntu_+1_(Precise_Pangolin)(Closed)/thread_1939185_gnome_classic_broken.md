---
title: "gnome classic broken"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-03-11
I've a long delay logging into the fallback session and when is finally loaded these errors are present in .xsession-errors.
Anyone else have this?

> $ more ../.xsession-errors 
*** glibc detected *** gsettings-data-convert: malloc(): memory corruption (fast): 0x09205180 ***
gnome-session[1684]: WARNING: Application 'gsettings-data-convert.desktop' failed to register before timeout
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator
Avviso del window manager: CurrentTime used to choose focus window; focus window may not be correct.
Avviso del window manager: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

Gtk-WARNING **: no parent (nil) is not realized but child GtkPlug 0x9c37010 is realized

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: gnome-sound-applet: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: nm-applet: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.

nautilus: ../../src/xcb_io.c:528: _XAllocID: asserzione "ret != inval_id" non riuscita.

** WARNING **: zeitgeist-datahub.vala:224: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
mporaneamente non disponibile) on X server :0.


Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: nm-applet: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


Gdk-WARNING **: nautilus: Fatal IO error 11 (Risorsa temporaneamente non disponibile) on X server :0.


** WARNING **: zeitgeist-datahub.vala:224: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
24: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!


Note.. it is inside a virtualmachine.

---

### Post by lucazade on 2012-03-11
disabling /etc/xdg/autostart/gsettings-data-convert.desktop to startup fixes the problem.
now i'm looking for an existing bug report.

---

### Post by tista on 2012-03-11
Hi Luca. ;)

Yeah last week I've experienced the crash of data-convert...
see my gdb log:
[http://paste.ubuntu.com/865382/]("http://paste.ubuntu.com/865382/")

Then now my PP seems to be OK with it...

Regards,
Tista

---

### Post by dino99 on 2012-03-11
> **lucazade said:**
> disabling /etc/xdg/autostart/gsettings-data-convert.desktop to startup fixes the problem.
now i'm looking for an existing bug report.

reported this one: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/951429](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/951429)

---

### Post by lucazade on 2012-03-11
thanks guys for the info :)

---

### Post by lucazade on 2012-03-24
Dino do you still have this issue?

---

### Post by dino99 on 2012-03-24
> **lucazade said:**
> Dino do you still have this issue?

not on my end; now im running nvidia 295.33 + xorg 1.12 from edgers + kernel 3.3

dont have xorg.conf anymore

---

### Post by lucazade on 2012-03-24
thanks dino..
so.. going to open a new bug report because your old one was marked as dup of wrong one imho.

---

### Post by dino99 on 2012-03-24
> **lucazade said:**
> thanks dino..
so.. going to open a new bug report because your old one was marked as dup of wrong one imho.

which of my old one?

---

### Post by lucazade on 2012-03-24
> **dino99 said:**
> which of my old one?

this one:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/951429](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/951429)

about  Fatal IO error 11 (Resource not available) on X server :0.

---

### Post by dino99 on 2012-03-24
> **lucazade said:**
> this one:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/951429](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/951429)

about  Fatal IO error 11 (Resource not available) on X server :0.

Thanks to remind me about that one; errors are effectively gone here, even before have switched to new nvidia driver & xorg 1.12. Sometimes i need to erase .local due to red herrings left behind (log out/in recreate a fresh one, without the buggy things of course :))

but agree that is not a dupe as marked anyway.

note about the duplicate(s): the sad effect is they are removed from the reporter radar, then forget about them. (even if "special search" can re-found them)

---

### Post by lucazade on 2012-04-04
still affected by this issue, opened a new bug report because Dino's one was closed and
reported as duplicated of a wrong one.

nobody else is affected?

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/973264](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/973264)

---

### Post by ventrical on 2012-04-04
Gnome classic with ccsm working here.. only nautilus bug.

---

### Post by sgage on 2012-04-04
> **lucazade said:**
> still affected by this issue, opened a new bug report because Dino's one was closed and
reported as duplicated of a wrong one.

nobody else is affected?

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/973264](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/973264)

I don't normally use Classic, but gave it a try, and yes, I see the same issue. I have added myself to the bug report.

---

