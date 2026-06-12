---
title: "Updates broke gnome flashback with compiz"
date: 2014-08-24
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-08-24
I noticed an update to gnome-session-flashback yesterday along with several others and never gave it a 2nd thought. They didn't require a reboot.

But, today gnome-flashback (with compiz) just boots to a blank screen (I see my wallpaper and nothing else happens).
This is booting with upstart or systemd - the same result. 

All I can boot into is a Unity session.

Anybody else have the same problem?

---

### Post by grahammechanical on 2014-08-24
Yes, it is happening on my system running Nouveau. It is login screen bounce but without the password panel and the app indicators. The same login background image with Ubuntu 14.10 logo. So, it does not load to the desktop.  I used Ctrl+Alt+F2 and as I entered the third character of my user name the screen went blank. Same thing with Crtl+Alt+F3

Regards.

---

### Post by fooman on 2014-08-24
i had *almost* the exact same thing happen a few days ago....except it was unity that would give me the blank desktop (wallpaper was there, but no unity launcher, dash, etc..).  i could only do a ctrl-alt-f1 to get to terminal, then "sudo reboot", and finally booted to gnome-shell to get to a working desktop.  

i somehow reset unity/compiz settings and all has been fine since.  could be mistaken,  but i think these were the commands that fixed it:

```
dconf reset -f /org/compiz/
 
setsid unity
```

btw, creating a new user resulted in a working unity desktop...it was just my user settings which failed.  like i said,  all is working perfectly again after resetting things.

---

### Post by Cavsfan on 2014-08-24
> **grahammechanical said:**
> Yes, it is happening on my system running Nouveau. It is login screen bounce but without the password panel and the app indicators. The same login background image with Ubuntu 14.10 logo. So, it does not load to the desktop.  I used Ctrl+Alt+F2 and as I entered the third character of my user name the screen went blank. Same thing with Crtl+Alt+F3

Regards.

Glad to see it is not only me. I seen this in the changelog: 
```
gnome-panel (1:3.8.1-1ubuntu1) utopic; urgency=medium

  * Merge with Debian unstable, remaining changes:
    - Use an epoch in version number.
    - Recommend indicator-applet-complete.
    - [COLOR=#ff0000]Use unity-control-center instead of gnome-control-center.[/COLOR]
    - Recommend gnome-screensaver instead of depending on it.
    - Suggest compiz.
    - Adjust Breaks/Replaces for Ubuntu versioning.
    - Drop 14_revert_timedate_change.patch, we are using timedated.
    - Add patches:
      + git_drop_gconf.patch
      + 40_unset_menuproxy.patch
      + 41_classic_layout.patch
      + 50_ubuntu_sessions.patch
      + 51_desktop_file.patch
      + lp-1314706.patch
      + clock-fix-expanding.patch
  * Merge 49_no_screensaver.patch into 50_ubuntu_sessions.patch.
  * Drop git_fix_panel_size.patch, applied upstream:
  * Refresh patches:
    - git_drop_gconf.patch
    - 40_unset_menuproxy.patch
    - lp-1314706.patch
    - clock-fix-expanding.patch
  * Rebase patches:
    - 50_ubuntu_sessions.patch
    - 51_desktop_file.patch

 --   Sat, 23 Aug 2014 18:48:54 +0400
```

I found that I didn't have unity-control-panel installed so I installed it. Rebooted and still no flashback - neither metacity or compiz would boot.
It would boot with gnome (cairo dock) though, that and Unity.

So I checked to see if there were any more updates and another update to gnome-panel and gnome-session-flashback came in. 

```
gnome-panel (1:3.8.1-1ubuntu2) utopic; urgency=medium

  * Fixes for gnome-session-flashback (LP: #1360778):
    - debian/rules: Add back symlinking code.
    - debian/patches/50_ubuntu_sessions.patch: make sure
      session file for Compiz session is installed.
  * Update previous changelog entries for proper merge.

 --   Sun, 24 Aug 2014 16:55:17 +0400
```

It fixed this bug which was done really fast! [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1360778](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1360778)

> **fooman said:**
> i had *almost* the exact same thing happen a few days ago....except it was unity that would give me the blank desktop (wallpaper was there, but no unity launcher, dash, etc..).  i could only do a ctrl-alt-f1 to get to terminal, then "sudo reboot", and finally booted to gnome-shell to get to a working desktop.  

i somehow reset unity/compiz settings and all has been fine since.  could be mistaken,  but i think these were the commands that fixed it:

```
dconf reset -f /org/compiz/
 
setsid unity
```

btw, creating a new user resulted in a working unity desktop...it was just my user settings which failed.  like i said,  all is working perfectly again after resetting things.

Thanks but I had no problem with Unity and now with the 2nd update gnome flashback (with compiz) is working great!
I booted with systemd and all is good now. :guitar:

It was kind of weird at first with the gnome (cairo dock) small panels overlaid on the flashback top panel but clicking the mouse on them caused them to go away.

---

### Post by Cavsfan on 2014-08-24
An update also asked me if I wanted to use the default cairo-dock themes and I gave that a "Y" which wiped out my custom settings. It did mention that it backed my settings up though.

I just had to find where they were and finally found them in **/home/cavsfan/.config/cairo-dock/themes/Theme_20140824_111000**.
So I just had to copy the contents of that folder back into **/home/cavsfan/.config/cairo-dock/current_theme** logout and back in and all was back to normal. :popcorn:

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-08-24133934.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-08-24133934.php")

---

