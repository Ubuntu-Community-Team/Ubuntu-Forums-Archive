---
title: "Evolution of Compiz: Desktop Environment"
date: 2009-05-18
forum: The Cafe
---

### Post by Regenweald on 2009-05-18
I think this may be the next logical step for the compiz project. The 9.xx series is being re-written in C++ for speed and stability, Compiz already does many things quite effeciently: Workspace management, Window Decoration, Desktop Effects...

I believe this project can evolve into a wonderful DE.
My pics for additional components:
Dolphin - File Manager
Cairo Dock (although Docky is my one and only)
Emerald - Window Manager
Hydroxygen - default Icon theme

I know such an endeavour would be a huge undertaking for a small group of developers, but I believe that if this project were to seriously push towards a DE and reached out to the community, they would receive positive feedback. They already have one dedicated tester here :)

I know that many view compiz with disdain, and regard it as fluff, but as a person who uses compiz not for effects (on-board graphics here) but for the functionality it offers, I would like to see it move on to the next level of development successfully.

I'll throw in a simple poll, what do you think ?

---

### Post by Giant Speck on 2009-05-18
As long as Compiz still retained their current composition manager so that I can continue using it in GNOME, I wouldn't mind seeing the development of a Compiz DE.

---

### Post by stwschool on 2009-05-18
Frankly Compiz first needs to become stable before it starts over-extending itself in other directions.

---

### Post by Regenweald on 2009-05-18
> **Giant Speck said:**
> As long as Compiz still retained their current composition manager so that I can continue using it in GNOME, I wouldn't mind seeing the development of a Compiz DE.

But what do you think of Gnome 3.0 ? it's basically locking out compiz at this point, but development is very early and anything could happen between now and the 3.0 release.

@stwschool: Hence the 9.xx work currently being done. The devs have said that the only further work on the8.xx series will be bugfixes and stability.

---

### Post by Xbehave on 2009-05-18
compiz have been limiting themselves for a long time, they haven't playd nice as a cross DE solution and so as DE implement the usefull parts of compiz themselves it will have to go somewhere (i just hope that kde and gnome also extentions to be easliy ported to/from compiz). 

Compiz effects should be implelemtned at WM level, so compiz should just concentrate on playing nice with all DEs, native WMs will catch up and compiz will slowly die out but i don't see that as a bad thing aslong as the fucntionality is not lost!

---

### Post by billgoldberg on 2009-05-18
It won't happen.

And the software you mention as the default for the DE is rubbish.

---

### Post by monsterstack on 2009-05-18
You chaps should have a look at Elive's [Compiz]("http://www.elivecd.org/Download/e17-compiz") [elivecd.org] distro. They've only gone and managed to get the E17 window manager working with Compiz. Well I say! If it can be done for Enlightenment, it should be done for others, too.

---

### Post by Regenweald on 2009-05-18
> **monsterstack said:**
> You chaps should have a look at Elive's [Compiz]("http://www.elivecd.org/Download/e17-compiz") [elivecd.org] distro. They've only gone and managed to get the E17 window manager working with Compiz. Well I say! If it can be done for Enlightenment, it should be done for others, too.

Effects like that on a netbook are quite impressive, E17 will become a serious contender next year once they get to a stable 1.0 hopefully in December. 
Ubuntu 10.04 minimal, E17, compiz 9.x series..... Interesting times :)

---

### Post by swoll1980 on 2009-05-18
Why did I think Compiz development was dead? I must have been misinformed.

---

### Post by Regenweald on 2009-05-18
> **swoll1980 said:**
> Why did I think Compiz development was dead? I must have been misinformed.

Severly misinformed :) check out compiz.org

---

### Post by binbash on 2009-05-18
> **Xbehave said:**
> compiz have been limiting themselves for a long time, they haven't playd nice as a cross DE solution and so as DE implement the usefull parts of compiz themselves it will have to go somewhere (i just hope that kde and gnome also extentions to be easliy ported to/from compiz). 

Compiz effects should be implelemtned at WM level, so compiz should just concentrate on playing nice with all DEs, native WMs will catch up and compiz will slowly die out but i don't see that as a bad thing aslong as the fucntionality is not lost!

Totally agree

---

### Post by stanca on 2009-10-03
I see ecomorph advancing very much and maybe even in Fluxbox WM too.

---

### Post by Tibuda on 2009-10-03
I already use Compiz as a standalone WM. You can use almost anything with it: tint2, gnome-panel, xfce-panel or nothing, nautilus, thunar or pcmanfm, metacity or emerald... I have writed a wiki entry about it: [https://help.ubuntu.com/community/CompizStandalone](https://help.ubuntu.com/community/CompizStandalone)

Perhaps a modular DE using Compiz as the WM would be a good idea (like LXDE does for Openbox).

---

### Post by SomeGuyDude on 2009-10-03
Compiz is a full-fledged WM. Throw in Compiz-Deskmenu and you're set, son. It's like Openbox with glitz.

The modular idea is neat though. I suggest:

- Compiz
- Tint2
- Compiz-Deskmenu
- PCManFM
- Wicd
- LXAppearance

---

### Post by Mehall on 2009-10-03
> **SomeGuyDude said:**
> Compiz is a full-fledged WM. Throw in Compiz-Deskmenu and you're set, son. It's like Openbox with glitz.

The modular idea is neat though. I suggest:

- Compiz
- Tint2
- Compiz-Deskmenu
- PCManFM
- Wicd
- LXAppearance

i would replace pcmanfm with thunar, as i just did in crunchbang, but i would definitely try that remix!

---

### Post by MaxIBoy on 2009-10-03
We don't need to create a new desktop. There are plenty enough tools out there that you can cobble a perfectly good desktop together out of "spare parts," so to speak-- no need to write yet another [s]tangled and inextricable[/s], excuse me, *well-integrated* set of utilities.


On the other hand, cobbling together such a desktop, then creating a "meta-package" in the repositories, would be kind of cool. A meta-package, when installed, will install all its dependencies without installing anything itself, and can be used to install large closely-related bits of software at the same time. If you've ever set up Debian or an Ubuntu Server, you know those lists of things like "LAMP Server," "Print Server," "Laptop," etc? Those are meta-packages.

---

### Post by Pogeymanz on 2009-10-03
Doesn't tint2 not work right with Compiz with multiple viewports?

The only thing I think Compiz needs to be a good DE is a good right-click root menu. Compiz-deskmenu sucks and is slow and buggy because of the way you have to call it.

Once you get a good root-menu, you can just use XFCE4-panel, PCManFM/Thunar, LXAppearance, XFCE4-Terminal/Urxvt and you're good.

EDIT: And Emerald sucks too. We need to get rid of that mess and start over with something simple but stable.

---

### Post by SomeGuyDude on 2009-10-03
> **Pogeymanz said:**
> The only thing I think Compiz needs to be a good DE is a good right-click root menu. Compiz-deskmenu sucks and is slow and buggy because of the way you have to call it.

I have it mapped to Ctrl+Space. Far more useful than "right click". :)

---

