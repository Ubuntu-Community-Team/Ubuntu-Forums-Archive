---
title: "Suggestion: Run nVidia X Server Settings with elevated priviledges"
date: 2008-11-29
forum: Ubuntu Brainstorm
---

### Post by Mutiny32 on 2008-11-29
This is more of a bug that nobody has bothered to correct. The nvidia-settings app is not run with elevated privileges by default when run from the Administration menu in Gnome. You can config all settings and apply them, but they don't stay persistent through a reboot or a restart of the xserver unless you hit that little button that says "Save to X Configuration File." Well what that does is merge or save your customizations or settings into xorg.conf. When you do this, It crashes and burns because it doesn't have the privileges to replace the backup of xorg.conf or edit xorg.conf. 

Now the workaround would be to run 
```
gksudo nvidia-settings
```
from the terminal, but your average joe has no clue how to even open a terminal window; for instance, my dad (I'm an evil son, I make my dad use linux). 

So my suggestion would be to simply run the nvidia-settings app from the Administration menu with elevated privileges just like how the update manager is run, prompting for a password.

So....anyone agree with me?:-s

---

### Post by smartboyathome on 2008-11-29
The only problem is Ubuntu *can't* modify nvidia's tool since its proprietary (this would fall under modifying, I think). NVidia would have to do this, but probably won't due to other distros using it which don't use sudo.

---

### Post by Mutiny32 on 2008-11-29
> **smartboyathome said:**
> The only problem is Ubuntu *can't* modify nvidia's tool since its proprietary (this would fall under modifying, I think). NVidia would have to do this, but probably won't due to other distros using it which don't use sudo. I'm not savvy on how the Gnome menus handle launching programs, but couldn't it just be made to launch it with elevated privs? No program modification needed.

---

### Post by Skripka on 2008-11-29
> **Mutiny32 said:**
> I'm not savvy on how the Gnome menus handle launching programs, but couldn't it just be made to launch it with elevated privs? No program modification needed.

Exactly.

All it takes is going into a menu editor (either KDE, or I presume Gnome also), and changing the terminal command of the icon shortcut from:

```

/usr/bin/nvidia-settings

```

to

```

kdesudo (gksu) /usr/bin/nvidia-settings

```

It can't be that difficult to add a script or something to change that by default--can it? :confused:

---

