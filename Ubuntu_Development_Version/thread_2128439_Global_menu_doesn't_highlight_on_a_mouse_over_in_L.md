---
title: "Global menu doesn't highlight on a mouse over in Libre Office"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by georgelappies on 2013-03-23
Not sure if anybody else noticed this but the global menu doesn't highlight to orange if you mouse over an option in it. So far this only seems to happen in Libre Office.

EDIT: I accidently tagged this as a lubuntu issue but obviously it is an ubuntu issue with the global menubar.

---

### Post by mc4man on 2013-03-23
here
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1153654](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1153654)

---

### Post by rrnbtter on 2013-03-23
Greetings,
Libre Office has been broken from the beginning of Raring in one form or another. Try, minimize and then maxize window and see what happens. Often it will make the menu active.

---

### Post by beforefirstlight on 2013-04-23
In 2 days it's the final release of ubuntu 13.04 and this bug has not been fixed !

---

### Post by Cornyspezi on 2013-04-28
Isnt fixed yet. :sad:

---

### Post by roly33 on 2013-04-29
Try adding these to your sources list 

[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) (main)

[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) (main (Source Code))

It'll add the repos for  Libre Office 4

I've been using it since before raring went final and never had any trouble with the Global Menu bar.

Roland

---

### Post by treb0r on 2013-05-30
> **roly33 said:**
> Try adding these to your sources list 

[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) (main)

[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) (main (Source Code))

It'll add the repos for  Libre Office 4

I've been using it since before raring went final and never had any trouble with the Global Menu bar.

Roland

Hmmm, I've added the repos and upgraded to the latest version, but my menus still don't highlight.

Any other ideas?

Rob

---

### Post by cariboo on 2013-05-30
It works the way it should here on my Saucy install.

[LIST]
[*]Unity version 7.0.0
[*]Kernel Linux alexis 3.9.0-3-generic #8-Ubuntu SMP Tue May 28 18:40:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[*]Video driver NVIDIA 313.30
[/LIST]

---

### Post by treb0r on 2013-06-25
For anybody using raring, there is now a fix in proposed.

sudo aptitude install unity/raring-proposed

or apt-get if you don't have aptitude installed.

The devs are asking for people to test it and feeback on Launchpad here:

[https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1153350?comments=all](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1153350?comments=all)

---

