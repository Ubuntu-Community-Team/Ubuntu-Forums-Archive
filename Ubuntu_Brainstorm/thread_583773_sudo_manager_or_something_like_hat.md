---
title: "sudo manager or something like hat"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by snake444 on 2007-10-20
for me it is annoying to enter sudo password all the time so maybe this will be good idea for hardy
an gui window that there something like this

Request sudo passwords on this windows

[x] Synaptic
[x] Graphic and screens
[x] System monitor
[x] Update manager

and alot of more checkboxes

and you can uncheck for example the update manager and after that everytime you open update manager and do an update it wont ask for a sudo password

and if you check the system monitor for example every time you open the system monitor it will ask from you a sudo password

---

### Post by smartboyathome on 2007-10-20
This won't work, as the programs that need sudo are ones that access files in your filesystem which aren't part of your /home/username directory. If you get rid of this, you take away are HUGE security feature in Linux.

---

### Post by yelo3 on 2007-10-21
I'm sure this can be done. with the command "visudo" you have the possibility to specify when asking for password and when not. And this can be done with the executable files you want.

---

