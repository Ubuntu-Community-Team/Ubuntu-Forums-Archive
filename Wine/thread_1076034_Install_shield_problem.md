---
title: "Install shield problem"
date: 2009-02-20
forum: Wine
---

### Post by Redopz on 2009-02-20
hey, running the newest version of ubuntu and wine 1.1.12.

im trying to install battlefield 1942, but everytime i try to run the setup.exe, the installshield for windows tries to come up. anyway to get past that?

edit: it says it cant open the iKernel.exe, and when i looked for that it was named iKernel.ex_ and since im a little bit of an ubuntu noob, i have no clue how to fix  that

---

### Post by 0bso on 2009-02-20
> **Redopz said:**
> 
im trying to install battlefield 1942, but everytime i try to run the setup.exe, the installshield for windows tries to come up.

Did you expect something else to happen? :) (That's what it is supposed to do, you are installing a windows application.)

---

### Post by Redopz on 2009-02-21
> **0bso said:**
> Did you expect something else to happen? :) (That's what it is supposed to do, you are installing a windows application.)

facepalm :D

well ive installed other games like Counter strike and wow, and never had a problem with this. Other people ive talked to have gotten it up without a problem to.

---

### Post by 0bso on 2009-02-21
From the wine FAQ:
> 6.9.  I get "Error installing iKernel.exe: (0x1400)"  when running an InstallShield 6 installer.

If you get the error "Error installing iKernel.exe: (0x1400)" at any point, it's probably because there are leftover processes from a previous try. You can verify this with the command

$ ps augxw | grep wine

If that command shows old copies of wine running your setup, you need to kill them before you can run the setup program. If there are no other Wine programs running, you can kill them all with the command

$ killall wine

Or you can try installing it right after a restart. Probably unnessassary, but there shouldn't be any wine processes running then.

---

### Post by Redopz on 2009-02-22
i tried that and it said that no wine processes were killed, probably because i wasnt running any, and when that didnt work i tried to restart, and that didnt work either.

But mine isnt "Error installing iKernel.exe: (0x1400)" its "Error installing iKernel.exe: (0x8002802b)"  again, im kinda extremely new to this, so i have no clue if thats important, or if its just some wierd resolution numbers

---

### Post by Redopz on 2009-02-24
bump

---

### Post by modemlamer on 2009-06-24
bumping again...

ikernel.exe failure like above


ubuntu 9.04
wine 1.1.12

and testet on wine 1.1.24

both throwing the same error

greetz from germany

---

### Post by Vik Vasilev on 2009-07-29
I have the same problem installing a game, can anyone tell me how this can be fixed?

---

