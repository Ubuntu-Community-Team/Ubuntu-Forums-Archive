---
title: "Mysterious File in Home Folder"
date: 2012-12-28
forum: Ubuntu Studio
---

### Post by themuseman on 2012-12-28
Greetings,

I am running 64 bit Ubuntu Studio 12.04 and I suddenly noticed a file name "exo-file-manager.desktop" in the Home folder. I have no idea where it came from ... was not previously there until sometime in the last few days.  I've been running this OS for many months, and suddenly the file mysteriously shows up in the Home folder.

Any ideas on what it is, why it's there, and if I can safely delete it?

themuseman

---

### Post by sudodus on 2012-12-28
A desktop file is there to launch an application, when you click on its icon in a file browser (or on the Desktop).

You can inspect it with a text editor or viewer, either right-click on it in a file browser and select Edit or View, or in a terminal window, run your favourite editor or viewer, for example

```
less "exo-file-manager.desktop"
```
and then you will understand what it is supposed to do. After that you can decide what you want to do with it.

---

### Post by ibjsb4 on 2012-12-28
Can also take a look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=exo-file-manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=exo-file-manager&as_qdr=all&sa=Google+Search&lang=en)

---

