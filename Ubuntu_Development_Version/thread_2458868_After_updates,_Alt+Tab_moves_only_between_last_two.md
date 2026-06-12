---
title: "After updates, Alt+Tab moves only between last two focused apps"
date: 2021-03-05
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2021-03-05
After last updates, alt+tab no lonnger moves between all applications. It only switches between the two last focused applications.
My keyboard settings are reset to default, and it behaves strangely:

1. "Alt+tab" is not there at all.
2. Switch Windows is "Super+;", Switch Applications is "Super+Tab". 
3. Super+Tab works just like Alt+Tab, i.e. switches between the last two focued appa. 
4. When I try to set Switch Windows "Alt+Tab" it complains that it is already in use for switching applications, although it is clearly not.
5. When I try to set "Switch Applications" to be "Alt+Tab", the shortcut still only moves between two last focused apps.

Any ideas? Is it just me?

---

### Post by multip on 2021-03-06
I have the same issue as you 

This happened after the update (2021-03-05), there were many updated packages, but my guess is:
gnome-shell:amd64 (3.38.3-2ubuntu2, 3.38.3-3ubuntu1), 
gnome-shell-common:amd64 (3.38.3-2ubuntu2, 3.38.3-3ubuntu1), 
gnome-shell-extension-prefs:amd64 (3.38.3-2ubuntu2, 3.38.3-3ubuntu1), 
 

The overlay with the preview is also gone while switching windows.


Perhaps unrelated to this, is my touchpad settings (tab to click and edge scrolling) are gone also. 
Changing them gnome preferences panel has no effect.

---

### Post by Wise Ferret on 2021-03-07
I reported this as a bug [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1918014").
Anyone suffering from this can confirm it there, so it may be taken care of.

---

### Post by corradoventu on 2021-03-08
This is a duplicate of [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1917926](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1917926)
and occur only in Xorg; no problem in Wayland.

---

