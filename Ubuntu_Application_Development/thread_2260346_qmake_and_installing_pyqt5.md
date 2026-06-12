---
title: "qmake and installing pyqt5"
date: 2015-01-11
forum: Ubuntu Application Development
---

### Post by Kingmaster on 2015-01-11
Hi
I tried to install pyqt5 that was requiered qt5 and python 3.x
python was already installed by ubuntu and I installed qt5 manually.
and i tried to install pyqt5 from read me instructions and i got this error
```
madman@madman-N53SV:~/Desktop/Desktop/PyQt-gpl-5.3.2$ sudo python3.4 configure.py --qmake ~/Qt5.4.0/
Querying qmake about your Qt installation...
/bin/sh: 1: /home/madman/Qt5.4.0: Permission denied
Error: PyQt5 requires Qt v5.0 or later. You seem to be using v3. Use the
--qmake flag to specify the correct version of qmake.
madman@madman-N53SV:~/Desktop/Desktop/PyQt-gpl-5.3.2$ 
```
I serched and I didn't find any thing helpfull any one can help me what should i do?
it was the same result even with out```
--qmake ~/Qt5.4.0/
``` part

i searched and some one told should do this but this doesn't work.
thanks

---

### Post by steeldriver on 2015-01-11
Hello and welcome to the forums

I'm guessing here, but perhaps the --qmake argument needs to point to the actual qt5 qmake binary rather than the toplevel directory where you installed it? so something like

```

--qmake="$HOME/Qt5.4.0/qtbase/bin/qmake"

```

(you will need to check the exact path)

---

### Post by Kingmaster on 2015-01-11
TNX for answering mr [**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")

this error was about two month ago and i until today I was tryng to install.
just a few hours after I posted I found the files in repository and two month ago I didn't find anything in repos.
an dI have to mention it needs SIP before installing.

---

### Post by Aviendha09 on 2015-03-12
I have a similar problem. The above almost worked. Now I get this error:

```

anabel@anabel-Dell:~/prog/PyQt-gpl-5.4.1$ sudo python3 configure.py --qmake="$HOME/prog/qt/5.4/Src/qtbase/qmake"
Querying qmake about your Qt installation...
/bin/sh: 1: /home/anabel/prog/qt/5.4/Src/qtbase/qmake:** Permission denied**
Error: PyQt5 requires Qt v5.0 or later. You seem to be using v3. Use the
--qmake flag to specify the correct version of qmake.

```

How can I get permission denied in my own directory ? So I tried with sudo, but to no avail.

---

### Post by Aviendha09 on 2015-03-12
I found this post (>.<) 

[http://ubuntuforums.org/showthread.php?t=2248707&highlight=pyqt]("http://ubuntuforums.org/showthread.php?t=2248707&highlight=pyqt")

---

### Post by Aviendha09 on 2015-03-24
Well it solved parts of my problem. 
Now I have 2 installations of PyQt5. None of which can find PyQt5.QtSql. Not even to run a PyQt5 demo! Other demos work, just not the one I need. Should I try to uninstall everything and re-install from Repository only , or is there another solution ??

---

### Post by Aviendha09 on 2015-03-25
oh boy: python3-pyqt5 packages have to be installed separately. *Doh!*

---

