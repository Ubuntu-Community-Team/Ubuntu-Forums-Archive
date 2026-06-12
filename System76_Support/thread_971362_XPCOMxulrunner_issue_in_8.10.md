---
title: "XPCOM/xulrunner issue in 8.10"
date: 2008-11-04
forum: System76 Support
---

### Post by gila_monster on 2008-11-04
thomasaaron (and any others),

gbutler69 mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=951615") that he had an issue after an update to 8.10 with Firefox not running. I am having a similar issue. Typing 

```
$ export LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.3/

$ firefox
```

does remedy the problem. You didn't address this issue directly in your response to him, and I didn't see anything useful on an (admittedly brief) perusal of the forums. I tried reinstalling xulrunner, and that didn't help much. Do you have any suggestions here? I've also done a System76 restore, and I am indeed running 2.2.7 of the System76 driver.

Thanks much.

gila

PS After reading some of your responses here, I think you have the patience of a saint! Thanks for all the help.

---

### Post by thomasaaron on 2008-11-05
Hey gila,

> After reading some of your responses here, I think you have the patience of a saint!

Actually, I'm somewhere between [-o<]  and  ](*,) !

Regarding the firefox issue. I *THINK* it is a broken simlink. This has been reported as a bug, and a fix may be on the way for it.

You should be able to add that line...

LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.3/

...to the bottom of .bashrc (sudo gedit .bashrc) and reboot to fix the problem until the fix comes down.

---

### Post by gila_monster on 2008-11-06
thomasaaron,

just informational: I tried completely removing and reinstalling Firefox and xulrunner in the hopes this would clear up the problem. No dice.

Setting the variable in .bashrc does work, but it's annoying to have to start from a terminal.

gila

---

