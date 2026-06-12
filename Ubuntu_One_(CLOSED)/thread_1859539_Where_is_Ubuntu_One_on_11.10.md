---
title: "Where is Ubuntu One on 11.10"
date: 2011-10-14
forum: Ubuntu One (CLOSED)
---

### Post by gepolv on 2011-10-14
I have two questions:

1:
I just tried Ubuntu one on 11.10 and now I fail to find where it is.  I am using "ubuntu classic".

2: 

I have syned a folder on another computer and there is no problem. 
However, when I try to syn it to my current computer, I always got an error:

----------------------------------------------------------------------------
File Sync error. (org.freedesktop.DBus.Error.NoReply: Did not
----------------------------------------------------------------------------

Any suggestions?

Thanks
Deryk

---

### Post by gepolv on 2011-10-14
Nobody met this problem?
It is weird.

---

### Post by nutznboltz on 2011-10-15
> **gepolv said:**
> I have two questions:

1:
I just tried Ubuntu one on 11.10 and now I fail to find where it is.  I am using "ubuntu classic".


Inside gnome-terminal run:

/usr/bin/python /usr/bin/ubuntuone-control-panel-gtk

---

### Post by vanadium on 2011-10-15
In Unity, Ubuntu one is easily located with the search "Ubuntu". I bet it will also be somewhere in a "classical" menu. Alternatively, find the application launcher in /usr/share/applications.
Indeed, the icon is not anymore included on the launchbar by default.

---

### Post by nutznboltz on 2011-10-15
> **vanadium said:**
> I bet it will also be somewhere in a "classical" menu. 

But you are just guessing and aren't even willing to shift to classic mode to test, right?

---

### Post by vanadium on 2011-10-15
Why should I have to test this?

---

### Post by nutznboltz on 2011-10-15
> **vanadium said:**
> Why should I have to test this?

Because posting "answers" to questions that are unverified uses up space in a forum without providing any answer to the question being asked.

---

### Post by duanedesign on 2011-10-16
The reason the user probably can not test this is because Classic mode is not available on 11.10.

> Ubuntu 11.10 will not include the classic GNOME desktop which is available alongside Unity in Ubuntu 11.04. Instead, Unity 2D will be installed to provide the Unity desktop even on systems without 3D graphics capabilities

To get classic Mode you have to install extra packages. This means it is not a 'supported' setup. If Ubuntu One is not showing up under the Me Menu or System > Preferences > Ubuntu One then you will likely need to edit your menus and add it manually.

---

