---
title: "How to get to Unity dock without windows button?"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kramer65 on 2012-03-02
Hello,

I've got a home pc with Ubuntu on it. Before this I was running Ubuntu 10.04 but I just upgraded to version 12.04 beta 1.

For my work (I'm a freelancer) I often need to access my home pc from my laptop (macbook pro). For this I installed teamviewer on both machines. This used to work perfectly well.

With the new Unity interface I now get into trouble. I've got the Unity dock on the left (or how do you call that thing?) set to automatically hide. When I log in with teamviewer however, I can't put the mouse pointer exactly to the left of the screen from my laptop, and because I also don't have a windows button on my mac laptop I am totally unable to reach the Unity dock or dash.

Any idea how I would be able to open any program from within a teamviewer remote desktop session?

All tips are welcome!

---

### Post by forrestcupp on 2012-03-02
Doesn't the Mac command key work like the Windows key?

---

### Post by Lisiano on 2012-03-02
If you are using Unity3D by default, you can start up a 2D launcher which shouldn't hide unless you tweaked the Unity2D settings too.
Open a terminal (Ctrl+Alt+T) and type this
```
unity-2d-launcher
```

PS: To answer directly if there are other ways to open programs: Yes, my favourite being the terminal.

PPS: If for some reason TeamViewer doesn't allow you to open a terminal using Ctrl+Alt+T, try to open any folder on the desktop or click anywhere on your desktop and hover your mouse over the top panel, click File -> New Window and go to this directory
```
/usr/share
``` and double click this file
```
gnome-terminal
```
Or open the Unity2D launcher using it, it's in the same folder.

---

### Post by sffvba[e0rt on 2012-03-03
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by alphacrucis2 on 2012-03-03
You can turn the launcher auto-hide off. Top right hand 'power' button - select System Settings - Appearance. Select Behaviour tab.

---

### Post by kyrealtor on 2012-03-08
> **kramer65 said:**
> Hello,
 
I've got a home pc with Ubuntu on it. Before this I was running Ubuntu 10.04 but I just upgraded to version 12.04 beta 1.
 
For my work (I'm a freelancer) I often need to access my home pc from my laptop (macbook pro). For this I installed teamviewer on both machines. This used to work perfectly well.
 
With the new Unity interface I now get into trouble. I've got the Unity dock on the left (or how do you call that thing?) set to automatically hide. When I log in with teamviewer however, I can't put the mouse pointer exactly to the left of the screen from my laptop, and because I also don't have a windows button on my mac laptop I am totally unable to reach the Unity dock or dash.
 
Any idea how I would be able to open any program from within a teamviewer remote desktop session?
 
All tips are welcome!
Great question & answers!
I had been hoping that someone would use the Start (Windows) button to bring up a menu (I have several dual-book PCs & two formerly Windows PC that now have only Ubuntu Linux). Unity finally does this, but it is now clear that there should be an alternative keystroke that does the same thing, perhaps using the Alt or Ctrl Keys.
I will remember this issue if it comes up under Kubuntu, Xubuntu, Lubuntu, and the desktop forums for KDE, Gnome, XFCE, and LXDE.
 
Basically, it would be nice if the Unity guys would give you an easier fix before the Feature Freeze deadline. It would also be an improvement to the other desktops if we could use that key on keyboards that have it.

---

### Post by cariboo on 2012-03-08
> **kyrealtor said:**
> Great question & answers!
I had been hoping that someone would use the Start (Windows) button to bring up a menu (I have several dual-book PCs & two formerly Windows PC that now have only Ubuntu Linux). Unity finally does this, but it is now clear that there should be an alternative keystroke that does the same thing, perhaps using the Alt or Ctrl Keys.
I will remember this issue if it comes up under Kubuntu, Xubuntu, Lubuntu, and the desktop forums for KDE, Gnome, XFCE, and LXDE.
 
Basically, it would be nice if the Unity guys would give you an easier fix before the Feature Freeze deadline. It would also be an improvement to the other desktops if we could use that key on keyboards that have it.

There is a whole list of keyboard short-cuts available in Unity, by holding down the Windows key

---

### Post by ronacc on 2012-03-08
it would be a good suggestion to have an option to have unity recognise the mac cmd key as a windows key .

---

### Post by mc4man on 2012-03-08
> **ronacc said:**
> it would be a good suggestion to have an option to have unity recognise the mac cmd key as a windows key .
That would be the best way (if not already
The Show launcher can be rebound to either a key combo or single key if not a modifier but likely to cause far more trouble than worth

(just noticed that the "keyboard short-cuts" screen is dynamic, didn't think it used to be.

An alternative could be to make use of a basic toggle script & use it to hide/unhide the launcher thru any binding you wish, whether key, mouse, edge, whatever 
(though like anything concerning unity/compiz & repeated non-standard use...

What I use here is this, sometimes thru a click on Desktop launcher, lately thru an edge binding, (bottom right), & a key, (menu button which I've never used)  in ccsm > commands, the command simply being toggle1
```

mkdir -p ~/bin && gedit ~/bin/toggle1
```

```
#!/bin/bash
key_value=$(gconftool --get /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode)
echo $key_value | grep "0"
if [[ $? -eq 0 ]] ; then
gconftool --type Integer --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 1
else
gconftool --type Integer --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 0
fi
```
```

 chmod +x ~/bin/toggle1
```
A restart adds ~/bin to PATH if not already

---

