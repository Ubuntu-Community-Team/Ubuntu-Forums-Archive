---
title: "How to install desktop environment in ubuntu server"
date: 2008-03-16
forum: Server Platforms
---

### Post by ykongbam on 2008-03-16
I am a beginner...
i have a server which has ubuntu installed
i wanted to ask if i can install any desktop environment like Gnome, KDE etc..etc
if yes, How???
thnx in advance

---

### Post by Koybe on 2008-03-16
You can install the metapackage :
```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop (for kde)
```But then you go to a desktop install, not a server one.

You can also install just what you need, for example :
```
sudo apt-get install x-window-system-core gdm gnome
``` so you won't get openoffice and other stuff.

---

### Post by SuperMiguel on 2008-03-16
does install a desktop environment slow ur server down?

---

### Post by Koybe on 2008-03-17
Of course installing a desktop environement means more services, means more ram used, means more cpu used... etc.

---

### Post by badperson on 2008-03-20
so if you hit

```
sudo apt-get install ubuntu-desktop
```

then at that point do you not have a lamp install, you have the regular ubuntu desktop edition? Not a server edition?
bp

---

