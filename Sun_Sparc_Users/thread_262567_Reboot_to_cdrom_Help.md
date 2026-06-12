---
title: "Reboot to cdrom??? Help"
date: 2006-09-21
forum: Sun Sparc Users
---

### Post by panzer77 on 2006-09-21
I installed the the sparc version on a Sun Ultra 5 and need to know how to reboot to the cdrom drive. Holding down the stop+A at start up and typing  "boot cdrom" is not working.  How do your force it to boot to the cdrom drive? Maybe a clear cmos or something like that?    

HELP...

Thanks,

---

### Post by kmantronix on 2006-09-22
CAn you tell us what is the message you get when trying to boot cdrom ?

---

### Post by panzer77 on 2006-09-23
As the system starts to boot I actually get to "boot:" This is just before it starts to load linux.  I've tryed boot cdrom. I've tried several commands, but to be honest I really don't know what I'm doing.  I just need to boot the cdrom so I can install Solaris 10.  I also let ubuntu load and mounted the cdrom but don't know how to reboot to that drive.  I don't know much about the ultra 5 box.

---

### Post by netced on 2006-09-24
boot cdrom

is the right command. Try to type it SEVERAL times, as quick as possible after the previous one failed (10 times is the average for me). This woks for me, I never get the "boot cdrom" working the first time, now I know at which moment to type it because I can ear the cdrom "charging" (that's hard to explain, but if you have the same problem, you'll understand ;-) !).

---

### Post by calixtine on 2006-09-24
Stop-A should get you to the OpenBoot prompt that looks like :

```
ok
```

If you see SILO loading and get this 
```
SILO Version 1.4.10
boot:
``` 
something's not right with stop-A. 

From the boot: prompt just type halt and it will bust you back down to OpenBoot. There you can type boot cdrom. OpenBoot also responds to "help" which is generally what I type when I'm faced with it :)

---

### Post by shawnerz on 2006-09-28
Panzer,
Try hitting F1 or F2 and OpenBoot starts.  I usually hit F1, F2, F10, and delete hoping one of them will stop the process.
Once it stops, you should have a 'boot' prompt.
Once it's stopped, type 'halt'
You should get 'ok'
Then type 'boot cdrom'
The computer should reboot to the CDROM.
Good luck.
-Shawn

---

