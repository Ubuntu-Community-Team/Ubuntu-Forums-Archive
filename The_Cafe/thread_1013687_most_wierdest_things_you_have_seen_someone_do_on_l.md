---
title: "most wierdest things you have seen someone do on linux"
date: 2008-12-17
forum: The Cafe
---

### Post by EnGorDiaz on 2008-12-17
im not going to mention names but the most weirdest thing i have seen someone do 

is install Norton anti virus on Linux i mean come on!

so what is the weirdest thing you have installed or someone else has installed on linux

---

### Post by MaxIBoy on 2008-12-17
Someone who learned BASH on the job was under the impression that in full text mode, he had to do something like this:
```
cd /dev
ls -a > ~/devices
emacs ~/devices
```
when in fact he could've done this:
```
cd /dev
ls -a | less
```


This same person also followed this set of steps to get back to the desktop after spending some time in a virtual terminal:
[LIST]
[*]rm /tmp/X0-lock
[*]startx
[*]LXDE starts up for some reason.
[*]ctrl-alt-backspace
[*]instead of going to the login screen, computer drops back to whatever graphical session he started with.
[/LIST]
when in fact he could've done this:
[LIST][*]ctrl-alt-F7[/list]



Sadly, this person was me.

---

### Post by ajcham on 2008-12-17
> **MaxIBoy said:**
> 
when in fact he could've done this:
[LIST][*]ctrl-alt-F7[/list]



Sadly, this person was me.

Even worse, you only need to alt-f7!

---

### Post by bp1509 on 2008-12-17
d

---

### Post by koffeinöverdos on 2008-12-17
I'm still a linux noob (about half a year now) so I can't get too technical. But I suppose its when I see people deck out their desktop theme to look exactly like Windows XP or Vista, or even worse, I saw an ubuntu installable package that pretty much completey decked out ubuntu to look like windows XP.

---

