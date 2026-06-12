---
title: "I want to introduce my last work: Epes"
date: 2011-02-23
forum: The Cafe
---

### Post by OpenNingia on 2011-02-23
If you, like me, follows lots of TV Shows then you need Epes :guitar:

This is my last fatigue and I'm very proud of it gh :)

Download: [http://code.google.com/p/myepes/]("http://code.google.com/p/myepes/")

How to install:  [http://code.google.com/p/myepes/wiki/InstallationGuide]("http://code.google.com/p/myepes/wiki/InstallationGuide")

A screenshot is valued more of a thousand word.

Epes should work on every Ubuntu flavour if installed correctly.
Sadly there is no ppa for it because I don't know how to manage one ^^,

However I'd be glad if you try it and you give me some feedback!

---

### Post by An Sanct on 2011-02-23
Nice one :)

Well, if you want people to use your software with ease, make it a [deb]("http://debcreator.cmsoft.net/") package. This will help anyone to install you program...

---

### Post by OpenNingia on 2011-02-23
> **An Sanct said:**
> Nice one :)

Well, if you want people to use your software with ease, make it a [deb]("http://debcreator.cmsoft.net/") package. This will help anyone to install you program...

Yes I could, but there are some issues. The major is that Epes depends on libraries which are not shipped with any Ubuntu system ( because are in beta yet )

The libraries are PySide, an LGPL binding of the Qt4 framework to python.

The solution would be to have a ppa with all the right dependences. But I really don't know how to create or manage a ppa.

---

### Post by OpenNingia on 2011-03-03
Hi :) I finally managed to create a ppa for epes.

You can install from Karmic, Lucid and Maverick with the following commands:

sudo add-apt-repository ppa:epesteam/ppa
sudo apt-get update
sudo apt-get install epes

:popcorn:

---

### Post by nilarimogard on 2011-03-08
Great work, the PPA was a must!

Edit: argh, but you should also upload python-pyside.qtcore and python-pyside.qtgui to the PPA...:

> sudo apt-get install epes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 epes : Depends: python-pyside.qtcore (>= 1.0.0~) but it is not going to be installed
        Depends: python-pyside.qtgui (>= 1.0.0~) but it is not going to be installed
E: Broken packages


---

### Post by Grenage on 2011-03-08
Interesting; does your program lookup series on thetvdb.com?  If so, I'll have to give this a whirl.

---

### Post by aeiah on 2011-03-08
> **Grenage said:**
> Interesting; does your program lookup series on thetvdb.com?  If so, I'll have to give this a whirl.

looks like it uses tv rage instead. python-tvrage is a dependency.


does this use an sqlite backend? it'd be awesome if it could easily be made compatible with the xbmc database, and could be used as an external tool for it.

---

### Post by Grenage on 2011-03-08
> **aeiah said:**
> looks like it uses tv rage instead. python-tvrage is a dependency.


does this use an sqlite backend? it'd be awesome if it could easily be made compatible with the xbmc database, and could be used as an external tool for it.

Thanks for the clarification.  I'm always looking at thetvdb when organising series, because I use their scraper in XBMC; I'll take a peek at tvrage.

---

### Post by furiat on 2011-04-05
Hi man, I like your app a lot, it keeps me organized. There was an update of qt recently and I suppose this is the reason I am gettinf this error when I am running epes:

Probably tables already exist... check if we need to update db
this db is already updated to the last version
Traceback (most recent call last):
  File "/usr/bin/epes", line 403, in <module>
    epesform = EpesCore(epesDb)   
  File "/usr/bin/epes", line 51, in __init__
    self.setupUi(self)
  File "/usr/lib/pymodules/python2.6/epescore/main_ui.py", line 17, in setupUi
    self.gridLayout.setMargin(3)
AttributeError: 'PySide.QtGui.QGridLayout' object has no attribute 'setMargin'


Is this an easy fix for you? I would be grateful to be able to use your app again. Thanks a lot

---

### Post by OpenNingia on 2011-04-05
I there :) sorry for late answer but... now here I am :)

The issue with the last update is rather simple to fix ( and I've already fixed in my svn repository ), however I must admit I'm pretty ignorant when it comes to packaging.

How do I build a debian package that is ok for more Ubuntu version? ( at least karmic, lucid, maverick and natty ) 

Is there someone willing to help me with packaging?

Also, to answer an early question. Yes epes uses sqlite for database ( but it stores little data in there )

---

### Post by OpenNingia on 2011-04-05
> **aeiah said:**
> looks like it uses tv rage instead. python-tvrage is a dependency.


does this use an sqlite backend? it'd be awesome if it could easily be made compatible with the xbmc database, and could be used as an external tool for it.

what is that xbmc database? And what do you mean by "compatibility" between epes and xbmc? 

Explain yourself :D If it's easy enough I may manage to get it done!

---

### Post by cariboo on 2011-04-05
@OpenNingia, This link may be helpful, if you want to set up a ppa:

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by OpenNingia on 2011-04-06
> **cariboo907 said:**
> @OpenNingia, This link may be helpful, if you want to set up a ppa:

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Thanks :D I'm trying to improve my packaging skill... From my point of view is more complicated that developing :°°D

---

