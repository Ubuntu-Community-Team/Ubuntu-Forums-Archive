---
title: "Issues with Proteus 7.7"
date: 2011-04-20
forum: Wine
---

### Post by GridLynx on 2011-04-20
Greetings. 

I was wondering if anyone had any issue while trying to run Proteus 7.7 ISIS after installing it with wine since i get the following error:

" COULD NOT LAUNCH ISIS7 PROFESSIONAL"
Failed to change to directory '/home/gridlynx/.wine/dosdevices/c:/Program Files/Labcenter Electronics/Proteus 7 Professional/Samples' (No such file or directory)

So i looked around for said path but apparently the bridge : dosdevices is inexistant. Also i found that the ISIS executable was under a different folder called BIN. Even tho this would let me open ISIS... i still would like to know why it won't launch from the route provided by the wine installation and if there is a way to correct this, since MPLAB uses this same path to launch the Proteus VSM simulator.

---

### Post by cogadh on 2011-04-21
That dosdevices directory can't be nonexistent, it is created automatically the first time you run Wine and without it, you can't even run winecfg, let alone try to install or run an application. The .wine directory it is found in is a hidden directory, so that is likely why you couldn't find it; you'll need to show hidden directories in the file browser before you will find it (assuming you were looking via the file browser).

I think we need some more info before we can really help you. What version of Wine are you using? How did you install ISIS (as in, did you install it in a custom location or anything)? Have you tried running the app from the terminal instead of from the shortcut and if so, what did Wine's error output say?

---

### Post by GridLynx on 2011-04-21
Alright... I just solved the issue.. it was such a meaningless fix as simply renaming the folder it looked for as Samples... apparently everything in this system seems to be case sensitive, therefore wine was looking for it as Samples, when the real installed folder was named SAMPLES, hence it wouldn't open it or hold it as inexistent...

---

