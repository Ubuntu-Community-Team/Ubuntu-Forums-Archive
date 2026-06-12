---
title: "Gloabl menu in Ubuntu 13.10"
date: 2013-09-08
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-09-08
It seems that the tweak to disable global menu in ubuntu 13.04, does not work in 13.10  So any ideas on how to disable?

Henry

---

### Post by wch on 2013-10-04
This worked for me:

```
sudo apt-get remove indicator-appmenu
```

---

### Post by osarusan on 2013-10-19
That works, but only partially... some of my windows now have their menus visible, while others now have no access to menus at all... nautilus being one of them.

---

### Post by mc4man on 2013-10-19
> **osarusan said:**
> That works, but only partially... some of my windows now have their menus visible, while others now have no access to menus at all... nautilus being one of them.

run this in terminal
```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'
```

---

### Post by jdorenbush on 2013-10-25
> **mc4man said:**
> run this in terminal
```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'
```

Thank you! That works great.

---

