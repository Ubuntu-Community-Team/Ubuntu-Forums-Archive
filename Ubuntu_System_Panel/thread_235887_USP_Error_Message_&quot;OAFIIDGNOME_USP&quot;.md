---
title: "USP Error Message: &quot;OAFIID:GNOME_USP&quot;"
date: 2006-08-13
forum: Ubuntu System Panel
---

### Post by Uncle Spellbinder on 2006-08-13
I get multiple error messages when trying to add the USP to the panel. Here's the kicker. It also happens when trying to add *anything* to the panel. 

Ideas???

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/applet.png[/IMG]

---

### Post by cantormath on 2006-08-13
> **Uncle Spellbinder said:**
> I get multiple error messages when trying to add the USP to the panel. Here's the kicker. It also happens when trying to add *anything* to the panel. 

Ideas???

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/applet.png[/IMG]

What did you change or do before this started happening....
ie) change your hostname, install something,......etc.

---

### Post by Uncle Spellbinder on 2006-08-13
> **cantormath said:**
> What did you change or do before this started happening....
ie) change your hostname, install something,......etc.

Oooops. Sorry. Just a bit frustrated....

I reinstalled totem. Something about gnome desktop flashed after the re-install. I rebooted and immediately the messages started.

---

### Post by cantormath on 2006-08-13
> **Uncle Spellbinder said:**
> Oooops. Sorry. Just a bit frustrated....

I reinstalled totem. Something about gnome desktop flashed after the re-install. I rebooted and immediately the messages started.

How did you go about reinstalling, synaptic?
did you get any errors when you did this, other then the pop up window?

maybe something broke as you were installing something
could try
```
laptop:~$ dpkg --configure -a
```
Another thing,
For setting up players/Video/DVD/Flash/java/Codecs and other cool programs
easy way
(x)ubuntu
Code:
```
http://ubuntuforums.org/showthread.php?t=190025
```
kubuntu
Code:
```
http://www.ubuntuforums.org/showthread.php?t=203294
```
manually
```
http://ubuntuguide.org/wiki/Dapper
```

---

### Post by Uncle Spellbinder on 2006-08-13
> **cantormath said:**
> How did you go about reinstalling, synaptic?
did you get any errors when you did this, other then the pop up window?

maybe something broke as you were installing something
could try
```
laptop:~$ dpkg --configure -a
```

I just tried *dpkg --configure -a*, nothing changed. I already have, and just used Automatix, to try and reinstall again. Used Synapric initially. The message regarding *gnome desktop* was so quick, I could not read it. Other than that, just the popups each time I try to add USP or anything to the panel.

---

### Post by Uncle Spellbinder on 2006-08-13
Have no clue how it happened, but somehow reinstalling totem borked everything up. I figured I'd try *sudo aptitude install ubuntu-desktop*. This worked as the missing packages were installed:

```
Setting up python2.4-gnome2-desktop (2.14.0-0ubuntu2) ...

Setting up python-gnome2-desktop (2.14.0-0ubuntu2) ...
Setting up deskbar-applet (2.14.2-0ubuntu1) ...

Setting up gtk2-engines-highcontrast (2.7.4.is.2.6.10-0ubuntu1) ...
Setting up gnome-accessibility-themes (2.14.3-0ubuntu1) ...

Setting up python-beagle (0.2.6-1ubuntu5) ...
Setting up serpentine (0.6.91-0ubuntu3) ...

Setting up totem-gstreamer (1.4.3-0ubuntu1) ...

Setting up totem (1.4.3-0ubuntu1) ...
Setting up ubuntu-desktop (0.120) ...
```

Rebooted, all is well. Now re-installing Compiz.

---

### Post by mat on 2006-08-14
Also try running usp from a terminal:
```
usp run-in-window
```

It helps figuring out what the problem is.

---

### Post by mat on 2006-08-14
> **Uncle Spellbinder said:**
> 
```
Setting up python2.4-gnome2-desktop (2.14.0-0ubuntu2) ... 
```


FWIW, this was probably the culprint.

---

