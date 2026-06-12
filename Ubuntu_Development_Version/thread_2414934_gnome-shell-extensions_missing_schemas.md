---
title: "gnome-shell-extensions: missing schemas"
date: 2019-03-17
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-03-17
With gnome-shell 3.32, a few extensions icons have been moved to the far right corner: like the clock (default), and weather (custom extension).
Seems they cant be moved/placed via dconf/tweaks as they does not have schema builtin. :(

Without a schema, the clock is not fully visible. That happen with the addition of fixed system-monitor (from github commits) wihch takes some width with displayed cores; but  was displayed as expected with previous gnome 3.30

---

### Post by paulycalvin on 2019-03-17
My advice is to uninstall all gnome-shell-extensions that you _**[COLOR=#ff0000]personally[/COLOR]**_ installed by going into local/share/gnome-shell/extensions and usr/share/gnome-shell/extensions and removing the extensions. Then install the extensions in the Ubuntu repositories. _**[COLOR=#ff0000]Don't remove[/COLOR]**_ any extensions in usr-share if they were installed by _[COLOR=#ff0000]**default**[/COLOR]_. it seems that if you have extensions form different sources they will create weird bugs.

---

### Post by dino99 on 2019-03-23
Some upgrades have resolved that problem. Only the weather icon has moved to the right. But none are hovering now; way better :)

---

### Post by P-I H on 2019-03-23
The extensions I'm using are also working OK now.

---

### Post by Chazall1 on 2019-03-23
All working here as well

---

