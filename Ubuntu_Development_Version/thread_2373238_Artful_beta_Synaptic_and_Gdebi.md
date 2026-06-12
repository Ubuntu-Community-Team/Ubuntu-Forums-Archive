---
title: "Artful beta Synaptic and Gdebi"
date: 2017-10-04
forum: Ubuntu Development Version
---

### Post by iamjiwjr on 2017-10-04
Neither starts when icon clicked in Artful beta.

---

### Post by ajgreeny on 2017-10-04
Do they start from terminal commands **gdebi-gtk** and **synaptic-pkexec**?

---

### Post by Chanath on 2017-10-04
> **iamjiwjr said:**
> Neither starts when icon clicked in Artful beta.

In Ubuntu default they won't start - Wayland. On Ubuntu on Xorg at login, they will.

---

### Post by dino99 on 2017-10-04
with a wayland session (ubuntu default), copy/paste into a terminal: [PHP] xhost +si:localuser:root[/PHP]
then apps will work  :P

---

### Post by Frogs Hair on 2017-10-04
I've added a script to startup applications that can be named whatever you'd like . There are a bug reports on synaptic and some other applications.

```
 #!/bin/bashsleep 10 && xhost +si:localuser:root

```

---

### Post by Chanath on 2017-10-04
> **dino99 said:**
> with a wayland session (ubuntu default), copy/paste into a terminal: [PHP] xhost +si:localuser:root[/PHP]
then apps will work  :P
and @ Frogs Hair 
Thanks!

---

### Post by iamjiwjr on 2017-10-04
Thanks! That did it. 'Preciate the assistance.

---

### Post by ajgreeny on 2017-10-05
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

