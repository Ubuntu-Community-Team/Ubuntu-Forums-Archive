---
title: "Screensaver determination"
date: 2014-10-14
forum: Ubuntu Application Development
---

### Post by wardexter on 2014-10-14
Hi,

I'm writing an application that has to have knowledge about the actual screensaver state.
On Ubuntu with GNome, it works by calling out "gnome-screensaver-command -q", this gives me active or inactive.

But when running Unity this doesn't work.
Anyone has any options for this?

Commandline or c++ :)

I've tried with XScreensaver extension but this continuously gives my a "disabled" state...

Kr

Mathieu

---

### Post by kostkon on 2014-10-14
I guess one way that will probably work on both desktops would be with D-Bus (either with C++ bindings or cli with dbus-monitor/dbus-send, if you can make it work.) The bus name for the screensaver is org.gnome.ScreenSaver. It provides methods (at least on my 12.04) like GetActive(), Lock(), SetActive() and a signal ActiveChanged, you might want to register a callback for that.

You can install [D-Feet]("https://apps.ubuntu.com/cat/applications/d-feet/") and play around.

---

### Post by wardexter on 2014-10-15
Thanks for pointing out D-Feet, that one helps a lot! Got already some other stuff that I was also looking for :).

It seems like the terms "screensaver" and "screenlock" are handled differently between gnome and unity. That's the thing that messed up my solution.

With gnome, the screensaver command also returns true when locking, which is not the case in Unity.
There I need the ScreenSaver.IsActive stuff.

This while ScreenSaver.IsActive is not working properly on gnome.

Thanks for the help Kostkon!

---

