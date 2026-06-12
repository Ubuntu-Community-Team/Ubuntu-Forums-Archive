---
title: "PrtScr and Alt-PrtScr for Lubuntu/LXQt 19.04 and 19.10"
date: 2019-12-14
forum: Tutorials
---

### Post by GhX6GZMB on 2019-12-14
The keyboard shortcuts **PrtScr** (copy full screen to clipboard) and **Alt-PrtScr** (copy active window to clipboard) are not available in Lubuntu/LXQt, although they are extremely useful.

Here's a recipe for settling them up.

First, install "**scrot**" and "**xclip**" (it's very likely that they are already installed).

Open **Preferences -> LXQt Settings ->  Shortcut Keys** from the Applications Menu.

Check if PrtScr ("Print") and Alt-PrtScr ("Print Window") shortcuts are already present (they probably aren't). Otherwise create them.

Assign this command to the PrtScr shortcut: **sh -c '****scrot -o /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''**
Do the same for Alt-PrtScr using:  **sh -c '****scrot -o -u /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''**

Now you can paste the latest PrtScr screenshot into any graphics or LibreOffice program. Even "Ctrl-V" will work.
 
The PrtScr shortcut command will create the file /tmp/clip_"UID" (eg, /tmp/clip_1001), this will disappear after each reboot and will be overwritten with each new screenshot.


_COMMENT:_
The reason for including the UID in the filename instead of just naming the screenshot file "/tmp/clip" is due to file ownership/permissions. When changing user (logout...login), the "/tmp/clip" file still exists with the previous user:group attributes and cannot be modified/overwritten by the new user.

---

