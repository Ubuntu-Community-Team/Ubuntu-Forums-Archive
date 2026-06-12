---
title: "Can't see WoW"
date: 2009-11-11
forum: Wine
---

### Post by smudge12b on 2009-11-11
I've installed WoW on my machine and can run the launcher.exe file ok with wine but then WoW itsself doesn't come up although a look at the processes shows WoW.exe is running.

My graphics card is a NVIDIA 6200 with 185.18.36 driver installed.

---

### Post by ExSuSEusr on 2009-11-11
> **smudge12b said:**
> I've installed WoW on my machine and can run the launcher.exe file ok with wine but then WoW itsself doesn't come up although a look at the processes shows WoW.exe is running.
 
My graphics card is a NVIDIA 6200 with 185.18.36 driver installed.
 
make sure you have the fonts installed.

---

### Post by smudge12b on 2009-11-11
The fonts are there. It did work previously when I was running 9.04

---

### Post by beastrace91 on 2009-11-11
Any error messages when you try to launch the program via terminal with Wine? Also what Wine version?

~Jeff

---

### Post by smudge12b on 2009-11-11
No error messages. Wine is version 1.1.32

---

### Post by Baked- on 2009-11-11
There is a bug with the launcher or wine changing the permissions of the wow folder

you need to chmod 775 the wow directory and run from the wow.exe not launcher.exe

it will be interesting to see what were going to have to do when the next upgrade comes out as i dont think the launcher will be able to update itself

---

### Post by smudge12b on 2009-11-12
> **Baked- said:**
> There is a bug with the launcher or wine changing the permissions of the wow folder

you need to chmod 775 the wow directory and run from the wow.exe not launcher.exe

it will be interesting to see what were going to have to do when the next upgrade comes out as i dont think the launcher will be able to update itself

That was the problem. It works fine now. Thanks

---

