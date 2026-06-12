---
title: "Menu In Panel"
date: 2013-06-20
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-06-20
Is their a way to have an Applications Menu show permanently in the Panel Mac OSX style instead of Auto Hide once you move the curser away?

I'm using 13.10 BTW.

Roland

---

### Post by zika on 2013-06-20
CCSM>Unity>Launcher>Hide_Launcher>Never
If I understood Your question right...

---

### Post by grahammechanical on 2013-06-20
I am not sure of what you want to do, either. But you could always experiment with this:

[http://www.omgubuntu.co.uk/2013/03/gnome-3-8-released](http://www.omgubuntu.co.uk/2013/03/gnome-3-8-released)

or see if this still works.

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

Regards.

---

### Post by roly33 on 2013-06-20
> **zika said:**
> CCSM>Unity>Launcher>Hide_Launcher>Never
If I understood Your question right...

> **grahammechanical said:**
> I am not sure of what you want to do, either. But you could always experiment with this:

[http://www.omgubuntu.co.uk/2013/03/gnome-3-8-released](http://www.omgubuntu.co.uk/2013/03/gnome-3-8-released)

or see if this still works.

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

Regards.

I mean this menu

[ATTACH=CONFIG]243980[/ATTACH]

The default setting is for it to Auto Hide when you move the mouse away, and I find it slows productivity down having to wait for the Menu to fade in when placing the mouse on the panel.

Roland

---

### Post by zika on 2013-06-20
> **roly33 said:**
> I mean this menu

[ATTACH=CONFIG]243980[/ATTACH]

The default setting is for it to Auto Hide when you move the mouse away, and I find it slows productivity down having to wait for the Menu to fade in when placing the mouse on the panel.

RolandThen You should try CCSM as as I wrote...

Update&#8321;: It seems that I missunderstood You... If GlobalMenu is in Your question then rhere are solutions below...

---

### Post by howefield on 2013-06-20
Try in terminal..

```
sudo apt-get remove indicator-appmenu
```

You'll probably need to log out and back in.

---

### Post by philinux on 2013-06-20
> **roly33 said:**
> 
The default setting is for it to Auto Hide when you move the mouse away, and I find it slows productivity down having to wait for the Menu to fade in when placing the mouse on the panel.

Roland
That's the global menu.

Fades in instantly here no delay at all. What graphics card have you?

---

### Post by jfernyhough on 2013-06-20
It's a usability issue, but it's by design. There are a load of "won't fix" bugs for exactly this issue. Canonical have made the decision that the menu will fade out no matter what.

To gain control over your menu you have to use a recompiled version of Unity which patches this behaviour.

---

### Post by roly33 on 2013-06-21
> **philinux said:**
> That's the global menu.

Fades in instantly here no delay at all. What graphics card have you?


My Graphics Card is a Mobile Intel GM45 Express.

Roland

---

### Post by roly33 on 2013-06-21
> **howefield said:**
> Try in terminal..

```
sudo apt-get remove indicator-appmenu
```

You'll probably need to log out and back in.

That sort of worked, but it didn't have the desired look I was looking for.  How do I return to the default Ubuntu Global Menu behaviour?

Roland

---

### Post by dino99 on 2013-06-21
> **roly33 said:**
> That sort of worked, but it didn't have the desired look I was looking for.  How do I return to the default Ubuntu Global Menu behaviour?

Roland

stay tuned with the past :confused:

---

### Post by philinux on 2013-06-21
> **roly33 said:**
> That sort of worked, but it didn't have the desired look I was looking for.  How do I return to the default Ubuntu Global Menu behaviour?

Roland

```
sudo apt-get install indicator-appmenu
```

---

