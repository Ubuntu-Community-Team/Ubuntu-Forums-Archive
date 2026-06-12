---
title: "Xubuntu 13.10 (saucy) asking password to shutdown/restart"
date: 2013-05-06
forum: Ubuntu Development Version
---

### Post by pnarciso on 2013-05-06
There's this annoying bug in saucy that, for unknown reason whenever I try to restart or shutdown using the log out dialog it ask me root password. This doesn't happen in 13.04, so I presume it's a bug.

My work around was to use visudo and remove sudo password. Doing this it doesn't ask me for the password no more.

Just to add that only myself is logged, there's no multiple users logged.

---

### Post by Elfy on 2013-05-07
Doesn't happen here for me.

---

### Post by pnarciso on 2013-05-07
I'm running 64 bits if it makes any difference.

This issues happened to me, with an update from 13.04 to 13.10, and with a full installation of a daily iso.

With the full installation it doesn't happen right away, but some updates caused this behavior.

Any sugestion why is it asking my root password when only one user is logged?

---

### Post by Elfy on 2013-05-07
I'll clean install  daily tomorrow and see if I can replicate it. 

No idea why it does that for you. It shouldn't as I guess you know.

Would be good to know if it's still affecting you.

---

### Post by Elfy on 2013-05-08
Seen this with reboot, though once I had the password dialogue it was unusable. 

Could get to shutdown from top panel button in login screen.

I'll look tomorrow with a daily and see whether it's there - if it is I'll bug report it.

---

### Post by pnarciso on 2013-05-08
The strange part is, if you log in as guest and press the reboot button, it works without asking any password.

---

### Post by Elfy on 2013-05-09
[https://bugs.launchpad.net/xfwm4/+bug/1178373](https://bugs.launchpad.net/xfwm4/+bug/1178373)

filed it - if you can confirm.

---

### Post by Elfy on 2013-05-13
Odd - installed nvidia.

Shutdown now not asking password - but it does appear to logout instead.

---

### Post by slickymaster on 2013-05-13
> **pnarciso said:**
> I'm running 64 bits if it makes any difference.

Don't know if it is related or not, but on a [32 bit daily iso]("http://cdimage.ubuntu.com/daily-live/current/saucy-desktop-i386.iso") install, I'm not having that problem.

---

