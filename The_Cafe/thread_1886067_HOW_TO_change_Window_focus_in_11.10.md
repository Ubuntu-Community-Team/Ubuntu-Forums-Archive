---
title: "HOW TO change Window focus in 11.10"
date: 2011-11-24
forum: The Cafe
---

### Post by blavthefaur on 2011-11-24
After a fresh install of 11.10, I noticed one annoying feature regarding new windows. When I pressed my keyboard shortcut for my home folder (Ctrl + Alt + H), the window would open in the foreground but not be selected or focused on. On many occasions, this resulted in my accidentally closing (via Alt + F4) a window in the background while attempting to close the window in the foreground.

To resolve this, first install gnome-tweak-tool:

```
sudo apt-get install gnome-tweak-tool
```

In the Dash, open "Advanced Settings" (which is what the gnome-tweak-tool is called).

Click on "Windows" in the sidebar. The last setting in the list should say "Window focus mode." Change this value to "Sloppy."

Problem solved!

---

