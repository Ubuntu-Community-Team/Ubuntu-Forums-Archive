---
title: "Trouble with Endorphin (Even if you don't know what that is you can still help)"
date: 2009-04-06
forum: Wine
---

### Post by Eggbertx on 2009-04-06
I am trying to run Naturalmotion Endorphin through wine, but I get this error:

Runtime Error!

Program C:\Program Files\NaturalM...

R6034
An application has made an attempt to load the C runtime library
incorrectly.
Please contact the application's support team for more information.

Can someone help me??

---

### Post by Eggbertx on 2009-05-01
Bump. Someone? Anyone? Echo....echo....

---

### Post by cogadh on 2009-05-01
It sounds like the application just needs one of the Visual C++ runtimes installed, which you can do using [winetricks]("http://wiki.winehq.org/winetricks"). We could confirm that if you ran the app from the terminal and posted Wine's output here. It is usually much more helpful than any error messages you might get from the application itself and will specify exactly what runtime library might be needed.

---

