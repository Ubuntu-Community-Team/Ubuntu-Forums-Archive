---
title: "pink red color tint on screen after today's gnome shell updates"
date: 2022-08-30
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-08-30
Hello,

when I had updated ubuntu 21.10 to 22.04, when choosing ubuntu xorg there was a red - pink tint on my screen where gray areas should be instead. That upgade had many errors though. I made another upgrade to 22.10 and I noticed that also flashback had this tint that didn't have before.

I made a brand new installation of 22.10 the other day, prior to the latest update of gnome shell and everything was fine. Now I have this tint under ubuntu wayland! Also I have flickers on my screen.

I checked a little more and I saw that the tint is a known bug, yet for xorg though.
[www.reddit.com/r/Fedora/comments/n2tel3/f34_reddish_tint_with_gnome_40_on_xorg/](www.reddit.com/r/Fedora/comments/n2tel3/f34_reddish_tint_with_gnome_40_on_xorg/)
gitlab.gnome.org/GNOME/gnome-shell/-/issues/4071

There is a solution, yet I do not know which option to pick:
bbs.archlinux.org/viewtopic.php?id=265336

Regards!

---

### Post by Claus7 on 2022-08-30
Hello,

using flashback, I went to system settings->color->laptop screen and I added the profile: Artifex Software sRGB ICC Profile. It was the 2nd offered, since the automatic one, which I saw (initially there was none) didn't to the trick. For the first one it mentioned about problems, so I picked up the 2nd one. After 2-3 restarts there is no problem.

Regards!

---

