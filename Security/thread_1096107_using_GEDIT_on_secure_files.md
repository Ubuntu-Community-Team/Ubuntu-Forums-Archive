---
title: "using GEDIT on secure files"
date: 2009-03-14
forum: Security
---

### Post by kwandtke on 2009-03-14
in the past I've always used NANO to edit secure files .. say like samba.conf .... so I can go sudo nano ......... 

So a friend I started on Ubuntu was trying to edit samab.conf and , being a long time Windows user fired up Gedit (which he figured was like Notepad which I guess is correct).  Now he explained how he could use Notepad to edit a bunch of stuff .. now he 's questioning how I can tell him Ubuntu is better than Windows if he can not make himself ROOT equal (I explained why that was not good and he sorta acknowledged it)  .. and the GUI tools do not allow anyway to invoke SUDO. He pointed out that in Windows XP he could do a RUN AS ... which I admit works ..

So.. are we really saying that the ONLY way to edit a "secure" files is from the command line? That does not seem right and seems like a big problem.

And guys .. I use NANO so please don't dump on me for being afraid of the comman line or anything .. I'm asking this along the lines of the "Grandma test" for general Linux use

---

### Post by bryonak on 2009-03-14
Press Alt+F2
then enter:
```
gksudo gedit
```

You could use sudo instead of gksudo, but that's a bad idea: gksudo is a wrapper for sudo which takes care that graphical config files are kept with user permissions/ownage. Sudo would assign some of them to root, which is not what you want.

For graphical stuff, use gksudo.

---

### Post by sisco311 on 2009-03-14
AFAIK, it's perfectly safe to edit files with a GUI editor.

```
gksu gedit /path/to/file
```
gksu/gksudo is the graphical front-end for su/sudo.

Backing up the file is always a good idea.
```
nano -B path/to/file
```
I think, the backup option is the default in gedit, but i'm not sure.


EDIT:
oh, and visudo has syntax check, so you have to run it from a terminal or 
check the *Run in terminal* box in the *Run program* dialog.

---

### Post by kwandtke on 2009-03-14
> **bryonak said:**
> Press Alt+F2
then enter:
```
gksudo gedit
```

You could use sudo instead of gksudo, but that's a bad idea: gksudo is a wrapper for sudo which takes care that graphical config files are kept with user permissions/ownage. Sudo would assign some of them to root, which is not what you want.

For graphical stuff, use gksudo.

Exactly what I was looking for .. thanks guys ...

---

### Post by bodhi.zazen on 2009-03-15
Well, to answer your question I  suggest you also look at :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

