---
title: "Alt+Tab Window Switcher only gives 1 option Freya Acer C720"
date: 2014-12-02
forum: Ubuntu/Debian BASED
---

### Post by tango_ninja on 2014-12-02
(I'm running Freya 0.3 64-bit on an Acer C720 NX.SHEAA.016.  Intel i3-4005u with 4GB ram.  Linux 3.13.0-40-generic)

The problem is that window switching by keyboard shortcut (Alt+Tab) only gives one option.  That is, the Alt+Tab only goes back one window.... if I press tab again, it goes back to the original starting window. 

E.g.:  I am in Google Chrome.  I also have Firefox and LibreOffice open.  If I press Alt+Tab my active window becomes Firefox.  Pressing Tab again (keeping Alt held down) goes right back to Google Chrome, bypassing LibreOffice.  This is the case for any number of windows in any open applications.  Alt+Tab only switches to the immediately previous window.

This only happened recently.... last week it was working fine.  I'm not sure if I changed a setting but I've tried retracing my steps and can't think of anything.  Also, I used to have a window switching image/indicator, which would appear when pressing Alt+Tab and visually show all open windows and which one I was switching to.  This no longer appears.

Both _org.gnome.settings-daemon.plugins.media-keys_ and _org.pantheon.desktop.gala.keybindings_ look good, as do the ElementaryOS Keyboard settings (see attached screenshots).  I don;t think this is a keybinding issue, since Alt+Tab still has window switching functionality.  

Is there a gala component I can reinstall to reset this functionality?  Any other suggestions?

---

