---
title: "Low experience, low resources"
date: 2005-05-10
forum: The Cafe
---

### Post by benplaut on 2005-05-10
i am quite happy with Hoary, but it might not work very well for my school project. My school, like many others, started with Win 98, and then did their most recent upgrade to XP last year (a bunch of Emachines).

luckily, my school is a project based charter school, so a few freinds and myself decided to start a project to recycle the old Win 98ers, which are in pretty bad condition. Becuase of my lack of budget to learn about hardware, i was put in charge of software and OS.

Like any decent *NIX user, i think it makes sense to, to quote one of the memebers of the project, "zippify" the computers. Since they will be sold to students, and we aren't providing tech support, we want to put on something that is a windows clone. Mandrake, Fedora, or SuSE, so what can i put on?

i am thinking torwards Ark Linux. It doesn't have much of a user base, but the 'Mission Control' is very nice.

Any thoughts on the matter?

(500MHz celerons with 128mb RAM)

---

### Post by defkewl on 2005-05-10
Try using Gentoo. It is a source distribution and it is recomendable for low resource computer. For the window manager use the ones that doesn't take much resources such as xfce.

---

### Post by poofyhairguy on 2005-05-10
Ubuntu would even work. Just don't use Gnome, use XFCE. Will work GREAT.


Just use Gnome tools when you need them.

---

### Post by Knome_fan on 2005-05-10
Hm, I don't think giving gentoo to users new to linux is a good idea.

You could try [http://www.vectorlinux.com/](http://www.vectorlinux.com/)
I never tried it, but from what I read, it sounds like what you are looking for.

---

### Post by benplaut on 2005-05-10
i have looked extensively into Vector Linux (for myself), but it isn't exactly what you would call newbie-ready (from what i've read)

keep in mind, the users of these computers don't even necesarily know what linux even is...  :roll: 

ubuntu was, obviously, my first thought, except it is not all that lightweight (never tried it, personally, on a low resource machine, so i'll check on that), and not all that easy to configure, from the standpoint of a Win XP user...

25 seperate programs from a menu? i control panel would be much better for newbies.

---

### Post by az on 2005-05-10
On a 500 Mhz machine, Ubuntu is still competitive with windows.

I can be more productive on a machine like that than on a Windows based-computer, expecially when you take into account the freezes you get when you work with more than one app at a time in Win98...

A low-ressource machine, to me, is more like a 300 Mhz machine with 64 megs or less of ram.

---

### Post by somuchfortheafter on 2005-05-10
well i have hoary running as a server on a 400mhz with 128mb of ram, its slow but i mainly ssh into it anyway, i will look into xfce and see how that turns out.

---

### Post by WildTangent on 2005-05-10
do a server install, and then when you login (in text mode)

```
sudo apt-get install xfce4
```
someone correct me if that code is wrong...
this will ensure you only install xfce, so theres no wasted space being used up

-Wild

---

### Post by weekend warrior on 2005-05-10
I have 2 systems, the older one is a Celeron 500 with 256 mem and ubuntu with Gnome runs on it like a champ. You should be able to do the same with xfce. I would say test it with a live cd. I don't like the ubuntu or gnoppix live cds at all but I can highly recommend the [ Morphix 0.5-pre4 LightGUI](http://www.morphix.org/index.php?option=com_content&task=view&id=26&Itemid=59) based on my experience with it on the celeron. It's very light and small, only 260 megs but still complete, and very well set up. It's Knoppix/debian-sid based and if it works well you can install it from the control center or go back and install ubuntu with xfce.   HTH

---

### Post by poofyhairguy on 2005-05-10
[QUOTE=azz]On a 500 Mhz machine, Ubuntu is still competitive with windows.
[/QUOTE]

Thats true. With 256mb of RAM a computer I gave  friend of mine (in order to spread Ubuntu) works like a champ.

---

### Post by az on 2005-05-10
[QUOTE=WildTangent]do a server install, and then when you login (in text mode)

```
sudo apt-get install xfce4
```
someone correct me if that code is wrong...
this will ensure you only install xfce, so theres no wasted space being used up

-Wild[/QUOTE]

I think you need to install x-windows-system-core, too.  Unless you do not have a display and will be running remotely (headless)

---

### Post by DJ_Max on 2005-05-10
If not Gentoo, try CRUX.

---

