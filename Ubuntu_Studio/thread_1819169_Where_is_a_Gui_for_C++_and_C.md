---
title: "Where is a Gui for C++ and C?"
date: 2011-08-05
forum: Ubuntu Studio
---

### Post by GoffyGoober on 2011-08-05
Does anybody here know a working, fast, executable, reliable header file to do GUIs in C++ and especially C? They can be different header files. I've already tried an already-made "hello world" program in a GTK tutorial, using it's special gcc arguments. It still didn't work. I also like using a simple execution which is something like:

```
cc ./Desktop/C.c -Wall -o./Desktop/C
```
(cc Links to gcc.)

I really don't need the C++ version now, but it would be useful for later. I need it executable because I am not thinking of making open-source programs. So I don't think I'll use Qt, because I've *never* seen that execute.

Oh, and also one for C* might be useful, thanks.

---

### Post by karlson on 2011-08-05
> **GoffyGoober said:**
> Does anybody here know a working, fast, executable, reliable header file to do GUIs in C++ and especially C?


Headers or sources?

> 
I really don't need the C++ version now, but it would be useful for later. I need it executable because I am not thinking of making open-source programs. So I don't think I'll use Qt, because I've *never* seen that execute.


Have you checked QT examples?

---

### Post by GoffyGoober on 2011-08-06
> **karlson said:**
> Headers or sources?
Headers (E.g. [COLOR="Silver"]#include <[COLOR="Black"]stdio.h[/COLOR]>[/COLOR]), but I also don't think Qt is a good idea...

---

### Post by karlson on 2011-08-06
> **GoffyGoober said:**
> Headers (E.g. [COLOR="Silver"]#include <[COLOR="Black"]stdio.h[/COLOR]>[/COLOR]), but I also don't think Qt is a good idea...

Headers for GUI libraries normally don't provide you with fully executable widget upon compile.  You will need libraries like GTK+, QT, Motif, etc.

Also, why do you think that QT is not a good idea?  I mean if you are learning GUI programming try something that you can easily understand Widgets, Dialogs, Notifications, callbacks, etc...   IMHO QT with the amount of documentation, examples, and books is the easiest to start with.

---

### Post by GoffyGoober on 2011-08-07
> **karlson said:**
> Headers for GUI libraries normally don't provide you with fully executable widget upon compile.  You will need libraries like GTK+, QT, Motif, etc.

Also, why do you think that QT is not a good idea?  I mean if you are learning GUI programming try something that you can easily understand Widgets, Dialogs, Notifications, callbacks, etc...   IMHO QT with the amount of documentation, examples, and books is the easiest to start with.
GTK+ does not work. I think I already said this in the original post. And Qt, I just don't think it would work well. Well, I guess I am going to have to use the idea that I already had a while ago: make my own header, then make a copy in Windows, etc.

---

