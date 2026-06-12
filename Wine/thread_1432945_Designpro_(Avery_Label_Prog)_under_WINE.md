---
title: "Designpro (Avery Label Prog) under WINE"
date: 2010-03-18
forum: Wine
---

### Post by Gopherit on 2010-03-18
I have been quite happily running this Avery Label maker prog under Ubuntu 9.10/Wine. My new m/c is 64 bit and running 9.10/64 bit, but although the prog loads it will not run. I have also tried Crossover with the same result. I can run it on a virtual version of Win 7, but that's not the objective.

I have tried getlibs but this tells me the appropriate libraries are installed.

I have tried various Wine vers from 1.0.1 (same as the 32 bit m/c) through to 1.1.40. The later hints at working as the spinning icon comes up - but then nothing!

Ideas very welcome - it must be something simple!:confused:

---

### Post by ajgreeny on 2010-03-18
Try **glabels**, which may do all you need without worrying about running it in wine.  It's in the repos.

---

### Post by Gopherit on 2010-03-18
AJ, that's a good steer. I've just tried it and it comes close to doing most things. Can't see how to link a database, although it will merge a text file.
I am fairly wedded to Designpro because of the length of time I have used it (8 years) and thus the library of labels I have built for instant use together with databases for mailouts. My network has 2 XP machines and 2 Ubuntu - all but this new 64bit one swap the label files quite happily. My other programs run under wine so this is really frustrating!

---

### Post by Gopherit on 2010-03-18
I have now tried to run the prog from terminal. Here is the output:

[email]paul@Gopher-Ubuntu:~/.wine[/email]/drive_c/Program Files/DesignPro$ wine designp.exe
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\DesignPro\\designp.exe" failed, status c0000005

I anyone can translate that for me I would be grateful! I'm guessing that there is something wrong with odbc32.dll. Is this pointing to a 64 bit problem?

---

