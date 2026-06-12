---
title: "Messed up wallpaper when resuming from suspend"
date: 2019-11-14
forum: Ubuntu Development Version
---

### Post by bswilson on 2019-11-14
I recently upgraded to **20.04**, and for the most part everything was fine. My computer's power management setup is configured for the machine to suspend/sleep (Automatic Suspend) after 2 hours. 

However, when I power up the machine from this suspend state, the wallpaper is all jacked up (see attachment). Now, I can go into the settings and change the wallpaper, and it's all good. But I'm not sure how to troubleshoot the problem. Has anyone else seen this problem? 

Thanks.

---

### Post by uRock on 2019-11-14
Moved to ***Ubuntu Development Version*** sub-forum, since 20.04 does "release" until April.

---

### Post by bswilson on 2019-11-14
Oops, my bad!

---

### Post by ank2 on 2019-11-14
I heard about this in the usenet already. Might be a bug in Gnome. I am using a gradiant of blue instead of a wallpaper and have no problems. If the wallpaper is not important to you, change the background to a gradiant or solid color to see if this helps.

---

### Post by ajgreeny on 2019-11-14
I'm not seeing this in either Xubuntu or Kubuntu 20.04, so you may be correct about it being a gnome problem.

---

### Post by bswilson on 2019-11-25
Thanks for the reply. In the GNOME GUI, I don't seem to even have an option to choose a solid color! Weird. I had to use:

```
gsettings set org.gnome.desktop.background picture-uri none
```

to remove it completely. We'll see if that resolves the issue...

---

