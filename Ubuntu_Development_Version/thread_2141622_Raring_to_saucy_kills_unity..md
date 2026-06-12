---
title: "Raring to saucy kills unity."
date: 2013-05-03
forum: Ubuntu Development Version
---

### Post by Zestypanda on 2013-05-03
Ok, first let me say that I foolishly jumped the gun and did a dist-upgrade to saucy way too easily and fried my raring machine, is there someway I can fix my unity so I don't have to reinstall? When I start it, no matter what kernel I pick from grub it does not load unity.

---

### Post by lisati on 2013-05-03
*Thread moved to **Ubuntu +1**.*

---

### Post by dino99 on 2013-05-03
i suppose compiz have crashed, so restore it from a terminal:

compiz --replace ccp &
setsid unity

---

### Post by Zestypanda on 2013-05-03
I've done that already, no dice.

---

### Post by grahammechanical on 2013-05-03
It is difficult to say because you do not tell us what you do get. Do you get to a desktop with a background wallpaper but no top panel or launcher? Does Ctrl+Alt+T bring up the terminal? And do not forget that none of us are experts on Saucy Salamander. This is just as much an experiment to us as it is to you.

If you get to a background wallpaper, then right click it and select Change Desktop Background. That will load System Settings and from there you can open Additional Drivers and experiment with another video driver in case that is the problem.

Reset unity with

```
dconf reset -f /org/compiz/
```

to reset Compiz and

```
setsid unity
```

to reset Unity. Do not forget to reboot. And browse through this thread and may I suggest that if you are going to run Saucy Salamander this early that you collect a tool kit of useful commands.

[http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435)

Regards

---

### Post by Zestypanda on 2013-05-03
Ok, so I did that, I tried installing the open source drivers, no dice.

---

### Post by Zestypanda on 2013-05-03
yaaaay It's working, I'm gonna post the code of the output window soon. Lots of errors .-. but reseting unity/the dconf seemed to get it to work.

---

### Post by Zestypanda on 2013-05-03
Oh, well apparently the terminal windows closed too soon :(

---

### Post by Zestypanda on 2013-05-03
Ok, to consolidate it, I uninstalled proprietary drivers, installed default, reset unity and compiz. It works now so I'm gonna trouble shoot and see if it's a problem with proprietary and the 3.9 kernel or something else.

---

### Post by Zestypanda on 2013-05-03
Yup, the problem is that proprietary does not support saucy yet (shocking) so by upgrading it broke it.

---

