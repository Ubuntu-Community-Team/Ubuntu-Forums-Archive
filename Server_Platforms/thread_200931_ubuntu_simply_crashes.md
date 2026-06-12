---
title: "ubuntu simply crashes"
date: 2006-06-21
forum: Server Platforms
---

### Post by DSABH on 2006-06-21
hey,

i didnt really know where to put my thread, however, i think it will fit to this forum.

im new in ubuntu, but i already love it :) .

but theres one things thats keeps annoying me. sometimes ubuntu simply goes back to the login screen, so i have to re-login and all my previously created work which i havent saved at this time are gone :(

im running on ubuntu 6 (gnome) with xgl and compiz.


thanks for help

---

### Post by Fac51 on 2006-06-21
i've had gdm crash on me a few times, it's getting annoying... have you tried switching to kdm or xdm?

---

### Post by DSABH on 2006-06-21
im pretty much happy with gnome.. does anyone know how to fix this??

---

### Post by Fac51 on 2006-06-21
uhm... you can still use gnome if you use kdm...

---

### Post by DSABH on 2006-06-21
errm.. now im confused.. i thought kde is another desktop manager similar to gnome.. how can i run both and how does it make sense?

---

### Post by Fac51 on 2006-06-21
kde stands for K Destop Environment

kdm stands for K Desktop Manager

kdm = login screen, much like gdm(the default)

or if you're new to linux, kdm = welcome screen and same for gdm

do: ```
sudo apt-get install kdm
```

when it prompts you, select kdm and press enter

log out and you'll see the difference

when you log back in, you'll still be using GNOME

stop thinking so much, it might be part of your issue

---

### Post by DSABH on 2006-06-23
hey..,

i checked out kdm, i switched back do gdm however cuz i think the problem is sth else.

it happened again, all of a sudden there was the login screen. i logged in and then there appeared an error message saying that my previous session wasnt longer than 10 seconds and that i shall look up ./.xsession-errors to fix the problem. i did so and there are some entries but i cant do anything with this.

heres the content of xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sjanisch"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
SESSION_MANAGER=local/sjanisch-laptop:/tmp/.ICE-unix/5241
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
gnome-window-decorator: Kein Prozess beendet
ERROR: ld.so: object '/usr/share/fglrx/diversions/libGL.so.1.2' from LD_PRELOAD cannot be preloaded: ignored.
compiz.real: Couldn't load plugin 'libmenu.so'
compiz.real: Couldn't load plugin 'libtransset.so'

(gnome-panel:5316): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_set_size: assertion `width >= 0 && height >= 0' failed

(gnome-panel:5316): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5316): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height 25

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

** (gnome-terminal:5492): WARNING **: Kein Handler für Kontrollsequenz »device-control-string« festgelegt.

```

for the non-germans ;) :
 Kein Handler für Kontrollsequenz »device-control-string« festgelegt.
 means
 No handler set for control-sequence

thanks for help

---

### Post by Fac51 on 2006-06-23
that has happened to me before... the "previous session wasnt longer than 10 seconds ..." message, i just let it sit for a minute and logged in, one time though it wouldn't stop, so i rebooted and was fine

but i'll see if i can find any information about it

---

### Post by DSABH on 2006-06-24
thanks a lot man.. this is really gettin annoying. i was once sittin on a presentation and didnt save for some reason when i was at lunch in the meantime. it does only happen when the comp is idle.. my presentation however was deleted :-!

---

