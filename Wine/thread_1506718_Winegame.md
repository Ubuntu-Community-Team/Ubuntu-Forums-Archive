---
title: "Winegame"
date: 2010-06-10
forum: Wine
---

### Post by pashazz on 2010-06-10
Hello guys :)

I am developing an utility for easy-installing win32 apps, named Winegame. 
It like playonlinux, but better. Why? It uses easy INI format for wine configuration and debian-like naming for package files (preinst-postinst-control).

Winegame is separated into two projects:

- winestuff is the core, shared library.
- winegame is a GUI.

Both of there is written in C++ with Qt 4.6

I provide an PPAs:
```

ppa:pzinin/winegame for releases
ppa:pzinin/winegame-daily for daiy builds (now it`s more stable)

```[Site]("http://winegame.googlecode.com") on GoogleCode.
[Project site ]("http://winegame-project.ru")in Russian. (contains all wiki pages about package format, etc).
There`s also non-full [English translation  ]("http://wiki.github.com/pashazz/winestuff/")of wiki.
[List of supported games]("http://code.google.com/p/winegame/wiki/GameList") 

[B]Source:
[/B][winestuff]("http://github.com/pashazz/winestuff") - LGPL v 2.1
[winegame]("http://github.com/pashazz/winegame") - GPL v. 3

I accept any help and suggestions. Thanks!

---

### Post by sprinda on 2010-06-10
I have a request.  can you make sure that it can play Fiesta from outspark?  please!!!!

---

### Post by cogadh on 2010-06-10
This is just a font end for Wine, it really can only do what Wine already can do. If Wine already supports Fiesta, then you're all set, if not, this won't help you.

---

