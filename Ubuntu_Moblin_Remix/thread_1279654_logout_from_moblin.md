---
title: "logout from moblin?"
date: 2009-10-01
forum: Ubuntu Moblin Remix
---

### Post by suoko on 2009-10-01
moblin has set itself as default DE on my karmic
however, since it can't connect to wi-fi net, i'd like to revert to gnome.
CTRL+ALT+BACKSPACE doesn't work, there is no logout button and flexiserver doesn't work

do i have to remove it ?

Ctrl+Alt+Backspace (i.e. the shortcut which was used to restart the X server) has to be enabled in a different way with respect to previous releases of Ubuntu.
This is due to the fact that “DontZap” is no longer an option in the X server and has become an option in XKB instead.

SOLUTION
open gnome-keyboard-properties

[* Get to the System->Preferences->Keyboard menu.]

* Select the “Layouts” tab and click on the “Layout Options” button.

* Then select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.

---

### Post by celticbhoy on 2009-10-01
Think its Alt - k - SysRq now.

---

