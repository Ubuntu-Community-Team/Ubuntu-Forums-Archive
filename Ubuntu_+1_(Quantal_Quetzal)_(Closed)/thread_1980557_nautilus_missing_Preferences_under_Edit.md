---
title: "nautilus missing Preferences under Edit"
date: 2012-05-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VMC on 2012-05-15
Is it just my install?

I'm missing Edit > Preferences.

Just checking before bug report.

Thanks

---

### Post by JMB74 on 2012-05-15
I have it on v 3.5.1 that was recently uploaded.

---

### Post by VMC on 2012-05-15
I should have stated its a new install only. 

Dated: ```
quantal-desktop-amd64.iso 15-May-2012 08:42 711M
```

---

### Post by mc4man on 2012-05-15
Missing here - ends on "Move to Trash"

 likely other 'missing' atm  - some of this
>       NAUTILUS_ACTION_NEW_WINDOW,
> 	NAUTILUS_ACTION_CONNECT_TO_SERVER,
> 	NAUTILUS_ACTION_PREFERENCES,
> 	NAUTILUS_ACTION_HELP,
> 	NAUTILUS_ACTION_ABOUT,
> 	NAUTILUS_ACTION_CLOSE_ALL_WINDOWS,

edit
you never know with gnome whether it's something someone decided to make not visible or maybe some gtk change not yet implemented or whatever, - can't see why they'd be made not visible so would expect to show up at some point

---

### Post by Yellow Pasque on 2012-05-15
OP filed bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/999827](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/999827)

---

### Post by ronacc on 2012-05-15
mee too'd the bug and added SS that was requested by sebastien .

---

### Post by VMC on 2012-05-15
> **ronacc said:**
> mee too'd the bug and added SS that was requested by sebastien .

Thanks. I was trying to use apport-bug but it failed on id`ing the package.

Edit: As a godawful work around, I used dconf editor and 'org.gnome.nautilus.preferences' to change preferences. This will most likely be fix for tomorrows iso install.

---

### Post by xebian on 2012-05-15
I see this missing 'edit/prefernces' only in unity/gnome-shell session but it's there in cinnamon/lxde/xfce session as well as the 'Help' menu.

---

### Post by mc4man on 2012-05-16
The menu items are in gnome-shell, just not in nautilus - seen in the application menu (drop down from "Files" in panel

---

### Post by zika on 2012-05-16
No Edit>Preferences in Nautilus (while in Unity)... I'll check in other environments later...

---

