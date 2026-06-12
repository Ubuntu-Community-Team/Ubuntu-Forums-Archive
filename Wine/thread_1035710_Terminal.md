---
title: "Terminal"
date: 2009-01-10
forum: Wine
---

### Post by wolfyking2 on 2009-01-10
Ok, I'm trying to install wine thru the terminal.  but,a it wont work because when i copy paste and press enter, it says you muist type dpkg --configure -a.  So i do, but it still doesnt work, because then it asks for superuser privelige, so before dpkg thing, i type sudo.  Then, finally when I think it's gonna work, it doesn't... please help, I dont know what i'm doing qwrong, i am in the root user, and i'm typing my p]asswords fine.

sorry bout the spelling and grammar, have to go soon

---

### Post by orlox on 2009-01-10
dpkg --configure -a must be run when you have certain problems wth the package manager, like an installation finishing abruptly or something like that. That is not wine related, so probably you should go to another section of the forums to get that fixed. In any case, if you want more help, you should always give the output of the command thats not working,

---

### Post by namdung on 2009-01-10
Post output of 
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

Use *Synaptic Package Manager* or *Add/Remove Programs for * for easier WINE installation.

---

