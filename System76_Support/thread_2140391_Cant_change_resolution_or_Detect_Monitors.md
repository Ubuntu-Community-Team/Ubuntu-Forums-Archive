---
title: "Cant change resolution or Detect Monitors"
date: 2013-04-29
forum: System76 Support
---

### Post by nickmc01 on 2013-04-29
Hello I just upgraded to 13.04. Everything was working fine last night after the update and several reboots. Today, I plugin my VGA, and reboot the laptop (gazzell professional) and I get a mirrored display when its normally just extended. I go to change it back and it doesnt show up in Display settings. I tried detect displays and nothing happens. I also am unable to change the resolution on the laptop itself. Any help would be appreciated.

---

### Post by isantop on 2013-04-29
Can you post a screen shot of your Display Settings window?

---

### Post by nickmc01 on 2013-04-29
[IMG]http://is.gd/zb8Ab1[/IMG]

Thats with the monitor plugged into VGA. The dropdown doesnt have any other resolutions.

[IMG]http://is.gd/W9tPdR[/IMG]

Also Something I noticed.

---

### Post by isantop on 2013-04-29
What sort of modifications have you made? It looks like your graphics system isn't loading properly.

---

### Post by nickmc01 on 2013-04-29
Non just installed gnome classic, and some themes so far.

---

### Post by nickmc01 on 2013-04-29
UPDATE: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"

is that possibly the issue?

---

### Post by isantop on 2013-04-29
I would go back to Unity, just for testing. You should also remove all of the GRUB options after "quiet splash". They aren't necessary.

---

### Post by nickmc01 on 2013-04-29
Switched to unity, still the same issue.

---

### Post by philbert on 2013-04-29
I have the same issue and behavior after the upgrade as well as after a clean install.

---

