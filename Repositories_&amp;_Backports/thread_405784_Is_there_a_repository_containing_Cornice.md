---
title: "Is there a repository containing Cornice"
date: 2007-04-10
forum: Repositories &amp; Backports
---

### Post by deep-z on 2007-04-10
Hello!

Recently I stumbled upon this ACDSee alternative Cornice [http://wxglade.sourceforge.net/extra/cornice.html](http://wxglade.sourceforge.net/extra/cornice.html), but didn't find any information on how to install it "normal" Ubuntu way.

Before trying to manually build it - maybe someone knows how to install it via apt-get or maybe there's a Debian package somewhere?


P.S. I'm not interested in Wine + Irfanview or similiar solutions with running same windows apps on linux. :)

---

### Post by compwiz18 on 2007-04-10
One freshly created deb, just for you.

---

### Post by deep-z on 2007-04-13
Thanks, man! :guitar:

---

### Post by helliewm on 2007-04-17
I typed in my password but it says I have to root to install this deb. How  do I install it? I am confused?

Helen

---

### Post by PatsM on 2007-04-17
Great tool! Just what I was looking for. Thanks for the deb.

Patrick

---

### Post by deep-z on 2007-04-18
Open Terminal and try this:

sudo dpkg -i cornice_0.6.1-all.deb

Then enter your password and you're done.

> **helliewm said:**
> I typed in my password but it says I have to root to install this deb. How  do I install it? I am confused?

Helen

---

### Post by semoetz on 2009-11-06
i had successfully install it. but how to open that application?
i didn't find it in graphic section applications....

---

### Post by Shazaam on 2009-11-07
Some apps do not add themselves to the menu list. Run this in terminal...
```
cornice
```
If it starts (don't close terminal until you are done with the app) and runs ok you can add it to the menu manually by going to System>Preferences>Main Menu.

---

### Post by semoetz on 2009-11-12
> **Shazaam said:**
> Some apps do not add themselves to the menu list. Run this in terminal...
```
cornice
```If it starts (don't close terminal until you are done with the app) and runs ok you can add it to the menu manually by going to System>Preferences>Main Menu.

i had doing this:

"sudo dpkg -i cornice_0.6.1-all.deb" in terminal

and it's normally success (there's no error i found), i think :sad:

when i run "cornice" in terminal, this msg appear:
```
Traceback (most recent call last):
  File "./cornice.py", line 68, in <module>
    main()
  File "./cornice.py", line 48, in main
    import fixdc
  File "/opt/cornice/fixdc.py", line 42, in <module>
    import wx
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory

```

and then i attach it to the main menu just liku u said, and it's there, cornice!!
but the problem is appear: when i open that cornice application, it's not work...
the app not appear at all...it's just like nothing happend on my screen..

is it wrong?? could u tell me step by step to install it on my jaunty??

thx...!!!

---

