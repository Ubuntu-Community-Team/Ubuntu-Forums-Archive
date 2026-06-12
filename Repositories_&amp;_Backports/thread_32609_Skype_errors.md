---
title: "Skype errors"
date: 2005-05-08
forum: Repositories &amp; Backports
---

### Post by benplaut on 2005-05-08
to put it simply, there is an update for skype to put it at 1.1, but Ubuntu Update Manager is not letting it happen

it complains:

[IMG]http://img260.echo.cx/img260/3093/screenshot8eq.png[/IMG] 

any suggestions?

---

### Post by bored2k on 2005-05-08
[QUOTE=benplaut]to put it simply, there is an update for skype to put it at 1.1, but Ubuntu Update Manager is not letting it happen

it complains:

[IMG]http://img260.echo.cx/img260/3093/screenshot8eq.png[/IMG] 

any suggestions?[/QUOTE]
 This is probably caused by a missing dependency. Run synaptic package manager and try to upgrade with it.

---

### Post by benplaut on 2005-05-08
^^yup, that's it

> skype:
  Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed

---

### Post by bored2k on 2005-05-08
[QUOTE=benplaut]^^yup, that's it[/QUOTE]

Try running sudo apt-get -f install 
(on a terminal window)

If it doesn't do anything, downloading here:

 Package: libqt3c102-mt (3:3.3.3-7ubuntu3)
[http://packages.ubuntu.com/hoary/libs/libqt3c102-mt](http://packages.ubuntu.com/hoary/libs/libqt3c102-mt)

Your sources.list should have taken care of that btw.

---

### Post by benplaut on 2005-05-08
no... it requires 3.3.4, but the only version that is in the repos (and that link) is 3.3.3,

i'll just stick with 1.0 for now

---

