---
title: "Ubuntu 6.08 TS"
date: 2007-02-03
forum: The Cafe
---

### Post by TBOL3 on 2007-02-03
Well, I was trying to upgrade from Ubunu 6.06 LTS, to 6.10, from the alternet disc.   But even after checking for no defects, it still crashed in the middle of installing.  So now I have some of Ubuntu 6.06 LTS and 6.10, aka 6.08 TS.

---

### Post by ~LoKe on 2007-02-03
```
sudo gedit /etc/apt/sources.list
```
Change all the "Dapper" entries to "Edgy".
```
sudo apt-get update && gksu "update-manager -c -d"
```

---

### Post by 23meg on 2007-02-03
> **~LoKe said:**
> ```
**sudo** gedit /etc/apt/sources.list
```You should use *gksudo* instead of *sudo* for graphical apps such as Gedit.
> Change all the "Dapper" entries to "Edgy".
```
sudo apt-get update && gksu "update-manager -c -d"
``` 
You shouldn't have to modify your sources.list anyway. And -d will make the update manager look for development releases as well.

---

### Post by ~LoKe on 2007-02-03
Oops, for a second there I thought he was going to Feisty.

But yeah, there's nothing particularly wrong with sudo for graphical interfaces.

---

### Post by 23meg on 2007-02-03
> **~LoKe said:**
> 
But yeah, there's nothing particularly wrong with sudo for graphical interfaces.
There is enough wrong to suggest against it. See:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.ubuntuforums.org/showthread.php?t=165957](http://www.ubuntuforums.org/showthread.php?t=165957)
and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), which says
> 
NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

---

### Post by TBOL3 on 2007-02-03
problem, the terminal doesn't recignize gksu

But it does recomend sudo.

Please help.

---

### Post by ~LoKe on 2007-02-03
Oh?  Try gksudo

---

### Post by 23meg on 2007-02-03
> **TBOL3 said:**
> problem, the terminal doesn't recignize gksu

But it does recomend sudo.

Please help.
What's the exact error message you get when you enter ```
gksu "update-manager -c" 
```?

---

### Post by TBOL3 on 2007-02-03
No it doesn't work, it can't find gk, but i just tried kdesu, and it works, I'm using GNOME!!!


Anywy, my computer just said upgraids are availible, but it saids a new upgrade is needed, should i do that, or try you command with kdesu?

---

### Post by 23meg on 2007-02-04
gksu may have been removed in the process. Try installing it. ```
sudo apt-get install gksu
```

---

### Post by 3rdalbum on 2007-02-04
On Ubuntu, you should use gksudo rather than gksu, just like how you should use sudo rather than su.

---

### Post by TBOL3 on 2007-02-04
Actually, the document on updating said use gksu, but I now have (I think), 6.10, I will find out soon.  :)  Thanks.

---

### Post by 23meg on 2007-02-04
> **TBOL3 said:**
> Actually, the document on updating said use gksu, but I now have (I think), 6.10, I will find out soon.  :)  Thanks.Type ```
lsb_release -a 
``` to find out once all packages are installed.

---

### Post by 23meg on 2007-02-04
> **3rdalbum said:**
> On Ubuntu, you should use gksudo rather than gksu, just like how you should use sudo rather than su.
According to [this page]("https://help.ubuntu.com/community/EdgyUpgrades"), with  the update manager, *gksu* should be used.

---

