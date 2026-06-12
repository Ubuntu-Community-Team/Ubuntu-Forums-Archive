---
title: "Eagle USB on Kubuntu"
date: 2005-04-26
forum: Repositories &amp; Backports
---

### Post by eltower on 2005-04-26
Hey.
I installed kubuntu (coz i prefer KDE). Now, it doesn't recognise my ADSL Comtrend CT350 modem, which works with the Eagle USB packages. 
However, while playing around with the CD, I noticed that there were Eagle USB packages in the /pool folder. When i started up Kynaptic, the options for Eagle USB were unchecked, and when I checked them, and pressed 'Commit changes to computer', Kynaptic just crashes. I assume its because it tries to connect to the net, but I can't because I need the Eagle USB packages to get my modem working!

Is there a way to select which packages to install during the installation? I tried 'expert' mode, but this doesn't help, as I still do not get the option. 

Any help would be greatly appreciated.

eltower

---

### Post by Firetech on 2005-04-26
Kynaptic is pretty incomplete, which is pretty bad :(
Try noting down the name(s) of the package(s) you want to install, then open Konsole (K Menu > System > [sometext] (Konsole)). In Konsole type:
```
sudo apt-get install [package-name(s)-here]
```
If you don't have your CD in the drive, it will ask you for it. If it doesn't, make sure you've got a CD entry in /etc/apt/sources.list (probably on the first line). If you don't have a CD-line, post a reply. (phew... many If's :D)

When you get your modem working, install synaptic if you want a package installer GUI (personally, I prefer apt-get). It has GNOME look, but it's more complete than kynaptic...

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=eltower]
Any help would be greatly appreciated.

eltower[/QUOTE]

You want to install synaptic. you also need the qt gtk package. put this in terminal:

sudo apt-get install synaptic  gtk2-engines-gtk-qt

---

