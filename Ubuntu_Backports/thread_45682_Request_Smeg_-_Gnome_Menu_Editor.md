---
title: "Request: Smeg - Gnome Menu Editor"
date: 2005-07-01
forum: Ubuntu Backports
---

### Post by bier444 on 2005-07-01
hy

Please bring **Smeg** into hoary. smeg is now in breezy. 

it's a nice little menu editor, stable and has the necessary functionality.
actual version: 0.7.5
(homepage: [http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/))

But: Smeg uses the newest version of **python-xdg**, which is not downwards compatible. So it has a conflict with the gnome-app-install.

i've patched the **gnome-app-install-20050404a-v2** with the v3-patch and uploaded the new version to bugzilla.
([https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871))

Please bring an updated version of gnome-app-install into hoary.

bier444

p.s.: also menuadd is a candidat, but it's beta. maybe some day ....

---

### Post by rpgcyco on 2005-07-01
Smeg 0.7.4 is already in the [stable] backports and 0.7.5 is in staging.

```
sudo apt-get update
sudo apt-get install smeg
```

- Rpg Cyco

---

### Post by Slo Mo Snail on 2005-07-01
smeg 0.7.5 currently is in hoary-backports-staging... and 0.7.4 is in hoary-backports

---

### Post by offby1 on 2005-10-05
I see that this is not the case anymore -- the python-xdg dependency is still nailing installation of smeg on my end.

Is this slated to be fixed?  I would really, REALLY like to be able to edit my menus...

---

### Post by Unit #134679 on 2005-10-05
Yea, I dont see it

---

### Post by bugi on 2005-10-06
[QUOTE=bier444]hy
Please bring **Smeg** into hoary. smeg is now in breezy. 
it's a nice little menu editor, stable and has the necessary functionality.
actual version: 0.7.5
(homepage: [http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/))
But: Smeg uses the newest version of **python-xdg**, which is not downwards compatible. So it has a conflict with the gnome-app-install.
i've patched the **gnome-app-install-20050404a-v2** with the v3-patch and uploaded the new version to bugzilla.
([https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871))
Please bring an updated version of gnome-app-install into hoary.
bier444
p.s.: also menuadd is a candidat, but it's beta. maybe some day ....[/QUOTE]
Take a look at repo. There already is newer python-xdg package for Hoary :-)
[http://dev.realistanew.com/smeg/python-xdg_0.14-0ubuntu1~5.04ubp1_all.deb](http://dev.realistanew.com/smeg/python-xdg_0.14-0ubuntu1~5.04ubp1_all.deb) 
I'm using it and it works without any problems.

---

