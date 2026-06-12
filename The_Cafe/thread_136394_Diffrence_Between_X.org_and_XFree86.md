---
title: "Diffrence Between X.org and XFree86?"
date: 2006-02-25
forum: The Cafe
---

### Post by Rev. Nathan on 2006-02-25
Both are the X graphic system... X.org just came out with version 7.0, and it seems Ubuntu is already supporting the upgrade? What is XFree86? Not in Ubuntu, but it is what is in place of X.org in Debian. How did the two come about? How do they differ? Any clear winner, or are they relitively the same?

On a larger scale, which one is more likely to be the better for the widespread of Linux?

---

### Post by Sirin on 2006-02-25
[QUOTE=Rev. Nathan]Both are the X graphic system... X.org just came out with version 7.0, and it seems Ubuntu is already supporting the upgrade? What is XFree86? Not in Ubuntu, but it is what is in place of X.org in Debian. How did the two come about? How do they differ? Any clear winner, or are they relitively the same?

On a larger scale, which one is more likely to be the better for the widespread of Linux?[/QUOTE]

XFree86 supports my Intel 865 card like a dream. [IMG]http://67.18.37.14/86/93/emo/logik.gif[/IMG] X.Org, on the other hand, is like a disease to Intel 865 cards. [IMG]http://67.18.37.14/86/93/emo/cry.gif[/IMG]

---

### Post by bjweeks on 2006-02-25
xfree86 is not gpl.

---

### Post by poofyhairguy on 2006-02-25
[QUOTE=bjweeks]xfree86 is not gpl.[/QUOTE]

Niether is Xorg.

---

### Post by poofyhairguy on 2006-02-25
[QUOTE=Rev. Nathan]Both are the X graphic system... X.org just came out with version 7.0, and it seems Ubuntu is already supporting the upgrade? What is XFree86? Not in Ubuntu, but it is what is in place of X.org in Debian. How did the two come about? How do they differ? Any clear winner, or are they relitively the same?

On a larger scale, which one is more likely to be the better for the widespread of Linux?[/QUOTE]


Xfree came first a long time ago. It was the standard. Then it tried to switch licences which caused a fork. Xorg is the result of that fork.

Xorg is the clear winner for Linux desktops today. Xfree is in Debian stable for the same reason other pieces of obsolete software are in Debian stable.

More info here:

[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)

---

### Post by bjweeks on 2006-02-25
Fine, not gpl Compatible.

---

### Post by dtfinch on 2006-02-25
Distros using older builds of XFree86 (due to the license change in newer builds) have had a tendency to cause my Dell with an Intel 845GV to crash frequently. So I favor X.org distros.

---

