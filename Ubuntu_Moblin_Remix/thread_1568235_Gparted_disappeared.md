---
title: "Gparted disappeared?"
date: 2010-09-04
forum: Ubuntu Moblin Remix
---

### Post by Microsoft Hater on 2010-09-04
Hey, I just replaced garbage XP with ubuntu on my Acer One last week and I just noticed today that GParted magically uninstalled itself - has anyone else noticed this problem?
 
When I search for 'gparted', i get only 5 files that appear:
 
gparted.desktop    at     /usr/share/app-install/desktop
gparted.png          at     /usr/share/app-install/icons
gparted.mo           at     /usr/share.locale-langpack/en_AU/LC_MESSAGES
gparted.mo           at     /usr/share.locale-langpack/en_CA/LC_MESSAGES
gparted.mo           at     /usr/share.locale-langpack/en_GB/LC_MESSAGES
 
and those five files only take up about... 6.7kb from a 3gb program. Disappeared! Any ideas what's up?

---

### Post by krimzonstarr on 2010-09-05
GParted is included on the LiveCD/LiveUSB, but not in the fully installed versions. This is easily remedied in the CLI with
```
sudo apt-get install gparted
```

Gparted was my favorite disk utility, until "Disk Utility" became a default installed app.

---

### Post by Microsoft Hater on 2010-09-05
I have disk utility still - is that more useful? Personally so far I've found it less user-friendly, or has less options. Maybe I just like the colours. :)
 
I had installed Gparted with package manager, or it installed automatically, I honestly don't remember but it magically disappeared?!? That's the weird part.
 
I'll look into Disk Utility more....

---

