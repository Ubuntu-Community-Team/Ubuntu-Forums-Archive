---
title: "Gnome-shell 3.24.1-0ubuntu2 dependencies"
date: 2017-04-26
forum: Ubuntu Development Version
---

### Post by harry332 on 2017-04-26
[B]The newest gnome-shell in artful proposed changes some dependencies on themes and backgrounds.
[/B][I]"gnome-shell (3.24.1-0ubuntu2) artful; urgency=medium
[ Jeremy Bicha ]
  * Lower more depends and recommends to suggests to smooth Main inclusion:
    - adwaita-icon-theme-full
    - gnome-themes-standard-data
    ...
Replace gnome-backgrounds dependency with ubuntu-wallpapers"[/I]
However, gnome-shell still depends on adwaita-icon-theme-full.
This may not be intended, though, I don't know.

About gnome-themes-standard, it seems that Thunderbird still needs it.
It looks terrible without g-t-s (I use the adwaita theme on my setup).
Firefox on the other hand doesn't need g-t-s.


I prefer gnome-backgrounds, so I still use it.
The installation of ubuntu-wallpapers did not change anything.

---

### Post by jbicha on 2017-04-26
"gnome-themes-standard" is the GTK2 part of Adwaita. (GTK3 itself includes the GTK3 part of Adwaita).

Ubuntu's thunderbird still uses GTK2 but I'm told version 52 will switch to GTK3.

Thanks for mentioning the remaining adwaita-icon-theme-full dependency.

Some of these changes are just to make it easier for gnome-shell to get into main. Some of the changes are temporary. There are a lot of decisions that haven't been made yet.

---

### Post by harry332 on 2017-04-26
Thanks for info Jeremy.

---

