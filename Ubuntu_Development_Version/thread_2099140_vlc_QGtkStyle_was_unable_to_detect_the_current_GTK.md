---
title: "vlc: QGtkStyle was unable to detect the current GTK+ theme"
date: 2012-12-28
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-12-28
This is just seen on a fresh 13.04 install with todays image. vlc will use some fallback theme.
Likely not too big an issue if using the global menu with vlc, quite obvious if keeping the menu in vlc. ( env QT_X11_NO_NATIVE_MENUBAR=1 vlc

Installing libgnome2-common fixes if one is adversely affected
(older installs will likely have the above package already installed
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1094360](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1094360)

---

