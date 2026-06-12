---
title: "qt mess with the new vivid."
date: 2015-03-26
forum: Ubuntu Development Version
---

### Post by mtt.castelli on 2015-03-26
Hi,
 
So I'm on Vivid and I've installed qttools5-dev-tools 'cause I need the linguist tool. I can see it in /usr/lib/i386-linux-gnu/qt5/bin/linguist, and with the whole path I can also launch it.

I do expect to launch it also without the path, but the system claims for the qt4 version which is not even installed.. Look:

matteo@HP-Mini-210:~$ linguistlinguist: could not exec '/usr/lib/i386-linux-gnu/qt4/bin/linguist': No such file or directory

---

### Post by zika on 2015-03-26
[http://manpages.ubuntu.com/manpages/utopic/man1/qtchooser.1.html](http://manpages.ubuntu.com/manpages/utopic/man1/qtchooser.1.html)

---

### Post by mtt.castelli on 2015-03-26
> matteo@HP-Mini-210:~$ qtchooser -list-versions
4
5                                                                                 
default                                                                           
qt4-i386-linux-gnu                                                                
qt4                                                                               
qt5-i386-linux-gnu                                                                
qt5                                                                               
matteo@HP-Mini-210:~$  qtchooser -print-env                                       
QT_SELECT="default"                                                               
QTTOOLDIR="/usr/lib/i386-linux-gnu/qt4/bin"                                       
QTLIBDIR="/usr/lib/i386-linux-gnu"

Ok, here is zika and thank you. Which version should i choose and how?

And also, why the system show me this if I have no qt4 tool installed?

---

### Post by mc4man on 2015-03-27
Your easiest solution is to just install this package - 
qt5-default

---

