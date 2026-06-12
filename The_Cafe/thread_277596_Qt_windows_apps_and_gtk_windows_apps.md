---
title: "Qt windows apps and gtk windows apps"
date: 2006-10-14
forum: The Cafe
---

### Post by darkhatter on 2006-10-14
all the qt apps I used in windows skype(think its qt) and opera both run good. Firefox, and inkscape runs good, but I find that amsn is not as good. Is programing for gtk on windows harder then it is qt apps on windows. From what I have seen qt seems to be the language of choice if you want to produce tri-os programs

---

### Post by Bloodfen Razormaw on 2006-10-14
Programming against GTK+ is harder on any platform than programming against Qt.  Qt is just a lot more powerful and polished.  Also, since you mention cross-platform development, it is important that GTK+ is just a graphical library, while Qt is an entire framework.  When you use Qt, your program will be supported on any platform that supports Qt.  Since GTK+ only covers the GUI it only makes the GUI cross-platform.  Whether or not the rest of the program is cross-platform depends on the code you write and the libraries you use.

P.S. Firefox on Windows doesn't use GTK+, and I think Opera on Windows doesn't use Qt (at least it still didn't in 8.x).

---

### Post by darkhatter on 2006-10-14
ok, I just wanted to know how come amsn was not as good as it was on Linux. This is starting to sound messy so explaining to me may be a waste of time

---

### Post by Bloodfen Razormaw on 2006-10-14
What precisely is the problem with amsn in Windows?  I was not aware that amsn used GTK+.  A quick look at it in aptitude says it uses Tcl/Tk.

---

### Post by darkhatter on 2006-10-14
I'm having a noob moment right now

---

### Post by Kimm on 2006-10-15
> **Bloodfen Razormaw said:**
> What precisely is the problem with amsn in Windows?  I was not aware that amsn used GTK+.  A quick look at it in aptitude says it uses Tcl/Tk.

True. aMSN doesnt use GTK at all :p

---

### Post by ComplexNumber on 2006-10-15
> **Kimm said:**
> True. aMSN doesnt use GTK at all :p
however, [this]("http://amsn.sourceforge.net/forums/viewtopic.php?t=618") gives it a native qt/gtk/whatever look and feel.

---

