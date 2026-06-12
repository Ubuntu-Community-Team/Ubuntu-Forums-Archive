---
title: "PCManFM 0.4.6 - has single click support now!"
date: 2008-07-14
forum: The Cafe
---

### Post by PCMan on 2008-07-14
Finally, PCManFM can open items with "single click". Hurray!

Website: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
GnomeFiles: [http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)

All users are encouraged to upgrade to this version.

Major Changes:

* Single click to open items (optional, finally we have it!).
* UI adjustment: The preference dialog is now GNOME HIG compliant.
* The preference dialog will use a non-GNOME HIG compliant, more compact layout under small screens.
* Support calling preference dialog via command line with --show-pref.
* Support changing wallpaper of PCManFM's desktop window via command line with --set-wallpaper.
* Open preference dialog no longer blocks the desktop window and other folder windows.
* Some fixes.

I've noticed that there was a patch for single click in pcmanfm previously. I, however, didn't apply that patch because I have some cleaner approaches. Single click is already implemented in XFCE's libexo. So, I borrowed some code from them, and write some myself. Finally, single click works nicely in PCManFM!

Regarding to the future plans of pcmanfm, here is a roadmap.
[http://lxde.org/wiki/TODO#PCManFM_.28file_manager.29](http://lxde.org/wiki/TODO#PCManFM_.28file_manager.29)

Cheers!

---

