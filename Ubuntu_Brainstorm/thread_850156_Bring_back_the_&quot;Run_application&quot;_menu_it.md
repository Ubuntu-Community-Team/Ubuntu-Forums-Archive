---
title: "Bring back the &quot;Run application&quot; menu item to Gnome"
date: 2008-07-05
forum: Ubuntu Brainstorm
---

### Post by Azrael Nightwalker on 2008-07-05
Gnome used to have a "Run Application" menu item just like in Windows, KDE, and others. But it was removed in Gnome 2.12. Now users have to know the ALT+F2 shortcut or search for the "Run" applet.
Alt+f2 run dialog is hardcoded into gnome-panel. There is no way to create a menu item for it. There are many independent implementations of it: grun, gmrun, gnome-run-dialog, gnome-panel-tool. It proves that people still need it.

Also lots of people ask for it:
[http://www.gossamer-threads.com/lists/gentoo/user/167129](http://www.gossamer-threads.com/lists/gentoo/user/167129)
[http://ubuntuforums.org/showthread.php?t=68031](http://ubuntuforums.org/showthread.php?t=68031)
[http://darkness.codefu.org/wordpress/post/152](http://darkness.codefu.org/wordpress/post/152)
[http://ubuntuforums.org/showthread.php?t=76150](http://ubuntuforums.org/showthread.php?t=76150)
[http://ubuntuforums.org/showthread.php?t=506489](http://ubuntuforums.org/showthread.php?t=506489)
[http://ubuntuforums.org/showthread.php?t=91454](http://ubuntuforums.org/showthread.php?t=91454)
[http://answers.launchpad.net/ubuntu/+question/32956](http://answers.launchpad.net/ubuntu/+question/32956)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/66659-run-command-gno](http://www.linuxforums.org/forum/redhat-fedora-linux-help/66659-run-command-gno) me-desktop.html
[http://ubuntuforums.org/showthread.php?t=593846](http://ubuntuforums.org/showthread.php?t=593846)
[http://ubuntuforums.org/showthread.php?t=88695](http://ubuntuforums.org/showthread.php?t=88695)
[http://ubuntuforums.org/showthread.php?t=512290](http://ubuntuforums.org/showthread.php?t=512290)
[http://ubuntuforums.org/showthread.php?t=65850](http://ubuntuforums.org/showthread.php?t=65850)

Removing this dialog from the menu was a stab to discoverability, and usability. Users shouldn't be required to know any cryptic spells like alt+f2 or nohup to run a single command which isn't available from the menu, without having to open a terminal window. Most often they don't even know what a terminal is. They just want to run a program by it's binary name.

When Gnome devs removed the run dialog from the menu they should have left a possibility to bring it back at will. But they didn't. They left no choice to users and distro creators.

See the Gnome bug: [http://bugzilla.gnome.org/show_bug.cgi?id=455537](http://bugzilla.gnome.org/show_bug.cgi?id=455537)

Brainstorm idea: [http://brainstorm.ubuntu.com/idea/10748/](http://brainstorm.ubuntu.com/idea/10748/)

---

