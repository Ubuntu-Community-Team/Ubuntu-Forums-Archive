---
title: "Steam Installs, updates, loads, login - crash"
date: 2009-08-29
forum: Wine
---

### Post by plasmamist on 2009-08-29
I am trying to run Valve's "Steam" application, but am currently having some issues.

The installer works fine and subsequently, the updater updates correctly. But, after I login, the application starts, the advertisement screen opens, freezes, and crashes.

What can I do?

Here is my terminal output:

```
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x1b9410)->(0x32c894)
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
```

If you want the rest of the terminal output, let me know.

Thanks!

---

### Post by plasmamist on 2009-08-30
Awww, vome on 44 views and no replies?!  :)

Even if its just to commiserate - maybe point me in some direction?

---

### Post by NightMKoder on 2009-08-30
If you have other things installed on the same prefix (if you don't know what a prefix is, replace "on the same prefix" with "on wine"), this may be a problem. Delete your prefix (~/.wine) and try again. But know that this will erase all your wine applications.

---

### Post by castlefox on 2009-08-30
What version of WINE are you using ?

---

### Post by solution123 on 2011-03-23
You gotta make sure all the necessary components are needed for steam to run.  check out the following link:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

