---
title: "gedit is a little messed up"
date: 2016-02-13
forum: Ubuntu Development Version
---

### Post by ELD on 2016-02-13
Looks like the gedit version pulled in for 16.04 is a little messed up. It has a double menu, and double window controls.

See a shot here: [http://imgur.com/72q5CNB](http://imgur.com/72q5CNB)

---

### Post by fthx on 2016-02-14
I would rather say that Unity is messed up with Gnome apps...

---

### Post by mc4man on 2016-02-14
> **ELD said:**
> Looks like the gedit version pulled in for 16.04 is a little messed up. It has a double menu, and double window controls.

See a shot here: [http://imgur.com/72q5CNB](http://imgur.com/72q5CNB)
There really aren't "double" menus. For ubuntu  session the actual menus are in the unity panel 
(- provided via a patch to gedit - 0001-Use-the-OSX-menubar-layout-for-XFCE-Unity-etc.patch
What's in the header bar are just a few actions, ie., open files (recent & anywhere else), open a new tab & save

The double "window controls" when gedit is maximized are the result of gedit using csd. Windows that use window deco have the deco merged into the unity panel when maxed, gedit with csd has no deco to be merged so the GtkHeaderBar that gedit is using stays below the panel.

What you're getting now may be about as good as it's going to get in 16.04, maybe they fix the header bar to  not have a colored radius in a squared off bar, otherwise most issues from GtkHeaderBar & csd have been mitigated. 
The only other choice would be or would have been to stick with 3.10 for 16.04, that would have been the best choice from a design perspective but as far as 16.04 & unity 7 Design has moved on.

Here I've  tested disabling csd in gedit but it looks odd due to the colored radius, plus there is redundant file name info - scr. 1 is example. Disabling also allows the gedit menus to be moved into the window, scr. 2 & also gets gedit on the same page theme-wise as every other default supplied app. 

Overall I think personally I'll just use gedit-3.10 in 16.04, am currently testing & no obvious issues yet.

---

### Post by mc4man on 2016-02-19
Ubuntu got an upstream patch to disable csd in an ubuntu session so now gedit looks & acts a bit better
> gedit (3.18.3-0ubuntu3) xenial; urgency=medium

  * debian/patches/unity_no_csd.patch:
    don't use GtkHeaderBar decorations under Unity, they still create
    integration issues and are too differents. That should fixes those issues
    - having duplicated decorations (lp: #1542129)
    - right click on decorations not providing common actions like move to
      workspace (lp: #1527592)
    - using local menus loose gedit ones (lp: #1518516)

---

### Post by ELD on 2016-02-20
Yep, looks better now.

---

### Post by ELD on 2016-02-21
Looks like gnome-software needs the same bit of love, look at those window buttons heh, tiny.

[http://imgur.com/Xmeohpc](http://imgur.com/Xmeohpc)

---

### Post by mc4man on 2016-02-21
> **ELD said:**
> Looks like gnome-software needs the same bit of love, look at those window buttons heh, tiny.

[http://imgur.com/Xmeohpc](http://imgur.com/Xmeohpc)
It's sized ok here but again another csd app..
It does appear that packages in general need a lot of work so they will show up in Software, currently only a small percentage do.
(got a mail about that, can't find it though
edit: [http://appstream.ubuntu.com/](http://appstream.ubuntu.com/)
Ex. try to find chromium-browser  or any gstreamer plugin or thousands of other packages

---

### Post by mc4man on 2016-03-04
For at least an ubuntu session now csd has been disabled, good deal.

---

