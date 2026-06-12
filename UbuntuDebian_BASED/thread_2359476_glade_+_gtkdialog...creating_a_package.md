---
title: "glade + gtkdialog...creating a package??"
date: 2017-04-24
forum: Ubuntu/Debian BASED
---

### Post by gmcn on 2017-04-24
hi all .. am a student new to the linux scene..but i am working on a small project and could use some help from veterans on here...

i am planning to build a raspberry pi 3 with touch screen + kali linux + custom app torun bash files to run a few tasks..

for this i was playing around on my vm machine...i installed glade & gtkdialog..made the interface ..it consists of a window and then a widget that has a button "update" and i assigned the clicked event to the update bash file...but the problem is when ever i try to compile the executable.. i get the error "** (gtkdialog:10083): ERROR **: Gtkdialog: Could not find the dialog description in the environment variable" since i am new ..i have no idea what the error is..help is highly appreciated thank you..

---

### Post by gmcn on 2017-04-24
the exact error i get is 


root@MaHaKaLi:~/Pro# gtkdialog --glade-xml=HackEasy.glade --program=HackEasy


** (gtkdialog:10083): ERROR **: Gtkdialog: Could not find the dialog description in the environment variable 'HackEasy'.
Trace/breakpoint trap

---

