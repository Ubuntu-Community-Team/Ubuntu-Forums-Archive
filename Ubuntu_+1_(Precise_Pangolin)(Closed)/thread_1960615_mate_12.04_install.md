---
title: "mate 12.04 install"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ibbill on 2012-04-17
Has anyone tried the mate install Ubuntu +1 (Precise Pangolin)

Was planning on giving it a try. Did anyone else install it? Was there any problems?

Thanks for the help.

---

### Post by pqwoerituytrueiwoq on 2012-04-17
installs and works
i cant get compiz working (pointless without compiz)
the logout does not work as a applet (works from the system menu) btw it is the one simialt to the indicator applet session 
gedit is not changed to pluma as the default text editor and it should be
there are others but they need to be labled as replaces [insert app here] in there .desktop file

edit:
compiz is not configured out of the box anymore so i assumed it was not working at all you need to go into ccsm and enable stuff like the window decorator and move
running compiz --replace cause 60% cpu usage i made a shell script to kill marco so there is no cpu usage out of the ordinary
```
#!/bin/sh
if [ 0`pidof mate-session` -gt 0 ]; then
    killall marco
    compiz --replace &
fi
```save it to a file and "[FONT=Courier New]chmod +x[/FONT]" it and add it to startup

---

### Post by ibbill on 2012-04-17
Awesome thanks very much. I have lisa 12 mate on one partition and 12.04 on another. Think I will wait for Mint13 and just install over 12.04 and go strictly with Mint.

Thanks again for your info.

---

