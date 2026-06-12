---
title: "Wine starts up slowly"
date: 2009-03-17
forum: Wine
---

### Post by linuxguru1 on 2009-03-17
Hi,

I just found out I was still using an old version of wine (1.0.7) and upgraded (to 1.1.17), and I'm not liking the new wine. Loading the configuration screen, or just running a simple command such as

```

wine notepad.exe

```

takes at **LEAST** one minute to start up... I don't think my computer's the problem since the previous version of wine didn't have that problem.
Is it just me, or is it wine? Is there a remedy?

Thanks!

PS: I also keep failing at installing MSOffice 2k7, but I just noticed 2 topics in this section of the forums that claim to have a working tutorial... I will try them asap. This PS just to inform you in case I suddenly start talking about Office :O

EDIT:

Also winetricks seems to have a problem...

```
stefaan@stefaan-ubuntu:~$ sh winetricks vcrun6 msi2
err:process:__wine_kernel_init boot event wait timed out
^Cerr:process:__wine_kernel_init boot event wait timed out
err:seh:raise_exception Unhandled exception code c000013a flags 0 addr 0xb805f430

```

Maybe it's because I'm not running the latest kernel at the moment, but the new kernel kinda royally raped my display :/


**EDIT2:**
Okay, starting the new kernel fixed the speedproblem. I'm still having trouble getting MSOffice 2007 to work though :/ I tried 4 different tutorials... help?

---

### Post by Aq32 on 2009-11-28
Hi
How did you start the new kernel? I have the same problem and no solutions as of yet.

---

