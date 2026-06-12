---
title: "Login Screen Bg... Can you change it?"
date: 2005-07-22
forum: The Cafe
---

### Post by KrisDwyer on 2005-07-22
Hey,

Just wondering... is there anyway to change the background of the login screen?

Thanks,
~Kris~

---

### Post by Xian on 2005-07-22
Sure, you can do that by issuing the 'gdmsetup' command as sudo in a terminal.

---

### Post by bored2k on 2005-07-22
you can get more themes on gnomelook.org. If you just want to change the background go to /usr/share/gdm/themes, look for the corresponding one and replace its wallpaper with the one you want.

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=bored2k]you can get more themes on gnomelook.org. If you just want to change the background go to /usr/share/gdm/themes, look for the corresponding one and replace its wallpaper with the one you want.[/QUOTE]
 no but i mean the login screen where u enter your username and password...

---

### Post by bored2k on 2005-07-22
[QUOTE=KrisDwyer]no but i mean the login screen where u enter your username and password...[/QUOTE]
 yes that is what i meant. [http://gnomelook.org/index.php?xcontentmode=150&PHPSESSID=325c06be898f6ddf14269ef5e567cc06](http://gnomelook.org/index.php?xcontentmode=150&PHPSESSID=325c06be898f6ddf14269ef5e567cc06)

---

### Post by Xian on 2005-07-22
gdmsetup > Graphical Greeter > Install New Theme

---

### Post by jerome bettis on 2005-07-23
Re: Login Screen Bg... Can you change it?
you could do what i did and type:  sudo gimp /usr/share/gdm/themes/Human/background.png

i just made it (and that splash screen) all black. looks pretty slick imo.

---

### Post by ThatRickGuy on 2005-07-23
What about the screen in between that and the desktop? I have smooth dragon installed, which looks goot at login and on the desktop, but I have to look at the brown background while things are loading.

-Rick

---

### Post by TravisNewman on 2005-07-23
you can change that background color through gdmsetup as well. Go to the "standard greeter" tab and change the background color there. Kinda doesn't make sense since you're using the graphical greeter, but it does work.

---

