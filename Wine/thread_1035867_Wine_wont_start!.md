---
title: "Wine wont start!"
date: 2009-01-10
forum: Wine
---

### Post by Hangwire on 2009-01-10
Hello all. Does someone know what is this? 

```
nick@nick-desktop:~$ winecfg
wine: Call from 0x7b8456d0 to unimplemented function hal.dll.HalGetBusDataByOffset, aborting
wine: Unimplemented function hal.dll.HalGetBusDataByOffset called at address 0x7b8456d0 (thread 001a), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.
```

When I do 

```
ulimit -c unlimited
```

It only gives me this thing again without the last line. 
Help please? :(

---

### Post by matteojg on 2009-01-10
Sorry, I incorrectly assumed you were trying to run a program with wine, not the winecfg.

In this case I am not sure of the fix...perhaps a clean reinstall of the last stable version of wine (make sure to follow the instructions given in the wine FAQ for the reinstall)











This means you are missing the .dll file listed in the error report.

Read the wineFAQ

[http://wiki.winehq.org/FAQ#head-bb6a7a98ea5016383c4f81717063463e5217c3bf](http://wiki.winehq.org/FAQ#head-bb6a7a98ea5016383c4f81717063463e5217c3bf)

You can also look for them with google...but head the warning in the FAQ

Once you acquire the missing .dll you need to place it in the system32 directory:

Places>Home>Ctrl+h>.wine>drive_c>windows>System32

---

### Post by hikaricore on 2009-01-10
You're using wine 1.1.12 I assume.  There is a sticky about this at the top of this fourm.

Downgrade to 1.1.11.


> **matteojg said:**
> This means you are missing the .dll file listed in the error report.

Read the wineFAQ

[http://wiki.winehq.org/FAQ#head-bb6a7a98ea5016383c4f81717063463e5217c3bf](http://wiki.winehq.org/FAQ#head-bb6a7a98ea5016383c4f81717063463e5217c3bf)

You can also look for them with google...but head the warning in the FAQ

**This is most likely incorrect.**

---

### Post by Hangwire on 2009-01-10
Thank you very much hikaricore!
Next time ill be sure to take a look at the stickys! :)

---

