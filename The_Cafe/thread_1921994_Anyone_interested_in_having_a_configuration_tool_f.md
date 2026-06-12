---
title: "Anyone interested in having a configuration tool for .lens files ?"
date: 2012-02-07
forum: The Cafe
---

### Post by cgroza on 2012-02-07
Hello everyone.

With more and more Unity lens being created, this feature gets very important.
So part of their configuration being stored in /usr/share/unity/lenses,  I thought someone would be interested in a configuration tool for them.

I have already written one in Haskell that lets you edit some basic fields but I am not sure if anyone would really need it.

Here is the github repo: [https://github.com/cgroza/LensesManager](https://github.com/cgroza/LensesManager)

I could do a 32 bit executable if someone wants it because you will need to install quite a lot of things to compile it.
I have attached a screen shot below.

---

### Post by hansdown on 2012-02-07
Looks nice, cgroza.

---

### Post by grahammechanical on 2012-02-07
Suppose someone copied a lens and renamed it. Would this tool let a person configure that lens to do something other than what the original lens did? In other words, would this tool short cut the making of a lens?

Ordinary users need something other than learning how to code lenses and scopes.

Regards.

---

### Post by cgroza on 2012-02-07
> **grahammechanical said:**
> Suppose someone copied a lens and renamed it. Would this tool let a person configure that lens to do something other than what the original lens did? In other words, would this tool short cut the making of a lens?

Ordinary users need something other than learning how to code lenses and scopes.

Regards.
No. This tool was designed to allow to change things such as the name of the lens, the description, the assigned shortcut key, the icon, the search hint and whether the lens should be displayed by the dash.
The last feature could be useful to hide lens without going through the hassle of actually removing the lens through the software center.

It does require to logout/login for the changes to take effect.

---

### Post by itagomo on 2012-09-29
this is nice .. checked the github page but not in development anymore? how can I install or use this on my 12.04?

---

### Post by cgroza on 2012-09-30
> **itagomo said:**
> this is nice .. checked the github page but not in development anymore? how can I install or use this on my 12.04?
I saw no interest in it at that time and Unity was still divided in 2d and 3d, and then school came and I couldn't continue. I will probably revive it when some free time comes along.

---

### Post by cgroza on 2012-09-30
I will give it the ability to open files other than those in /usr/share/unity/places.
And maybe I will add some other features if anyone finds this application remotely useful.

---

### Post by CesarOscar on 2013-02-10
I was looking for something like this, there is a lot of interest but we have to make it know. Maybe Canonical can accept it as upstream now that they wish to include 100 lenses in 13.04, a 12.04 back port would be awesome (i use 12.04). I'm specially interested in the lenses shortcut editor and hide feature. 

What need to be done to start the project again?

---

### Post by MadmanRB on 2013-02-10
That would be nice, the lenses are a good idea but I wish they had some tweakability.

---

### Post by Copper Bezel on 2013-02-10
I still want Sam Hewitt's design for the Unity Dash settings screen. Mockups at the end of [this article](http://www.webupd8.org/2012/10/unity-680-released-with-option-to.html) on WebUpD8. Originally from the Ayatana mailing list, apparently.

[img]https://dl.dropbox.com/u/17749392/Image%20Hosting/Ubuntu%20Dash%20privacy%20mockup/unity-settings-panel-files.png[/img]

---

### Post by MadmanRB on 2013-02-10
Hope those mockups become a reality.

---

