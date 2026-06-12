---
title: "[SOLVED] how do i completely reinstall wine?"
date: 2009-01-04
forum: Wine
---

### Post by Meow27 on 2009-01-04
here is all of what i know,
-uninstall wine, by synaptic or whatother means
-delete the .wine folder
-*reinstall wine 
-see that my .wine folder is empty
-panic
-post on ubuntuforums.org


i think my point is made :P

last time i went through this procedure, i noticed that reinstalling wine did nothing in my .wine folder, more importantly, nothing is being touched in the windows folder and im not sure what to do.

im using ubuntu hardy x86

---

### Post by matteojg on 2009-01-05
My guess is that you deleted the contents but not the folder during the uninstall.

Try deleting it again using "rm -rf $HOME/.wine" in a console and then
"sudo apt-get remove --purge wine."

Reinstall the last stable version for your OS and hopefully things will be ok.

---

### Post by Meow27 on 2009-01-05
ok things arent working out :/

i did as you said but the problem has emerged, after the install only the windows folder with the system32 folder (inside) are there, but NOTHING else

this is a frustrating problem, not one worth reinstalling ubuntu >.>

help please! :0

---

### Post by david_kt on 2009-01-05
> **Meow27 said:**
> ok things arent working out :/

i did as you said but the problem has emerged, after the install only the windows folder with the system32 folder (inside) are there, but NOTHING else

this is a frustrating problem, not one worth reinstalling ubuntu >.>

help please! :0

What you want to do? Go ahead to run any exe file and see if it is working. Wine will create/update .wine directory when it run.

DK

---

### Post by matteojg on 2009-01-05
You of course need to re-install the software that you were previously running with wine...the clean re-install seemed to work as intended from this end.

Try installing something marked platinum for your version of wine ([http://appdb.winehq.org/](http://appdb.winehq.org/)) and seeing if it works.

---

### Post by Meow27 on 2009-01-05
ok  thanks guys, i didnt know the dlls show up when they are needed. 

i guess ill mark this thread as solved.

---

