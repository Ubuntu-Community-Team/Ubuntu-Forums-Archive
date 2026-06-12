---
title: "VBox - segfault in recovery mode, just me?"
date: 2013-09-22
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-09-22
so i needed to delete some stuff and don't know how to ctrl+alt+f1 in virtualbox
so i used recovery mode
i then selected enable networking no it would mount the system in read/write
at the end of the output there was a segfault
then i dropped to root console and did what i wanted to
if there is a bug in recovery mode that really needs to be fixed asap, that is the last thing someone needs there

---

### Post by Elfy on 2013-09-23
>  if there is a bug in recovery mode that really needs to be fixed asap, that is the last thing someone needs there I saw no seg fault in recovery mode.

>  so i needed to delete some stuff and don't know how to ctrl+alt+f1 in virtualboxYou need to use the host key instead - default is Right Ctrl, so RightCtrl+F1

---

### Post by pqwoerituytrueiwoq on 2013-09-23
did you run the enable networking option?
i am using a bridged net adapter in virtualbox if that helps

---

### Post by Elfy on 2013-09-24
>  did you run the enable networking option?Yes I did.

I also went to a root prompt and updated/graded it.

>  i am using a bridged net adapter in virtualbox if that helps Not here. 

I've not had any issues with recovery mode used normally either, if it is a bug - perhaps it's with VBbox.

---

