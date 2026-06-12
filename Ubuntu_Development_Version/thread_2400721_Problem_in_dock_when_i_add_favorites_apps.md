---
title: "Problem in dock when i add favorites apps"
date: 2018-09-09
forum: Ubuntu Development Version
---

### Post by zetita14 on 2018-09-09
Hi, im having issues at the moment of adding some favorite apps to the dock like the video one for example.
im having this issue since ubuntu 18.04 with gnome and i dont know why? :confused::(
i appreciate your help. :)
[ATTACH=CONFIG]281026[/ATTACH]

---

### Post by RobGoss on 2018-09-09
Hello and welcome, what seems to be the problem you don't really give much information

---

### Post by zetita14 on 2018-09-09
the problem is that when i add an app to favorites in the dock, the icon of the app appears twice like in the attached image.
i installed ubuntu and i didnt touched anything else.

---

### Post by RobGoss on 2018-09-09
I'm assuming you're using Gnome's desktop correct? The screen shot you posted could not be accessed

---

### Post by deadflowr on 2018-09-09
You need to remove the current attachment and post one that complies with the forums list of acceptable file extension formats.
(If you use Reply to Thread or Go Advanced, go down and there will be a section marked Manage Attachments which shows what file extension types are doable.
Also double check the extension isn't cutoff, like it reads as pn instead of png, or something like that.)

---

### Post by zetita14 on 2018-09-09
the attached photo to my problem

---

### Post by RobGoss on 2018-09-09
Have you tried removing that icons **completely** and then adding it again to see if it adds only one

---

### Post by mc4man on 2018-09-09
you likely have 2 desktop files for Videos (totem
what's this show
```
gsettings get org.gnome.shell favorite-apps
```

---

### Post by corradoventu on 2018-09-11
try to remove the second one

---

