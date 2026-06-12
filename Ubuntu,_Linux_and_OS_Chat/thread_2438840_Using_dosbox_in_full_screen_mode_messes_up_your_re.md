---
title: "Using dosbox in full screen mode messes up your resolution"
date: 2020-03-18
forum: Ubuntu, Linux and OS Chat
---

### Post by tiriss on 2020-03-18
If you're using dosbox under Ubuntu 19.10 (I'm guessing at the version as Xubuntu is still fighting with Gnome), you're going to have a major issue when changing to full screen inside a dosbox.  It completely destroys your X settings in Gnome.  I'm not sure why it happens and don't really care but they've known Gnome has serious issues with dosbox since 2014!  The solution is surprisingly the Gnome code and to switch to xfce4.  Not only is it massively faster on all GPU's but you don't have to put up with the Gnome.    It's a different graphical interface, and takes some getting used to.  But it IS the ISO standard for sharing desktops etc.  The CE means common environment and was a standard before Gnome and systemd.  It takes less space and resources, so do yourself a favor if you're using dosbox and:  sudo apt install xubuntu-desktop  There are some underlying Gnome anomalies I'll need to fix but steam games are faster, switching full screen or vice-versa in dosbox works fine, and the common desktop is great to see again. And the best part is you're using a UNIX-like system like it should be used:  don't need to reboot every time something crashes.  I'm not sure how dosbox is able to crash gnome completely forcing a reboot.  I don't deal with that anymore, X works fine and dosbox works fine.

---

### Post by wildmanne39 on 2020-03-18
*Thread moved to **Ubuntu, Linux and OS Chat since this is not a support request**.*

---

### Post by mastablasta on 2020-03-19
wine does it as well for some fullscreen titles. and that's not all, native engine for Jedi knight 2 (openJK and  OpenJK Academy) can do that as well for wide screen. i use kde and don't get a full cash. i found the easiest way is to reset resolution in system settings after the game session or to logout and log back in (since i have it set to always start a fresh KDE session).

---

