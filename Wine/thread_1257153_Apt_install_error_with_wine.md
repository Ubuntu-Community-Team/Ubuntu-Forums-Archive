---
title: "Apt install error with wine"
date: 2009-09-03
forum: Wine
---

### Post by jlh68 on 2009-09-03
I have been trying to install an apt called Heavy Weather.  I get the following error message "Fatal error at script line 584" and "unable to open destination file".

I had this apt installed once before so I know it can be done.  I also can install successfully another apt for another weather station device (Same manufacturer of the weather station), except my weather station will not communicate with it.

I would like to just "start over" with wine and the applications I have installed and get it all clean and working.

For some reason I have not had a lot of success with wine.  I have gotten a few apts to work but the majority that I have tried have not worked.  That makes me wonder about wine as a useful program.  Also I cannot remove from my wine>programs>removed apts.

---

### Post by hikaricore on 2009-09-03
WINE is plenty useful you just may be expecting to much from it.
For the 5000th time the Gnome program menu and WINE do not interact well.
WINE does not add or remove items properly and probably won't for some time.

Thing is some things just can not be run outside of a ***dows OS, this is a fact.
Software is often badly designed and sometimes dependant on drivers and other such crap which WINE currently doesn't support. (gameguard for example)

Always always always always check the WINE application database when trying to install a new program.
If not one else has been able to run it chances are you aren't going to be either.

Perhaps you should look for native linux programs to replace the ones your having trouble with?

---

### Post by YokoZar on 2009-09-04
> **hikaricore said:**
> 
For the 5000th time the Gnome program menu and WINE do not interact well.
WINE does not add or remove items properly and probably won't for some time.
Correction: If you install the app with a recent beta Wine, and then uninstall it with a recent beta Wine, its entry should be cleaned properly now.  This unfortunately doesn't work with stuff you installed using an earlier Wine.

---

### Post by hikaricore on 2009-09-04
> **YokoZar said:**
> Correction: If you install the app with a recent beta Wine, and then uninstall it with a recent beta Wine, its entry should be cleaned properly now.  This unfortunately doesn't work with stuff you installed using an earlier Wine.

Thanks I wasn't aware the long standing menu fiasco had been resolved.  ^_^

---

