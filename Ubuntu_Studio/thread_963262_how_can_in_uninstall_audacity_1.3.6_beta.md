---
title: "how can in uninstall audacity 1.3.6 beta ?"
date: 2008-10-30
forum: Ubuntu Studio
---

### Post by jaskah on 2008-10-30
hello
i would like to uninstall audacity 1.3.6 beta and re-install, from synaptic, version 1.3.4 beta (this seems more stable to me).
can anyone tell me how to do this. i am running audacity on ubuntu 8.04.
thanks for any help

---

### Post by moggy812 on 2008-10-30
have you tried going to system, preferences then to main menu and right clicking the offending program and then deleting it?

---

### Post by jaskah on 2008-10-30
hello
thanks for your reply, but your suggestion would only remove the program from the menu but not from the computer--which is what i would like to do.
in a nutshell: my basic question is how can one manually un-install programs?

---

### Post by thorgal on 2008-10-30
in a terminal:

sudo apt-get remove audacity

read the warnings carefully if it spits out some.

---

### Post by jaskah on 2008-10-30
hello

thanks for your answer, but i'm not sure this applies to my situaion, either.

i applied audacity manually from source code: 
./configure
make
make install

i didn't use synaptic, i didn't install using apt-get.
anyone have a solution for this?

---

### Post by thorgal on 2008-10-30
but then, go to the audacity source directory and type

sudo make uninstall

that's all it takes. Then you can do whatever with the source dir, delete it or upgrade it if you have gotten the source from svn.

---

### Post by jaskah on 2008-10-30
hi
thanks again for your answer...this is exactly what i was looking for.
will now give it a try...

---

### Post by lmno393 on 2008-10-31
Also love this book.--------------------------------------------------------------------------------------[Runescape Accounts](http://www.gold4kingdom.com/)

---

