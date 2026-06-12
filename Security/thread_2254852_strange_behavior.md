---
title: "strange behavior"
date: 2014-11-30
forum: Security
---

### Post by darko6 on 2014-11-30
My ubuntu  sudenly stopped working or working with  delays, when i noticed that "firefox guest y+" was running although  my firefox was closed. What is happening? I cannot open anything on my computer. tnx

---

### Post by ajgreeny on 2014-11-30
Open a terminal, if you can, and run **killall firefox** to stop all firefox sessions running.  If you can't open a terminal try Ctrl+Alt+F1 to get to a command-line, login there (no password will show on screen but it will be typed and entered; just type and hit Enter) and from there try the command again.  It may say there is no firefox process running as you are now in a tty, not the xsession, but the xsession is still running so it should still be shown.

I do not know if you have the system set to open a previous session, but it might be worth making sure that is not the case, and also removing any saved sessions from **~/.cache/sessions** just to ensure there is no instance of firefox saved there that opens at new xsession start.

What is the spec of your machine as there are a huge %age of memory resources being used, including 78% of your swap, which I would suggest is pretty unusual even on a medium spec machine.  However, cpu %age is not particularly high, so there is obviously something very odd going on here that needs sorting out.

---

### Post by darko6 on 2014-11-30
Tnx man! Now its ok. How to open [COLOR=#000000] [/COLOR]**~/.cache/sessions ?**

---

### Post by darko6 on 2014-11-30
Also,  when i installed 14.04 firefox didnt want to run youtube and facebook so i have installed varius kinds of alternative flash extensions, but none of them seems to be working. Any idea what to do?

---

### Post by ajgreeny on 2014-11-30
I suggest you remove any flash packages you now have installed, though how you do that will depend on how you installed them, so tell us more of the packages you have now.
Then install the ***ubuntu-restricted-extras** package with softwaqre-centre for whatever version of *ubuntu you have installed.
You can open ~/.cache/sessions by using Ctrl+H in the file manager in order to show hidden files and folders.
The **~/** at the start of that path is just a shortcut for **/home/darko6** (or whatever your username is).

---

### Post by darko6 on 2014-11-30
Besides this i have installed in plugins  divx video player and icedtea web plugin but you cant see them coz they are on top.

---

