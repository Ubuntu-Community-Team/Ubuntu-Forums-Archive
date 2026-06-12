---
title: "Application title bar occasionally black"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-03-21
I started to experience this issue after updating GTK+3 to the version 3.3.20-0ubuntu1.
Downgrading back to 3.3.18 solves the issue immediately.

The issue is that the application title bar gets completely black, not always, but occasionally.

I have seen this happen with NVidia proprietary drivers and with ATI open source drivers, plus both with xserver 1.11 and 1.12.

I am using gnome-shell (3.3.90-0ubuntu1) and Adwaita theme.

---

### Post by kaldor on 2012-03-21
Yep, I've also had this since last night.

---

### Post by Harry33 on 2012-03-21
Here is the bug report (961310):
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/961310](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/961310)

---

### Post by Quackers on 2012-03-21
I've had this on a reboot for the last couple of days. If you go in to System Settings > Appearance and change the theme to Ambiance, then change it back to Adwaita, the border returns normally.

---

### Post by sammiev on 2012-03-21
> **Quackers said:**
> I've had this on a reboot for the last couple of days. If you go in to System Settings > Appearance and change the theme to Ambiance, then change it back to Adwaita, the border returns normally.

Been doing the same thing myself. Glad to know it's a bug and not from my playing. :)

---

### Post by pressureman on 2012-03-22
Yes, same here. Window titles are black after logging in. If I change the theme to something else, then change it back, it's OK for the rest of that session.

---

### Post by Harry33 on 2012-03-22
> **pressureman said:**
> Yes, same here. Window titles are black after logging in. If I change the theme to something else, then change it back, it's OK for the rest of that session.

Yes that is true here too.
This bug might also be a theme issue, the theme being not compatible with the latest GTK+3.

---

### Post by kaldor on 2012-03-22
I just applied updates and it seems to be fixed. There were a few updates related to GNOME (Shell, themes, etc).

---

### Post by Harry33 on 2012-03-22
> **kaldor said:**
> I just applied updates and it seems to be fixed. There were a few updates related to GNOME (Shell, themes, etc).

Fixed here too:
- gnome-themes-standard 3.3.92-0ubuntu2 is responsible for the Adwaita theme.

---

