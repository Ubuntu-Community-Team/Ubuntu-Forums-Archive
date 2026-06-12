---
title: "Ubuntu One Will not Install"
date: 2012-01-09
forum: Ubuntu One (CLOSED)
---

### Post by duranl on 2012-01-09
Ubuntu one was not sync-ing, so I tried to uninstall it and then reinstall it.  After I removed it through the software center, I tried to install it again.  When I try to install it through the software center, it does that installation, but when I open the control panel to do the next installation, the status bar goes all the way to the right (fills up) and just stays there.  After that, nothing happens until I close the window.

When I try to do it through the terminal: sudo apt-get install ubuntuone-control-panel
I get this: ubuntuone-control-panel is already the newest version.

So I try to open it: ubuntuone-control-panel-gtk
I get this: The program 'ubuntuone-control-panel-gtk' is currently not installed.  You can install it by typing: sudo apt-get install ubuntuone-control-panel

Anyway I cen get Ubuntu One working again?  I depend on it heavily for my school files.

Thanks!

---

### Post by duranl on 2012-01-10
Bump.  I have yet to find a solution to this problem.

---

### Post by duranl on 2012-01-10
Okay.  I got it installed, but now I get this message: File Sync error. (org.freedesktop.DBus.Error.UnknownMethod: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist
)

I found [this thread]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-control-panel/+bug/858808") in which people mentioned a work around, but cannot find "~/.config/ubuntuone" and "~/.local/share/ubuntuone".  What does the squiggly line at the beginning of both paths mean?  I cannot find those folders anywhere.

---

