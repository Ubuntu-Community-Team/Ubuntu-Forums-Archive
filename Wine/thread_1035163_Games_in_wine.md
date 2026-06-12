---
title: "Games in wine"
date: 2009-01-09
forum: Wine
---

### Post by matthewbrave on 2009-01-09
generally how do you install games in wine?

---

### Post by arsenic23 on 2009-01-09
Double click on the installer or type something like:
```
wine pathtoinstaller/installer.exe
```

into your terminal.

---

### Post by matthewbrave on 2009-01-09
ok i have just installed abes oddysee and the sound is jumpy and when i quit it the screen resolution goes weird

---

### Post by khelben1979 on 2009-01-09
You should follow the instructions on [this page]("http://www.winehq.org/download/deb") to have a working version of Wine.

Using the latest version of Wine would be to recommend and that you report bugs to the Wine developers. What version are you using?

I have experienced that Wine works best together with KDE. Try it if you haven't already done so.

---

### Post by Toffeeapple on 2009-01-09
I use [Playonlinux]("http://www.playonlinux.com/en/").

---

### Post by khelben1979 on 2009-01-09
From what I can see it uses the Wine application. I think you might be better off using Wine directly instead, perhaps?

Does the playonlinux offer you the ability to configure the Wine application?

Since Wine can be configured to use Win95, Win98 and Windows XP I think that this might be a place to have a look.

---

### Post by hikaricore on 2009-01-09
[http://appdb.winehq.org](http://appdb.winehq.org)

Be sure the program/game acutally runs first.

---

### Post by Toffeeapple on 2009-01-10
Playonlinux is good for me as it makes it easy to manage multiple wine prefixes with multiple versions of wine, it makes it easy to keep each game separate and tweak individually : ) thats what I use it for anyway.

It does have some scripts for installing some games but I've never used any of them.

---

### Post by jdodson on 2009-01-10
INFO: I use Hardy.

basically what I did was install wine, then from a console run "winecfg"

Most of the settings I just use from the defaults.  I think I remove all the drives and have it set them up for me automagically.

From there I pop in a game install CD, lets say Warcraft III and then right click on the setup.exe or some such.  I then associate that with wine and it opens.  Install the game from there and then I added some  -opengl switch to the launcher as some blizz games notice that only use opengl to render and not directx.

Other games like halflife2 follow similar paths minus the launcher switch.

It helps to have a NVIDIA card and stick to games that wine supports fairly well.  That or linux native games like quake4 or doom3.  I just installed the native prey and its great fun.

---

### Post by binbash on 2009-01-11
if you dont much about wine, or you are lazy i suggest using playonlinux

---

### Post by some1udontknow on 2009-01-12
or you can do what i do, install the game on a windows pc, get it to work with no disc and make sure it is now portable, then stick it onto your flash drive and plug it into a linux pc, and find the exe file. I only do this tho because i dont have a cd-rom (i got ubuntu on a mini-notebook). i got some great games such as warcraft 3 and the doom95 games working by this

---

