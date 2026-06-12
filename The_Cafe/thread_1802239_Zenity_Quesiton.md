---
title: "Zenity Quesiton?"
date: 2011-07-11
forum: The Cafe
---

### Post by LowSky on 2011-07-11
For giggles can you guys/girls have a file named:

```
/usr/share/zenity/zenity.ui
```

I seem to be missing mine, or I should say the entire zenity files within the folder are missing,  and it causing a few headaches

Does the file exist on your installs?

---

### Post by Tibuda on 2011-07-11
> **LowSky said:**
> For giggles can you guys/girls have a file named:

```
/usr/share/zenity/zenity.ui
```

I seem to be missing mine, or I should say the entire zenity files within the folder are missing,  and it causing a few headaches

Does the file exist on your installs?

yep
```
% ls /usr/share/zenity/          
clothes              zenity-list.png          zenity-scale.png
zenity-calendar.png  zenity-notification.png  zenity-text.png
zenity-entry.png     zenity.png               zenity.ui
zenity-file.png      zenity-progress.png

```
try to reinstall the package.


I have heard of someone who got an empty /usr/bin/mplayer file. Weird bugs.

---

### Post by LowSky on 2011-07-11
Nevermind, I stole the files from another machine and now things seem to be working fine. Even a reinstall didn't fix it. I grabbed the files from my netbook running Arch and Gnome 3.. seems to do the job just fine on Ubuntu 11.04

---

