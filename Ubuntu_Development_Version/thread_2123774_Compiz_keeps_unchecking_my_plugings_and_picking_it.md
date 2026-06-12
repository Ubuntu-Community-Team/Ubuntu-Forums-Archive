---
title: "Compiz keeps unchecking my plugings and picking its own"
date: 2013-03-08
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-03-08
i have started a serious test on my desktop (been testing my notebook)
i am really happy to see so many fixes in compiz, it now even has default settings again, but every time it re-stares i have to re check my boxes in ccsm
anyone know a way to make it keep the plugins enabled?

[s]anyone know how to change the theme in the compiz window decorator? also how to add the menu icon to the bar (like what people would use to move the buttons to the right)[/s]
```
gsettings set org.gnome.desktop.wm.preferences button-layout 'menu:minimize,maximize,close'
gsettings set org.gnome.desktop.wm.preferences theme 'Albatross'
```

---

### Post by serdotlinecho on 2013-03-09
@[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458"), do you have this directories in your Home?

```
~/.cache/compizconfig-1
~/.compiz
```

---

### Post by pqwoerituytrueiwoq on 2013-03-09
i do, but it have it working now i did some playing with the import export stuff in ccsm and it is holding

---

### Post by screaminj3sus on 2013-03-09
I had this happen too with xubuntu + compiz. Strange thing is, after I rebooted a few times eventually it just unchecked *every* plugin by itself, and then after that happened when I re-enabled all the ones I wanted it acted fine every since, keeping my settings. I reproduced this once on a clean install too, pretty odd lol.

---

