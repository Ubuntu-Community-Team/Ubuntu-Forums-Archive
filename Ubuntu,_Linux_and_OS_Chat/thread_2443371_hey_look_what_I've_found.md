---
title: "hey look what I've found"
date: 2020-05-14
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2020-05-14
I found this very cool cover flow file manager called Dfilemanager that looks like what they get on a Mac. [http://dfilemanager.sourceforge.net/](http://dfilemanager.sourceforge.net/)

It looks like development has stopped a while ago but compiling from source on Ubuntu 20.04 is a breeze, have it up and running in no time. I am not using it as my default file manager, it is not functional enough and there are probably issues to integrate with the DE (I use nemo on Unity) but it is fun to have it around as a toy and for the eye candy. :p

This is the code

```
sudo apt install qt5-default qt5-qmake libqt5x11extra5-dev libffmpegthumnailer-dev libpoppler-qt5-dev libkf5solid-dev libmagic-dev
 
git clone git://git.code.sf.net/p/dfilemanager/code dfilemanager-code
cd dfilemanager-code
mkdir build && cd build
cmake -DQT5BUILD=ON ..
make 
sudo make install
```

---

### Post by Hwæt on 2020-05-14
D file manager and it's not written in D? :confused:

---

### Post by Perfect Storm on 2020-05-14
Reminds me of a plugin you could get for nautilus back in the GTK2 days with compiz.

---

