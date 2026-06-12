---
title: "Opening lid reveals unlocked screen contents before showing lock-screen"
date: 2020-09-23
forum: Security
---

### Post by helipil0t2 on 2020-09-23
The following post describes my problem exactly.   
[https://forum.xfce.org/viewtopic.php?id=14030](https://forum.xfce.org/viewtopic.php?id=14030)

When opening my laptop lid to wake it up from sleep, I see everything I  was working on (Unlocked Screen) for a few seconds before the lock  screen appears.  
A bit of a security issue seeing as anyone can have a glimpse at what's active on your session.  

It seems to be an issue when using the Prime profile NVIDIA and not when I'm using the Intel driver.  
I thought the recent driver upgrade would sort me out but I'm still having the same issues even with Nvidia 450.66 drivers installed. 
The solution described in the xfce forum of adding a pause.sh script  in /lib/systemd/system-sleep did not work.

I'm assuming I'm not the only one with this issue out there and was hoping someone could shed some light on this problem.  
What steps should I take to dig into this a little further?  

I appreciate everyone's time.

---

### Post by #&amp;thj^% on 2020-09-23
I'm not convinced this is strictly an Nvidia Driver bug, XFCE4 Screensaver has had known issues past and present.
This issue though would be best suited on the bug squad: [https://gitlab.xfce.org/apps/xfce4-screensaver/-/issues](https://gitlab.xfce.org/apps/xfce4-screensaver/-/issues)
And it would also be nice to include this for some information about whats happening or not happening.;)
```
kill -9 $(pidof xfce4-screensaver)
xfce4-screensaver --no-daemon --debug
```
Good Luck and keep us posted here would also be nice thing.

---

### Post by helipil0t2 on 2020-09-24
I guess I should have noted I am not using xfce.  I'm running Ubuntu 20.04 with Gnome 3.  xfce4-screensaver isn't being used.

---

### Post by #&amp;thj^% on 2020-09-24
I kind of wondered about that, but opted for not second guessing.
> The following post describes my problem exactly.
[https://forum.xfce.org/viewtopic.php?id=14030](https://forum.xfce.org/viewtopic.php?id=14030)

Anyway lets see what your using with:
```
more /etc/X11/default-display-manager
```
If its lightdm, it might be possible to set a delay to help hide contents shown on wake.

---

