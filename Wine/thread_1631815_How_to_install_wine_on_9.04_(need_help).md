---
title: "How to install wine on 9.04 (need help)"
date: 2010-11-27
forum: Wine
---

### Post by RingWraith007 on 2010-11-27
I need help in installing wine on ubuntu 9.04..
Everytime I use the command sudo apt-get install wine it says it cannot find package "wine" 

need help quick:?:

---

### Post by karthick87 on 2010-11-27
Try this,

To install the latest version of wine,Goto System>>Administration>>Software Sources,Select **[FONT=Arial]T[/FONT]hird Party Software **Tab
[FONT=Arial]
Click [/FONT]**Add** and add the following

```
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
```And then goto terminal and do the following,

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by RingWraith007 on 2010-12-05
Thanks got it working :D

---

### Post by karthick87 on 2010-12-05
Mark it as[COLOR=Red] [SOLVED][/COLOR]

---

