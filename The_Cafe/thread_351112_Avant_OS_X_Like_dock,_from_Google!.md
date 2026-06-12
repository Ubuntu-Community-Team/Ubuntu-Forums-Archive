---
title: "Avant OS X Like dock, from Google!"
date: 2007-02-01
forum: The Cafe
---

### Post by Tipo on 2007-02-01
[http://code.google.com/p/avant-window-navigator/]("http://code.google.com/p/avant-window-navigator/")

Just saw this up on digg...

What do you guys think about it?

Pretty neat if you ask me :)

---

### Post by towsonu2003 on 2007-02-01
just to note, it's not from google, it is from someone named: njpatel
google hosts his/her project (similar to sourceforge)

---

### Post by Choad on 2007-02-01
cool, im getting it from svn right now :)

---

### Post by Tipo on 2007-02-01
> **towsonu2003 said:**
> just to note, it's not from google, it is from someone named: njpatel
google hosts his/her project (similar to sourceforge)

Ahh, will a mod correct the thread title, please? :)

---

### Post by Choad on 2007-02-01
blegh too many dependencies 

cant be bothered to hunt for them

---

### Post by towsonu2003 on 2007-02-01
> **Choad said:**
> cool, im getting it from svn right now :)

just be careful though. what if it has got a virus or rootkit... bla

---

### Post by maxamillion on 2007-02-01
Looks like a nice project, but to be honest it seems like the project creator is reinventing the "gnome-dock" wheel ....

---

### Post by Somenoob on 2007-02-01
I hope Google will realese [Goobuntu]("http://en.wikipedia.org/wiki/Goobuntu") someday

---

### Post by cbudden on 2007-02-01
Is anyone able to access the SVN?  I am behind a proxy and usually have no problem with SVN.  Would someone mind checking out and then putting it in a tar.gz or something then uploading here?

Thanks

Chris

---

### Post by FunnyLookinHat on 2007-02-01
I get a nice little seg-fault after I compile it...

the packages to grab aren't too bad, just a few -dev ones.  the ./configure even tells you which ones to get, heh

---

### Post by Super King on 2007-02-01
Looks nice, I'll probably wait patiently until someone cooks up a .deb.

---

### Post by prizrak on 2007-02-01
There are quite a few desklets like that actually. Never understood the point of such a dock bar.

---

### Post by christhemonkey on 2007-02-01
From his blog:
[QUOTE=Blog]
1) I don't work for Google (I wish I did :), but do use their excellent project-hosting services.

2) This differs from previous docks in that it is firstly a task switcher, just like the task list in GNOME, and therefore it will keep track of all open windows on the desktop.

3) Although this look like the MAC OS X dock, it does not try to imitate it. Awn is fully configurable, it has planned features not available elsewhere, such as the ability for applications to control their icons through dbus, and allow progress indicators on the icon.

4) Launching applications from Awn and tracking the application windows (like 'The Dock') is planned, and is being implemented as we speak.

5) The dependency on a patched libwnck is not required in svn.

6) I you are getting a segfault, this is a problem with schema installation, and can be overcome by entering the 'data' directory (after make install), and executing:

$  gconftool-2 --install-schema-file=avant-window-navigator.schemas

Also, if you are using svn, be sure to try the new task-manger launching Awn like this:

$ avant-window-navigator -x
[/QUOTE]

Just to help clear up a few things :D
It looks really nice, will give it a try if i get time.

---

### Post by FunnyLookinHat on 2007-02-01
Here is my tutorial to get it compiled and running correctly...

I did it on edgy-eft, but should work on dapper-drake


[http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

---

