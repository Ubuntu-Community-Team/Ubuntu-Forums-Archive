---
title: "emacs on server?"
date: 2009-04-10
forum: Server Platforms
---

### Post by poundjd on 2009-04-10
Guys, I did an apt-get update, then an upgrade and then apt-get install emacs.  And I was told that it was not installable. 
Is there a good way to get emacs installed on a 8.04.2 server, or do I need to install a workstation to be able to install emacs.....
-jeff

---

### Post by DannyW on 2009-04-11
Hi

It could be that apt tried to install emacs which requires a graphical display.

Try installing emacs22-nox

sudo apt-get install emacs22-nox

---

